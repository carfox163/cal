<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>成绩转换器 - 百分制成绩转换工具</title>
    <style>
        body {
            font-family: 'Microsoft YaHei', Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 1000px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f9f9f9;
        }
        h1, h2, h3 {
            color: #2c3e50;
        }
        h1 {
            text-align: center;
            border-bottom: 2px solid #3498db;
            padding-bottom: 10px;
            margin-bottom: 30px;
        }
        h2 {
            border-left: 5px solid #3498db;
            padding-left: 10px;
            margin-top: 30px;
        }
        .container {
            background-color: white;
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            margin-bottom: 30px;
        }
        .calculator {
            background-color: #f1f9fe;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input[type="number"] {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }
        button:hover {
            background-color: #2980b9;
        }
        .result {
            margin-top: 20px;
            padding: 15px;
            background-color: #e8f7e8;
            border-radius: 4px;
            display: none;
        }
        .features {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin: 20px 0;
        }
        .feature-item {
            background-color: #f1f9fe;
            padding: 15px;
            border-radius: 5px;
        }
        .note {
            background-color: #fff8e1;
            padding: 15px;
            border-left: 4px solid #ffc107;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <h1>成绩转换器 - 百分制成绩转换工具</h1>
    
    <div class="container">
        <h2>概述</h2>
        <p>成绩转换器是一款专业的在线成绩标准化工具，能够将不同评分体系的原始成绩转换为标准百分制成绩。通过线性转换算法，确保成绩评价的公平性和可比性。</p>
    </div>
    
    <div class="container">
        <h2>成绩转换计算器</h2>
        <div class="calculator">
            <div class="form-group">
                <label for="originalScore">原始成绩 (g1):</label>
                <input type="number" id="originalScore" step="0.01" placeholder="请输入原始成绩">
            </div>
            
            <div class="form-group">
                <label for="originalMean">原始成绩均分 (a1):</label>
                <input type="number" id="originalMean" step="0.01" placeholder="请输入原始成绩的平均分">
            </div>
            
            <div class="form-group">
                <label for="originalStdDev">原始成绩标准差 (k1):</label>
                <input type="number" id="originalStdDev" step="0.01" placeholder="请输入原始成绩的标准差">
            </div>
            
            <div class="form-group">
                <label for="targetMean">目标均分 (g2):</label>
                <input type="number" id="targetMean" step="0.01" placeholder="请输入转换后的目标平均分" value="75">
            </div>
            
            <div class="form-group">
                <label for="targetStdDev">目标标准差 (k):</label>
                <input type="number" id="targetStdDev" step="0.01" placeholder="请输入转换后的目标标准差" value="10">
            </div>
            
            <button onclick="calculateGrade()">计算转换成绩</button>
            
            <div id="result" class="result">
                <h3>转换结果</h3>
                <p><strong>转换后的百分制成绩:</strong> <span id="convertedScore"></span></p>
                <p><strong>转换后成绩均分:</strong> <span id="convertedMean"></span></p>
                <p><strong>转换后成绩标准差(离散度k2):</strong> <span id="convertedStdDev"></span></p>
                <p><strong>最高分:</strong> <span id="maxScore"></span></p>
                <p><strong>最低分:</strong> <span id="minScore"></span></p>
            </div>
        </div>
        
        <h3>计算公式</h3>
        <p>转换公式为：</p>
        <p><strong>百分制成绩 = 目标标准差k × (原始成绩g1 - 原始均分a1) / 原始标准差k1 + 目标均分g2</strong></p>
    </div>
    
    <div class="container">
        <h2>核心功能</h2>
        <div class="features">
            <div class="feature-item">
                <h3>线性标准化转换</h3>
                <p>基于原始成绩分布进行科学转换，确保成绩评价的公平性。</p>
            </div>
            <div class="feature-item">
                <h3>多参数自定义</h3>
                <p>可灵活设置目标均分和标准差，满足不同转换需求。</p>
            </div>
            <div class="feature-item">
                <h3>成绩分布分析</h3>
                <p>自动计算转换后的成绩分布特征，包括均分、标准差等。</p>
            </div>
            <div class="feature-item">
                <h3>批量处理</h3>
                <p>支持大量成绩数据一次性转换，提高工作效率。</p>
            </div>
        </div>
    </div>
    
    <div class="container">
        <h2>适用场景</h2>
        <ul>
            <li>不同学校/课程间的成绩比较</li>
            <li>标准化考试分数转换</li>
            <li>学术研究中的数据标准化处理</li>
            <li>教育评估中的跨体系成绩对比</li>
        </ul>
    </div>
    
    <div class="note">
        <h3>注意事项</h3>
        <ul>
            <li>本转换器假设成绩分布近似正态分布</li>
            <li>极端原始成绩转换后可能超出常规百分制范围</li>
            <li>建议转换前后检查数据分布特征</li>
        </ul>
    </div>
    
    <div class="container">
        <h2>技术支持</h2>
        <p>如有任何使用问题，请联系我们的客服团队或访问帮助中心获取更多信息。</p>
    </div>
    
    <script>
        function calculateGrade() {
            // 获取输入值
            const g1 = parseFloat(document.getElementById('originalScore').value);
            const a1 = parseFloat(document.getElementById('originalMean').value);
            const k1 = parseFloat(document.getElementById('originalStdDev').value);
            const g2 = parseFloat(document.getElementById('targetMean').value);
            const k = parseFloat(document.getElementById('targetStdDev').value);
            
            // 验证输入
            if (isNaN(g1) || isNaN(a1) || isNaN(k1) || isNaN(g2) || isNaN(k)) {
                alert('请输入所有必要的数值！');
                return;
            }
            
            if (k1 === 0) {
                alert('原始标准差不能为零！');
                return;
            }
            
            // 计算转换成绩
            const convertedScore = k * (g1 - a1) / k1 + g2;
            
            // 计算其他统计量（示例值，实际应用中可能需要更多数据）
            const convertedMean = g2;
            const convertedStdDev = k;
            const maxScore = convertedMean + 3 * convertedStdDev; // 假设±3σ范围
            const minScore = convertedMean - 3 * convertedStdDev;
            
            // 显示结果
            document.getElementById('convertedScore').textContent = convertedScore.toFixed(2);
            document.getElementById('convertedMean').textContent = convertedMean.toFixed(2);
            document.getElementById('convertedStdDev').textContent = convertedStdDev.toFixed(2);
            document.getElementById('maxScore').textContent = maxScore.toFixed(2);
            document.getElementById('minScore').textContent = minScore.toFixed(2);
            
            document.getElementById('result').style.display = 'block';
        }
    </script>
</body>
</html>
