<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сравнение автомобилей Ford</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background: linear-gradient(135deg, #00274D 0%, #0056b3 100%);
            color: white;
            padding: 2rem 0;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }
        
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
        }
        
        .logo h1 {
            font-size: 2.5rem;
            margin-left: 1rem;
            font-weight: 700;
        }
        
        .logo-icon {
            font-size: 2.8rem;
            color: #fff;
        }
        
        .currency-notice {
            background-color: #e6f2ff;
            padding: 0.5rem;
            border-radius: 5px;
            margin-top: 1rem;
            display: inline-block;
            font-size: 0.9rem;
        }
        
        .tabs-container {
            max-width: 1400px;
            margin: 2rem auto;
            background: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            overflow: hidden;
        }
        
        .tabs-header {
            display: flex;
            background-color: #003366;
        }
        
        .tab-btn {
            flex: 1;
            background-color: transparent;
            border: none;
            color: white;
            padding: 1.2rem;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .tab-btn:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }
        
        .tab-btn.active {
            background-color: #0056b3;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        
        .tab-content {
            display: none;
            padding: 2rem;
        }
        
        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .section-title {
            color: #00274D;
            margin-bottom: 1.5rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid #f0f0f0;
            font-size: 1.8rem;
        }
        
        .cars-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }
        
        .car-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .car-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }
        
        .car-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-bottom: 3px solid #0056b3;
            background-color: #f0f0f0;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #666;
            font-size: 1rem;
        }
        
        .car-info {
            padding: 1.5rem;
        }
        
        .car-name {
            font-size: 1.5rem;
            color: #00274D;
            margin-bottom: 0.5rem;
        }
        
        .car-price {
            font-size: 1.3rem;
            color: #0056b3;
            font-weight: 700;
            margin-bottom: 1rem;
        }
        
        .price-byn {
            font-size: 1.1rem;
            color: #28a745;
            font-weight: 600;
        }
        
        .car-features {
            list-style-type: none;
            margin-bottom: 1.5rem;
        }
        
        .car-features li {
            padding: 0.3rem 0;
            display: flex;
            align-items: center;
        }
        
        .car-features li:before {
            content: "✓";
            color: #28a745;
            font-weight: bold;
            margin-right: 0.5rem;
        }
        
        .btn {
            display: inline-block;
            background-color: #0056b3;
            color: white;
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            text-align: center;
            transition: all 0.3s ease;
            text-decoration: none;
            width: 100%;
        }
        
        .btn:hover {
            background-color: #003d82;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .comparison-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 2rem;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            font-size: 0.9rem;
        }
        
        .comparison-table th, .comparison-table td {
            padding: 0.8rem;
            text-align: left;
            border-bottom: 1px solid #e0e0e0;
        }
        
        .comparison-table th {
            background-color: #f8f9fa;
            color: #00274D;
            font-weight: 600;
            width: 25%;
        }
        
        .comparison-table td {
            width: 25%;
        }
        
        .comparison-table tr:hover {
            background-color: #f8f9fa;
        }
        
        .highlight {
            background-color: #e6f2ff;
            font-weight: 600;
        }
        
        .price-cell {
            font-weight: 600;
            color: #0056b3;
        }
        
        .specs-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .spec-card {
            background-color: #f8f9fa;
            border-radius: 8px;
            padding: 1.5rem;
            text-align: center;
            transition: transform 0.3s ease;
        }
        
        .spec-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .spec-value {
            font-size: 1.8rem;
            font-weight: 700;
            color: #0056b3;
            margin: 0.5rem 0;
        }
        
        .spec-name {
            color: #666;
            font-size: 0.9rem;
        }
        
        .details-section {
            margin-top: 2rem;
            padding: 1.5rem;
            background-color: #f8f9fa;
            border-radius: 8px;
        }
        
        details {
            margin: 1rem 0;
            padding: 1rem;
            background: white;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        summary {
            cursor: pointer;
            font-weight: 600;
            color: #00274D;
        }
        
        mark {
            background-color: #fff9c4;
            padding: 0.2rem 0.4rem;
            border-radius: 3px;
        }
        
        blockquote {
            border-left: 4px solid #0056b3;
            margin: 1.5rem 0;
            padding-left: 1.5rem;
            font-style: italic;
            color: #555;
        }
        
        progress {
            width: 100%;
            height: 20px;
            border-radius: 10px;
        }
        
        progress::-webkit-progress-bar {
            background-color: #f0f0f0;
            border-radius: 10px;
        }
        
        progress::-webkit-progress-value {
            background-color: #0056b3;
            border-radius: 10px;
        }
        
        .mini-table {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin: 15px 0;
        }
        
        .mini-table div {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: center;
            background: white;
            border-radius: 5px;
        }
        
        footer {
            background-color: #00274D;
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1.5rem;
        }
        
        @media (max-width: 768px) {
            .cars-grid {
                grid-template-columns: 1fr;
            }
            
            .tabs-header {
                flex-direction: column;
            }
            
            .tab-btn {
                width: 100%;
            }
            
            .comparison-table {
                font-size: 0.8rem;
            }
        }

        .image-loading {
            background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
            background-size: 200% 100%;
            animation: loading 1.5s infinite;
        }

        @keyframes loading {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">
            <div class="logo-icon">🚗</div>
            <h1>Сравнение автомобилей Ford</h1>
        </div>
        <p>Общее и индивидуальное задание по сравнению характеристик</p>
        <div class="currency-notice">Все цены указаны в белорусских рублях (BYN)</div>
    </header>
    
    <div class="tabs-container">
        <div class="tabs-header">
            <button class="tab-btn active" data-tab="general">Общее задание</button>
            <button class="tab-btn" data-tab="individual">Индивидуальное задание</button>
        </div>
        
        <!-- Общее задание -->
        <div class="tab-content active" id="general">
            <h2 class="section-title">Сравнение автомобилей Ford</h2>
            
            <div class="cars-grid">
                <div class="car-card">
                    <img src="https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?ixlib=rb-4.0.3&auto=format&fit=crop&w=1170&q=80" 
                         alt="Ford Explorer" 
                         class="car-image"
                         data-fallback="https://images.pexels.com/photos/112460/pexels-photo-112460.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                         onerror="handleImageError(this)">
                    <div class="car-info">
                        <h3 class="car-name">Ford Explorer</h3>
                        <p class="car-price">от 148 000 BYN</p>
                        <p class="price-byn">(~3 800 000 российских рублей)</p>
                        <ul class="car-features">
                            <li>Двигатель 2.3L EcoBoost</li>
                            <li>300 л.с.</li>
                            <li>Автоматическая КПП</li>
                            <li>Полный привод</li>
                        </ul>
                        <button class="btn">Подробнее</button>
                    </div>
                </div>
                
                <div class="car-card">
                    <img src="https://images.unsplash.com/photo-1552519507-da3b142c6e3d?ixlib=rb-4.0.3&auto=format&fit=crop&w=1170&q=80" 
                         alt="Ford Mustang" 
                         class="car-image"
                         data-fallback="https://images.pexels.com/photos/210019/pexels-photo-210019.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                         onerror="handleImageError(this)">
                    <div class="car-info">
                        <h3 class="car-name">Ford Mustang</h3>
                        <p class="car-price">от 125 000 BYN</p>
                        <p class="price-byn">(~3 200 000 российских рублей)</p>
                        <ul class="car-features">
                            <li>Двигатель 5.0L V8</li>
                            <li>450 л.с.</li>
                            <li>Механическая КПП</li>
                            <li>Задний привод</li>
                        </ul>
                        <button class="btn">Подробнее</button>
                    </div>
                </div>
                
                <div class="car-card">
                    <img src="https://images.unsplash.com/photo-1605559424843-9e4c228bf1c2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1064&q=80" 
                         alt="Ford Focus" 
                         class="car-image"
                         data-fallback="https://images.pexels.com/photos/112460/pexels-photo-112460.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                         data-fallback2="https://media.ed.edmunds-media.com/ford/focus/2022/oem/2022_ford_focus_sedan_st-line_fq_oem_1_1600.jpg"
                         onerror="handleImageError(this)">
                    <div class="car-info">
                        <h3 class="car-name">Ford Focus</h3>
                        <p class="car-price">от 66 000 BYN</p>
                        <p class="price-byn">(~1 700 000 российских рублей)</p>
                        <ul class="car-features">
                            <li>Двигатель 1.5L EcoBoost</li>
                            <li>150 л.с.</li>
                            <li>Автоматическая КПП</li>
                            <li>Передний привод</li>
                        </ul>
                        <button class="btn">Подробнее</button>
                    </div>
                </div>
            </div>
            
            <!-- Остальной код остается без изменений -->
            <table class="comparison-table">
                <thead>
                    <tr>
                        <th>Характеристика</th>
                        <th>Ford Explorer</th>
                        <th>Ford Mustang</th>
                        <th>Ford Focus</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Самая дорогая модель</td>
                        <td class="highlight price-cell">175 000 BYN</td>
                        <td class="price-cell">164 000 BYN</td>
                        <td class="price-cell">90 000 BYN</td>
                    </tr>
                    <tr>
                        <td>Самая дешёвая модель</td>
                        <td class="price-cell">148 000 BYN</td>
                        <td class="price-cell">125 000 BYN</td>
                        <td class="highlight price-cell">66 000 BYN</td>
                    </tr>
                    <tr>
                        <td>Двигатель</td>
                        <td>2.3L EcoBoost</td>
                        <td>5.0L V8 / 2.3L EcoBoost</td>
                        <td>1.5L EcoBoost / 1.0L EcoBoost</td>
                    </tr>
                    <tr>
                        <td>Расход топлива</td>
                        <td>10.5 л/100км</td>
                        <td>12.5 л/100км</td>
                        <td>6.2 л/100км</td>
                    </tr>
                    <tr>
                        <td>Разгон до 100 км/ч</td>
                        <td>7.2 сек</td>
                        <td class="highlight">4.8 сек</td>
                        <td>9.0 сек</td>
                    </tr>
                    <tr>
                        <td>Экологические сертификаты</td>
                        <td>Euro 6</td>
                        <td>Euro 6</td>
                        <td>Euro 6d</td>
                    </tr>
                    <tr>
                        <td>Гарантийный срок</td>
                        <td>3 года</td>
                        <td>3 года</td>
                        <td>3 года</td>
                    </tr>
                    <tr>
                        <td>Максимальная скорость</td>
                        <td>210 км/ч</td>
                        <td class="highlight">250 км/ч</td>
                        <td>215 км/ч</td>
                    </tr>
                    <tr>
                        <td>Тип КПП</td>
                        <td>Автоматическая</td>
                        <td>Автоматическая / Механическая</td>
                        <td>Автоматическая / Механическая</td>
                    </tr>
                    <tr>
                        <td>Количество передач</td>
                        <td>10</td>
                        <td>6 / 10</td>
                        <td>6 / 8</td>
                    </tr>
                </tbody>
            </table>
            
            <div class="details-section">
                <details>
                    <summary>Подробная информация о Ford Explorer</summary>
                    <p>Ford Explorer - полноразмерный кроссовер, который сочетает в себе просторный салон, современные технологии и мощные двигатели. Идеально подходит для семейных поездок и путешествий.</p>
                    <p><strong>Основные преимущества:</strong></p>
                    <ul>
                        <li>Просторный салон на 7 человек с регулируемыми сиденьями</li>
                        <li>Система полного привода Intelligent 4WD</li>
                        <li>Цифровая приборная панель 12.3 дюйма</li>
                        <li>Система помощи при парковке с камерой 360°</li>
                        <li>Продвинутая мультимедийная система SYNC 4 с 10.1-дюймовым экраном</li>
                    </ul>
                    <blockquote>
                        "Explorer предлагает отличное сочетание комфорта, мощности и технологий, делая его одним из лучших в своем классе. Просторный салон и современные системы безопасности делают его идеальным для семей."
                    </blockquote>
                </details>
                
                <details>
                    <summary>Подробная информация о Ford Mustang</summary>
                    <p>Ford Mustang - легендарный спортивный автомобиль, известный своим агрессивным дизайном и мощными двигателями. Символ американского маслкара.</p>
                    <p><strong>Основные преимущества:</strong></p>
                    <ul>
                        <li>Мощные двигатели V8 с характерным звуком выхлопа</li>
                        <li>Спортивная подвеска с несколькими режимами езды</li>
                        <li>Система запуска двигателя с дистанционным управлением</li>
                        <li>Цифровая приборная панель с настраиваемыми дисплеями</li>
                        <li>Система распознавания дорожных знаков и помощи при движении по полосе</li>
                    </ul>
                    <blockquote>
                        "Mustang продолжает оставаться иконой автомобильного мира, предлагая непревзойденное сочетание стиля и производительности. Это не просто автомобиль, это воплощение мечты для многих автолюбителей."
                    </blockquote>
                </details>
                
                <details>
                    <summary>Подробная информация о Ford Focus</summary>
                    <p>Ford Focus - компактный автомобиль, предлагающий отличную управляемость, экономичность и современные технологии по доступной цене.</p>
                    <p><strong>Основные преимущества:</strong></p>
                    <ul>
                        <li>Экономичные двигатели EcoBoost с высокой эффективностью</li>
                        <li>Просторный багажник для своего класса - 375 литров</li>
                        <li>Система помощи при парковке Active Park Assist</li>
                        <li>Мультимедийная система SYNC 3 с поддержкой Apple CarPlay и Android Auto</li>
                        <li>Система предупреждения о слепых зонах с Assist Technology</li>
                    </ul>
                    <blockquote>
                        "Focus доказывает, что компактный автомобиль может быть одновременно стильным, технологичным и увлекательным в управлении. Отличный выбор для городской эксплуатации с редкими выездами за город."
                    </blockquote>
                </details>
            </div>
        </div>
        
        <!-- Индивидуальное задание -->
        <div class="tab-content" id="individual">
            <h2 class="section-title">Индивидуальное задание: Детальное сравнение</h2>
            
            <div class="specs-grid">
                <div class="spec-card">
                    <div class="spec-value">2.3L / 5.0L</div>
                    <div class="spec-name">Объем двигателя</div>
                </div>
                <div class="spec-card">
                    <div class="spec-value">300-450 л.с.</div>
                    <div class="spec-name">Мощность</div>
                </div>
                <div class="spec-card">
                    <div class="spec-value">6-10</div>
                    <div class="spec-name">Количество передач</div>
                </div>
                <div class="spec-card">
                    <div class="spec-value">4.8-9.0 сек</div>
                    <div class="spec-name">Разгон 0-100 км/ч</div>
                </div>
            </div>
            
            <table class="comparison-table">
                <thead>
                    <tr>
                        <th>Характеристика</th>
                        <th>Ford Explorer</th>
                        <th>Ford Mustang</th>
                        <th>Ford Focus</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Тип двигателя</td>
                        <td>Бензиновый, турбированный</td>
                        <td>Бензиновый, атмосферный/турбированный</td>
                        <td>Бензиновый, турбированный</td>
                    </tr>
                    <tr>
                        <td>Расход топлива (город/трасса/смешанный)</td>
                        <td>13.1/9.4/10.8 л/100км</td>
                        <td>16.8/10.2/12.8 л/100км</td>
                        <td>8.1/5.4/6.4 л/100км</td>
                    </tr>
                    <tr>
                        <td>Тип КПП</td>
                        <td>Автоматическая, 10-ступенчатая</td>
                        <td>Механическая 6-ступ. / Автоматическая 10-ступ.</td>
                        <td>Механическая 6-ступ. / Автоматическая 8-ступ.</td>
                    </tr>
                    <tr>
                        <td>Количество передач</td>
                        <td>10</td>
                        <td>6 / 10</td>
                        <td>6 / 8</td>
                    </tr>
                    <tr>
                        <td>Габариты (Д×Ш×В), мм</td>
                        <td>5050×2004×1778</td>
                        <td>4789×1916×1387</td>
                        <td>4378×1825×1455</td>
                    </tr>
                    <tr>
                        <td>Колесная база, мм</td>
                        <td>3025</td>
                        <td>2720</td>
                        <td>2700</td>
                    </tr>
                    <tr>
                        <td>Объем багажника, л</td>
                        <td>510 (до 2485 сложив сиденья)</td>
                        <td>408</td>
                        <td>375 (до 1320 сложив сиденья)</td>
                    </tr>
                    <tr>
                        <td>Системы активной безопасности</td>
                        <td>ABS, ESP, TCS, EBD, HSA, RSC</td>
                        <td>ABS, ESP, TCS, EBD, AdvancTrac</td>
                        <td>ABS, ESP, TCS, EBD, HSA</td>
                    </tr>
                    <tr>
                        <td>Системы пассивной безопасности</td>
                        <td>7 подушек безопасности, система крепления детских сидений ISOFIX</td>
                        <td>6 подушек безопасности, система крепления детских сидений ISOFIX</td>
                        <td>6 подушек безопасности, система крепления детских сидений ISOFIX</td>
                    </tr>
                    <tr>
                        <td>Рейтинг краш-тестов Euro NCAP</td>
                        <td>5 звезд (2020)</td>
                        <td>Не тестировался</td>
                        <td>5 звезд (2018)</td>
                    </tr>
                    <tr>
                        <td>Разгон до 100 км/ч, сек</td>
                        <td>7.2</td>
                        <td class="highlight">4.8 (GT)</td>
                        <td>9.0</td>
                    </tr>
                    <tr>
                        <td>Максимальная скорость, км/ч</td>
                        <td>210</td>
                        <td class="highlight">250 (ограничена электроникой)</td>
                        <td>215</td>
                    </tr>
                    <tr>
                        <td>Начальная цена, BYN</td>
                        <td class="price-cell">148 000</td>
                        <td class="price-cell">125 000</td>
                        <td class="highlight price-cell">66 000</td>
                    </tr>
                    <tr>
                        <td>Цена топовой комплектации, BYN</td>
                        <td class="price-cell">175 000</td>
                        <td class="price-cell">164 000</td>
                        <td class="price-cell">90 000</td>
                    </tr>
                    <tr>
                        <td>Наличие Wi-Fi и Bluetooth</td>
                        <td>Да, FordPass Connect с 4G LTE</td>
                        <td>Да, FordPass Connect с 4G LTE</td>
                        <td>Да, FordPass Connect</td>
                    </tr>
                    <tr>
                        <td>Тормозная система (передние/задние)</td>
                        <td>Дисковые вентилируемые/дисковые</td>
                        <td>Дисковые вентилируемые/дисковые</td>
                        <td>Дисковые вентилируемые/дисковые</td>
                    </tr>
                    <tr>
                        <td>Системы предотвращения столкновений</td>
                        <td>Pre-Collision Assist с AEB, система предупреждения о фронтальном столкновении</td>
                        <td>Pre-Collision Assist с AEB, система предупреждения о фронтальном столкновении</td>
                        <td>Pre-Collision Assist с AEB, система предупреждения о фронтальном столкновении</td>
                    </tr>
                    <tr>
                        <td>Дополнительные системы безопасности</td>
                        <td>Система удержания в полосе, адаптивный круиз-контроль, мониторинг слепых зон</td>
                        <td>Система удержания в полосе, адаптивный круиз-контроль, мониторинг слепых зон</td>
                        <td>Система удержания в полосе, мониторинг слепых зон</td>
                    </tr>
                    <tr>
                        <td>Гарантийный срок</td>
                        <td>3 года / 100 000 км</td>
                        <td>3 года / 100 000 км</td>
                        <td>3 года / 100 000 км</td>
                    </tr>
                    <tr>
                        <td>Срок службы аккумулятора</td>
                        <td>5 лет / 100 000 км</td>
                        <td>5 лет / 100 000 км</td>
                        <td>5 лет / 100 000 км</td>
                    </tr>
                    <tr>
                        <td>Антикоррозийная гарантия</td>
                        <td>5 лет / неограниченный пробег</td>
                        <td>5 лет / неограниченный пробег</td>
                        <td>5 лет / неограниченный пробег</td>
                    </tr>
                </tbody>
            </table>
            
            <div class="details-section">
                <h3>Рейтинг безопасности</h3>
                <div class="mini-table">
                    <div>Ford Explorer</div>
                    <div>Ford Mustang</div>
                    <div>Ford Focus</div>
                    <div>
                        <progress value="92" max="100"></progress>
                        92% (Euro NCAP)
                    </div>
                    <div>
                        <progress value="85" max="100"></progress>
                        85% (NHTSA)
                    </div>
                    <div>
                        <progress value="94" max="100"></progress>
                        94% (Euro NCAP)
                    </div>
                </div>
                
                <details>
                    <summary>Системы активной и пассивной безопасности</summary>
                    <p>Все модели Ford оснащены современными системами безопасности:</p>
                    <ul>
                        <li><mark>ABS</mark> (антиблокировочная система тормозов) - предотвращает блокировку колес при торможении</li>
                        <li><mark>ESP</mark> (система курсовой устойчивости) - помогает сохранить контроль над автомобилем в сложных условиях</li>
                        <li><mark>TCS</mark> (система контроля тяги) - предотвращает пробуксовку колес</li>
                        <li><mark>EBD</mark> (электронное распределение тормозных усилий) - оптимально распределяет тормозное усилие между колесами</li>
                        <li>Подушки безопасности (от 6 до 7 в зависимости от модели) - фронтальные, боковые и шторки безопасности</li>
                        <li>Система помощи при торможении - увеличивает эффективность экстренного торможения</li>
                        <li>Система контроля давления в шинах - предупреждает о падении давления</li>
                        <li>Система предупреждения о столкновении - распознает потенциальные столкновения</li>
                        <li>Адаптивный круиз-контроль - автоматически поддерживает безопасную дистанцию</li>
                        <li>Система помощи при движении по полосе - предупреждает о непреднамеренном съезде с полосы</li>
                    </ul>
                </details>
                
                <details>
                    <summary>Дополнительные характеристики и технологии</summary>
                    <p><strong>Дата выпуска моделей и обновлений:</strong></p>
                    <ul>
                        <li>Ford Explorer: <time datetime="2020-01">Январь 2020</time> (текущее поколение)</li>
                        <li>Ford Mustang: <time datetime="2017-09">Сентябрь 2017</time> (рестайлинг в 2022)</li>
                        <li>Ford Focus: <time datetime="2018-03">Март 2018</time> (текущее поколение)</li>
                    </ul>
                    
                    <p><strong>Экологические характеристики:</strong></p>
                    <ul>
                        <li>Все модели соответствуют стандарту Euro 6</li>
                        <li>Система старт-стоп для снижения расхода топлива в городском цикле</li>
                        <li>Система рекуперативного торможения для подзарядки аккумулятора</li>
                    </ul>
                    
                    <p><strong>Комфорт и дополнительные опции:</strong></p>
                    <ul>
                        <li>Климат-контроль с фильтрацией воздуха</li>
                        <li>Подогрев передних сидений и рулевого колеса</li>
                        <li>Электропривод регулировки сидений с памятью положений</li>
                        <li>Бесключевой доступ и запуск двигателя кнопкой</li>
                        <li>Светодиодная оптика с автоматическим включением</li>
                    </ul>
                    
                    <p><strong>Отзывы владельцев:</strong></p>
                    <blockquote>
                        "Ford Explorer - отличный семейный автомобиль с просторным салоном и всеми необходимыми технологиями. Расход топлива немного высокий, но для такого размера это ожидаемо. Системы безопасности на высшем уровне - чувствуешь себя защищенным в любой ситуации."
                    </blockquote>
                    <blockquote>
                        "Mustang - это не просто автомобиль, это эмоции. Мощный двигатель, агрессивный дизайн и отличная управляемость. Мечта сбылась! Несмотря на спортивный характер, в салоне достаточно комфортно для ежедневных поездок."
                    </blockquote>
                    <blockquote>
                        "Focus оказался очень экономичным и маневренным городским автомобилем. Технологии Sync 3 радуют своей простотой и функциональностью. Отличный выбор для тех, кто ищет надежный и технологичный автомобиль по доступной цене."
                    </blockquote>
                </details>
            </div>
        </div>
    </div>
    
    <footer>
        <div class="footer-content">
            <p>Сравнение автомобилей Ford &copy; 2025</p>
            <p style="margin-top: 1rem; font-size: 0.9rem;">Цены указаны в белорусских рублях (BYN) и могут изменяться</p>
            <p style="margin-top: 0.5rem; font-size: 0.8rem;">Информация носит ознакомительный характер</p>
        </div>
    </footer>

    <script>
        // Переключение между вкладками
        document.querySelectorAll('.tab-btn').forEach(button => {
            button.addEventListener('click', () => {
                // Убираем активный класс у всех кнопок и контента
                document.querySelectorAll('.tab-btn').forEach(btn => {
                    btn.classList.remove('active');
                });
                document.querySelectorAll('.tab-content').forEach(content => {
                    content.classList.remove('active');
                });
                
                // Добавляем активный класс к нажатой кнопке и соответствующему контенту
                button.classList.add('active');
                const tabId = button.getAttribute('data-tab');
                document.getElementById(tabId).classList.add('active');
            });
        });
        
        // Функция для обработки ошибок загрузки изображений
        function handleImageError(img) {
            console.log('Ошибка загрузки изображения:', img.src);
            
            // Добавляем анимацию загрузки
            img.classList.add('image-loading');
            
            // Пробуем запасные варианты
            const fallback1 = img.getAttribute('data-fallback');
            const fallback2 = img.getAttribute('data-fallback2');
            
            if (fallback1 && img.src !== fallback1) {
                console.log('Пробуем запасной вариант 1:', fallback1);
                img.src = fallback1;
            } else if (fallback2 && img.src !== fallback2) {
                console.log('Пробуем запасной вариант 2:', fallback2);
                img.src = fallback2;
            } else {
                // Если все варианты не работают, показываем заглушку
                console.log('Все варианты не работают, показываем заглушку');
                img.outerHTML = '<div class="car-image">🚗 Ford ' + img.alt.replace('Ford ', '') + '</div>';
            }
        }
        
        // Обработка кнопок "Подробнее"
        document.querySelectorAll('.btn').forEach(button => {
            button.addEventListener('click', function() {
                const carName = this.closest('.car-card').querySelector('.car-name').textContent;
                alert(`Подробная информация о ${carName} представлена в таблице сравнения ниже!`);
            });
        });

        // Предзагрузка изображений с обработкой ошибок
        document.addEventListener('DOMContentLoaded', function() {
            const images = document.querySelectorAll('.car-image');
            images.forEach(img => {
                // Добавляем обработчик успешной загрузки
                img.addEventListener('load', function() {
                    this.classList.remove('image-loading');
                });
                
                // Добавляем обработчик ошибки
                img.addEventListener('error', function() {
                    handleImageError(this);
                });
                
                // Инициируем загрузку
                if (img.complete) {
                    if (img.naturalHeight === 0) {
                        handleImageError(img);
                    }
                }
            });
        });
    </script>
</body>
</html>
