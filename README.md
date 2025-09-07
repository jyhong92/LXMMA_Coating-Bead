<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grade Recommendations by Application - Interactive Design</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: #f0f2f5;
            padding: 20px;
        }
        
        .main-container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 5px 30px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #a91b1b 0%, #d63636 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 32px;
            margin-bottom: 10px;
        }
        
        .header p {
            opacity: 0.9;
            font-size: 14px;
        }
        
        .content-wrapper {
            display: flex;
            min-height: 600px;
        }
        
        .sidebar {
            width: 350px;
            background: #f8f9fa;
            padding: 20px;
            border-right: 1px solid #e0e0e0;
            overflow-y: auto;
            max-height: 600px;
        }
        
        .app-button {
            width: 100%;
            padding: 15px;
            margin-bottom: 10px;
            background: white;
            border: 2px solid transparent;
            border-radius: 10px;
            text-align: left;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 14px;
            font-weight: 500;
            color: #333;
        }
        
        .app-button:hover {
            background: #fff;
            border-color: #a91b1b;
            transform: translateX(5px);
            box-shadow: 0 3px 10px rgba(169, 27, 27, 0.1);
        }
        
        .app-button.active {
            background: #a91b1b;
            color: white;
            border-color: #a91b1b;
        }
        
        .detail-panel {
            flex: 1;
            padding: 40px;
            display: none;
        }
        
        .detail-panel.active {
            display: block;
            animation: fadeIn 0.3s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .app-title {
            color: #a91b1b;
            font-size: 28px;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 3px solid #a91b1b;
        }
        
        .grade-container {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 30px;
        }
        
        .grade-header {
            font-size: 12px;
            color: #666;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 15px;
            font-weight: bold;
        }
        
        .grade-pills {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .grade-pill {
            background: white;
            border: 2px solid #a91b1b;
            color: #a91b1b;
            padding: 8px 20px;
            border-radius: 25px;
            font-size: 14px;
            font-weight: bold;
            position: relative;
            transition: all 0.3s ease;
        }
        
        .grade-pill:hover {
            background: #a91b1b;
            color: white;
            transform: scale(1.05);
        }
        
        .characteristics-container {
            margin-top: 30px;
        }
        
        .char-header {
            font-size: 18px;
            color: #333;
            margin-bottom: 20px;
            font-weight: bold;
        }
        
        .char-card {
            background: linear-gradient(135deg, #fff 0%, #f8f9fa 100%);
            border-left: 4px solid #a91b1b;
            padding: 15px 20px;
            margin-bottom: 15px;
            border-radius: 8px;
            transition: all 0.3s ease;
        }
        
        .char-card:hover {
            transform: translateX(10px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .char-grade {
            color: #a91b1b;
            font-weight: bold;
            font-size: 15px;
            margin-bottom: 5px;
        }
        
        .char-desc {
            color: #666;
            font-size: 14px;
            line-height: 1.5;
        }
        
        .icon {
            display: inline-block;
            width: 20px;
            height: 20px;
            margin-right: 10px;
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <div class="main-container">
        <div class="header">
            <h1>LX MMA Grade Recommendations</h1>
            <p>Select an application to view recommended grades and specifications</p>
        </div>
        
        <div class="content-wrapper">
            <div class="sidebar">
                <button class="app-button active" onclick="showDetail(0, this)">
                    <span class="icon">🎨</span>Road Marking & Concrete Coating
                </button>
                <button class="app-button" onclick="showDetail(1, this)">
                    <span class="icon">🚢</span>Heavy Duty Coating
                </button>
                <button class="app-button" onclick="showDetail(2, this)">
                    <span class="icon">🏢</span>MMA Flooring
                </button>
                <button class="app-button" onclick="showDetail(3, this)">
                    <span class="icon">🖨️</span>Gravure Ink
                </button>
                <button class="app-button" onclick="showDetail(4, this)">
                    <span class="icon">🎯</span>PCM/Coil Paint (PVDF)
                </button>
                <button class="app-button" onclick="showDetail(5, this)">
                    <span class="icon">🔗</span>Hot Melt Adhesive (PUR)
                </button>
                <button class="app-button" onclick="showDetail(6, this)">
                    <span class="icon">📦</span>Heat Seal Lacquer
                </button>
                <button class="app-button" onclick="showDetail(7, this)">
                    <span class="icon">🚗</span>Auto-refinish
                </button>
                <button class="app-button" onclick="showDetail(8, this)">
                    <span class="icon">🔥</span>Intumescent Coating
                </button>
                <button class="app-button" onclick="showDetail(9, this)">
                    <span class="icon">⚙️</span>Additives (PVC/SMC/BMC)
                </button>
                <button class="app-button" onclick="showDetail(10, this)">
                    <span class="icon">💧</span>Specific Solubility Ink/Paint
                </button>
            </div>
            
            <div class="detail-panel active" id="detail-0">
                <h2 class="app-title">Road Marking & Concrete Coating</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA122</span>
                        <span class="grade-pill">BA123</span>
                        <span class="grade-pill">BA124</span>
                        <span class="grade-pill">BA140</span>
                        <span class="grade-pill">BA141</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA122</div>
                        <div class="char-desc">General, but only for not sensitive application to color or clearness</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA123/124</div>
                        <div class="char-desc">Fast drying, good color expression</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA140/141</div>
                        <div class="char-desc">Better chemical resistance, high viscosity, high gloss</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-1">
                <h2 class="app-title">Heavy Duty Coating (Shipment/Container)</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA123</span>
                        <span class="grade-pill">BA124</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA123</div>
                        <div class="char-desc">Good weatherability and color expression</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA124</div>
                        <div class="char-desc">Better adhesion</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-2">
                <h2 class="app-title">MMA Flooring</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA123</span>
                        <span class="grade-pill">BA124</span>
                        <span class="grade-pill">BN070</span>
                        <span class="grade-pill">BN080</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA123/124</div>
                        <div class="char-desc">Easy viscosity control</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BN070/BN080</div>
                        <div class="char-desc">Very soft & flexible, for hygiene floor</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-3">
                <h2 class="app-title">Gravure Ink</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA531</span>
                        <span class="grade-pill">BA720</span>
                        <span class="grade-pill">BA123</span>
                        <span class="grade-pill">BA124</span>
                        <span class="grade-pill">BA126</span>
                        <span class="grade-pill">BN070</span>
                        <span class="grade-pill">BN080</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA531/720</div>
                        <div class="char-desc">Hard coating, scratch resistance</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA123/BA124/BA126</div>
                        <div class="char-desc">Good adhesion and color expression</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BN070/080</div>
                        <div class="char-desc">For adhesive layer</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-4">
                <h2 class="app-title">PCM/Coil Paint (PVDF)</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA160</span>
                        <span class="grade-pill">BA127</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA160</div>
                        <div class="char-desc">PVDF compatible</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA127</div>
                        <div class="char-desc">Low viscosity ver.</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-5">
                <h2 class="app-title">Hot Melt Adhesive (PUR)</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA123</span>
                        <span class="grade-pill">BA410</span>
                        <span class="grade-pill">BA411</span>
                        <span class="grade-pill">BA330</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA410/411</div>
                        <div class="char-desc">Non-reactive, adhesion improve</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA330</div>
                        <div class="char-desc">Hydroxy modified, reactive type</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-6">
                <h2 class="app-title">Heat Seal Lacquer</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BN070</span>
                        <span class="grade-pill">BN080</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BN070/080</div>
                        <div class="char-desc">For pharma packaging and food packaging</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-7">
                <h2 class="app-title">Auto-refinish</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA123</span>
                        <span class="grade-pill">BA124</span>
                        <span class="grade-pill">BA410</span>
                        <span class="grade-pill">BA411</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA123/124</div>
                        <div class="char-desc">Color & adhesion</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA410/411</div>
                        <div class="char-desc">Harder, gasoline resistant</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-8">
                <h2 class="app-title">Intumescent Coating</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA123</span>
                        <span class="grade-pill">BN070</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA123</div>
                        <div class="char-desc">Binder function</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BN070</div>
                        <div class="char-desc">Better foam stability but higher viscosity</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-9">
                <h2 class="app-title">Additives (PVC/SMC/BMC)</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA525</span>
                        <span class="grade-pill">BA611</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA525</div>
                        <div class="char-desc">SMC/BMC</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BA611</div>
                        <div class="char-desc">PVC modifier</div>
                    </div>
                </div>
            </div>
            
            <div class="detail-panel" id="detail-10">
                <h2 class="app-title">Specific Solubility Ink/Paint</h2>
                <div class="grade-container">
                    <div class="grade-header">Recommended Grades</div>
                    <div class="grade-pills">
                        <span class="grade-pill">BA500</span>
                        <span class="grade-pill">BN120</span>
                    </div>
                </div>
                <div class="characteristics-container">
                    <div class="char-header">Key Characteristics</div>
                    <div class="char-card">
                        <div class="char-grade">BA500</div>
                        <div class="char-desc">Alcohol soluble, high A.V. (65)</div>
                    </div>
                    <div class="char-card">
                        <div class="char-grade">BN120</div>
                        <div class="char-desc">Aliphatic soluble (ex: MTO)</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        function showDetail(index, button) {
            // Remove active class from all buttons
            const buttons = document.querySelectorAll('.app-button');
            buttons.forEach(btn => btn.classList.remove('active'));
            
            // Add active class to clicked button
            button.classList.add('active');
            
            // Hide all detail panels
            const panels = document.querySelectorAll('.detail-panel');
            panels.forEach(panel => panel.classList.remove('active'));
            
            // Show selected detail panel
            const selectedPanel = document.getElementById('detail-' + index);
            selectedPanel.classList.add('active');
        }
    </script>
</body>
</html>
<!DOC[grade-design-2 (1).html](https://github.com/user-attachments/files/22197296/grade-design-2.1.html)
TYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LX MMA Grade Specifications</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: #f0f2f5;
            padding: 20px;
        }
        
        .main-container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 5px 30px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #a91b1b 0%, #d63636 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 32px;
            margin-bottom: 10px;
        }
        
        .header p {
            opacity: 0.9;
            font-size: 14px;
        }
        
        .table-container {
            padding: 30px;
            overflow-x: auto;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
        }
        
        thead {
            background: #333;
            color: white;
            position: sticky;
            top: 0;
            z-index: 10;
        }
        
        thead th {
            padding: 15px 10px;
            text-align: left;
            font-weight: 500;
            border-bottom: 3px solid #a91b1b;
        }
        
        thead th:first-child {
            width: 120px;
        }
        
        tbody tr {
            transition: all 0.3s ease;
            border-bottom: 1px solid #e0e0e0;
        }
        
        tbody tr:hover {
            background: #fff5f5;
            transform: translateX(3px);
            box-shadow: 0 2px 5px rgba(169, 27, 27, 0.1);
        }
        
        td {
            padding: 12px 10px;
        }
        
        .grade-code {
            color: #a91b1b;
            font-weight: bold;
            font-size: 15px;
        }
        
        .polymer-type {
            background: #f8f9fa;
            padding: 4px 8px;
            border-radius: 5px;
            display: inline-block;
            font-size: 12px;
            color: #555;
        }
        
        .property-value {
            text-align: center;
            font-weight: 500;
            color: #333;
        }
        
        .av-value {
            text-align: center;
            color: #666;
        }
        
        .characteristics {
            font-size: 13px;
            line-height: 1.5;
            color: #555;
        }
        
        /* BA와 BN 시리즈 구분 */
        .series-separator {
            background: linear-gradient(135deg, #a91b1b 0%, #d63636 100%);
            color: white;
            font-weight: bold;
            font-size: 16px;
            text-align: center;
        }
        
        .series-separator td {
            padding: 10px;
        }
        
        @media (max-width: 768px) {
            .table-container {
                padding: 15px;
            }
            
            table {
                font-size: 12px;
            }
            
            .header h1 {
                font-size: 24px;
            }
            
            thead th {
                padding: 10px 5px;
                font-size: 12px;
            }
            
            td {
                padding: 8px 5px;
            }
        }
    </style>
</head>
<body>
    <div class="main-container">
        <div class="header">
            <h1>LX MMA Grade Specifications</h1>
            <p>Complete Technical Data Sheet for Acrylic Bead Resins</p>
        </div>
        
        <div class="table-container">
            <table>
                <thead>
                    <tr>
                        <th>Grade</th>
                        <th>Polymer Type</th>
                        <th style="text-align: center;">Tg (°C)</th>
                        <th style="text-align: center;">MW (g/mol)</th>
                        <th style="text-align: center;">A.V. / (H.V.)</th>
                        <th>Main Characteristics</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="series-separator">
                        <td colspan="6">BA Series</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA122</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">60</td>
                        <td class="property-value">60,000</td>
                        <td class="av-value">4</td>
                        <td class="characteristics">General purpose grade, Good adhesion and pigment dispersion, Fast solvent release</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA123</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">60</td>
                        <td class="property-value">60,000</td>
                        <td class="av-value">3.5</td>
                        <td class="characteristics">General purpose grade, Higher viscosity version of BA122</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA124</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">60</td>
                        <td class="property-value">60,000</td>
                        <td class="av-value">8</td>
                        <td class="characteristics">General purpose grade, Higher adhesion and pigment dispersion than BA122</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA126</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">60</td>
                        <td class="property-value">50,000</td>
                        <td class="av-value">9.5</td>
                        <td class="characteristics">Faster organic solvent releasing version of BA124</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA140</td>
                        <td><span class="polymer-type">MMA/EA</span></td>
                        <td class="property-value">55</td>
                        <td class="property-value">100,000</td>
                        <td class="av-value">3.5</td>
                        <td class="characteristics">Clear concrete coating, Excellent weatherability, High gloss</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA141</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">55</td>
                        <td class="property-value">100,000</td>
                        <td class="av-value">3</td>
                        <td class="characteristics">Softer and low smell version of BA140</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA160</td>
                        <td><span class="polymer-type">MMA/EA</span></td>
                        <td class="property-value">60</td>
                        <td class="property-value">110,000</td>
                        <td class="av-value">6</td>
                        <td class="characteristics">Suitable for PCM paints with PVDF</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA190</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">60</td>
                        <td class="property-value">350,000</td>
                        <td class="av-value">7</td>
                        <td class="characteristics">Better mechanical strength and chemical resistance than BA124</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA320</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">75</td>
                        <td class="property-value">65,000</td>
                        <td class="av-value">7</td>
                        <td class="characteristics">Better blocking resistance than BA123</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA330</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">75</td>
                        <td class="property-value">70,000</td>
                        <td class="av-value">0 / (4)</td>
                        <td class="characteristics">Hydroxy modified acrylic resin for adhesive</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA400</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">85</td>
                        <td class="property-value">15,000</td>
                        <td class="av-value">3</td>
                        <td class="characteristics">Excellent flowability with good hardness</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA410</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">80</td>
                        <td class="property-value">40,000</td>
                        <td class="av-value">3.5</td>
                        <td class="characteristics">Harder but low Mw version of BA123, Clear finishes for furniture</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA411</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">85</td>
                        <td class="property-value">35,000</td>
                        <td class="av-value">5</td>
                        <td class="characteristics">Harder and better glossy than BA410, Clear finishes for furniture</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA500</td>
                        <td><span class="polymer-type">MMA/i-BMA</span></td>
                        <td class="property-value">100</td>
                        <td class="property-value">20,000</td>
                        <td class="av-value">65</td>
                        <td class="characteristics">Alcohol soluble type for general ink</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA525</td>
                        <td><span class="polymer-type">MMA/EA</span></td>
                        <td class="property-value">90</td>
                        <td class="property-value">70,000</td>
                        <td class="av-value">16</td>
                        <td class="characteristics">Low profile additive for SMC/BMC, Excellent metal adhesion, Durability</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA531</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">105</td>
                        <td class="property-value">100,000</td>
                        <td class="av-value">2</td>
                        <td class="characteristics">Hard coating resin with excellent durability, weatherability, and abrasion resistance</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA611</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">105</td>
                        <td class="property-value">40,000</td>
                        <td class="av-value">2</td>
                        <td class="characteristics">General purpose hard resin with improved solubility, Calendaring varnish, PVC modifier</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA720</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">115</td>
                        <td class="property-value">50,000</td>
                        <td class="av-value">2</td>
                        <td class="characteristics">Hard coating resin with low Mw, Excellent chemical resistance & weatherability</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BA840</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">120</td>
                        <td class="property-value">120,000</td>
                        <td class="av-value">2</td>
                        <td class="characteristics">Highest hardness version of BA720 for Top coating</td>
                    </tr>
                    <tr class="series-separator">
                        <td colspan="6">BN Series</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BN070</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">50</td>
                        <td class="property-value">140,000</td>
                        <td class="av-value">&lt;1</td>
                        <td class="characteristics">Very Soft and Flexible grade, Suitable for flooring and hot seal layer</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BN080</td>
                        <td><span class="polymer-type">MMA/n-BMA</span></td>
                        <td class="property-value">50</td>
                        <td class="property-value">180,000</td>
                        <td class="av-value">&lt;1</td>
                        <td class="characteristics">Very Soft and Flexible grade, Suitable for flooring and hot seal layer</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BN600</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">100</td>
                        <td class="property-value">20,000</td>
                        <td class="av-value">&lt;1</td>
                        <td class="characteristics">Excellent flowability with good hardness</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BN640</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">100</td>
                        <td class="property-value">100,000</td>
                        <td class="av-value">&lt;1</td>
                        <td class="characteristics">General PMMA beads, Excellent weatherability</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BN641</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">100</td>
                        <td class="property-value">90,000</td>
                        <td class="av-value">&lt;1</td>
                        <td class="characteristics">General PMMA beads, Excellent weatherability</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BN650</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">110</td>
                        <td class="property-value">130,000</td>
                        <td class="av-value">&lt;1</td>
                        <td class="characteristics">General PMMA beads, Excellent weatherability</td>
                    </tr>
                    <tr>
                        <td class="grade-code">BN740/741</td>
                        <td><span class="polymer-type">MMA</span></td>
                        <td class="property-value">115</td>
                        <td class="property-value">110,000</td>
                        <td class="av-value">&lt;1</td>
                        <td class="characteristics">General PMMA beads, Excellent weatherability</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</body>
</html>
