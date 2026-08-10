<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Офіційний Портал Судової Системи — Ukraine RP</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        :root {
            --bg-primary: #030712;
            --bg-secondary: #090f1d;
            --bg-card: #0d1527;
            --bg-card-hover: #131c33;
            --border-primary: #1e293b;
            --border-accent: #38bdf8;
            --accent-blue: #0ea5e9;
            --accent-blue-hover: #38bdf8;
            --accent-glow: rgba(14, 165, 233, 0.35);
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --success-color: #22c55e;
            --warning-color: #f59e0b;
            --transition-speed: 0.35s;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: linear-gradient(135deg, #020617 0%, #090d1f 50%, #030712 100%);
            background-attachment: fixed;
            color: var(--text-main);
            line-height: 1.7;
            padding: 25px;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }

        /* Динамічні світлові ефекти на фоні */
        body::before {
            content: '';
            position: fixed;
            top: -150px;
            left: -150px;
            width: 450px;
            height: 450px;
            background: rgba(14, 165, 233, 0.12);
            filter: blur(120px);
            border-radius: 50%;
            z-index: -1;
            animation: pulseGlow 8s ease-in-out infinite alternate;
        }

        body::after {
            content: '';
            position: fixed;
            bottom: -150px;
            right: -150px;
            width: 450px;
            height: 450px;
            background: rgba(129, 140, 248, 0.1);
            filter: blur(120px);
            border-radius: 50%;
            z-index: -1;
            animation: pulseGlow 10s ease-in-out infinite alternate-reverse;
        }

        @keyframes pulseGlow {
            0% { transform: scale(1); opacity: 0.8; }
            100% { transform: scale(1.25); opacity: 1; }
        }

        .main-container {
            max-width: 1250px;
            margin: 0 auto;
        }

        /* Анімації появи елементів (скрол) */
        .animate-on-scroll {
            opacity: 0;
            transform: translateY(35px);
            transition: opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1), transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .animate-on-scroll.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .portal-header {
            background: linear-gradient(135deg, rgba(9, 15, 29, 0.9) 0%, rgba(17, 27, 51, 0.9) 100%);
            backdrop-filter: blur(10px);
            border: 1px solid var(--border-primary);
            border-bottom: 4px solid var(--accent-blue);
            padding: 35px 20px;
            text-align: center;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.7), inset 0 1px 0 rgba(255, 255, 255, 0.05);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .portal-header:hover {
            transform: translateY(-3px);
            box-shadow: 0 25px 50px rgba(14, 165, 233, 0.2);
        }

        .portal-header h1 {
            color: var(--accent-blue);
            font-size: 2.4rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 10px;
            text-shadow: 0 0 25px var(--accent-glow);
        }

        .portal-header p {
            color: var(--text-muted);
            font-size: 1.05rem;
            max-width: 800px;
            margin: 0 auto;
        }

        .hero-info-box {
            background: linear-gradient(135deg, rgba(11, 19, 41, 0.9) 0%, rgba(23, 28, 74, 0.9) 100%);
            backdrop-filter: blur(10px);
            border: 2px solid var(--accent-blue);
            border-radius: 22px;
            padding: 40px 30px;
            margin-bottom: 30px;
            text-align: center;
            box-shadow: 0 0 45px rgba(14, 165, 233, 0.25), inset 0 0 20px rgba(56, 189, 248, 0.1);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .hero-info-box:hover {
            transform: translateY(-3px);
            box-shadow: 0 0 60px rgba(14, 165, 233, 0.35), inset 0 0 25px rgba(56, 189, 248, 0.15);
        }

        .hero-info-box h2 {
            font-size: clamp(2.2rem, 5vw, 3.5rem);
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 3px;
            background: linear-gradient(135deg, #38bdf8 0%, #818cf8 50%, #c084fc 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 15px;
            text-shadow: 0 0 35px rgba(56, 189, 248, 0.5);
        }

        .hero-info-box p {
            color: #cbd5e1;
            font-size: 1.15rem;
            max-width: 950px;
            margin: 0 auto 15px auto;
            line-height: 1.8;
        }

        .content-section {
            background: linear-gradient(135deg, rgba(13, 21, 39, 0.9) 0%, rgba(8, 13, 26, 0.9) 100%);
            backdrop-filter: blur(10px);
            border: 1px solid var(--border-primary);
            border-radius: 20px;
            padding: 35px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6);
            position: relative;
            overflow: hidden;
            transition: border-color 0.4s ease;
        }

        .content-section:hover {
            border-color: rgba(56, 189, 248, 0.3);
        }

        .content-section::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(56, 189, 248, 0.4), transparent);
        }

        .section-title {
            color: var(--accent-blue);
            font-size: 1.6rem;
            margin-bottom: 18px;
            border-bottom: 2px solid var(--border-primary);
            padding-bottom: 10px;
            display: inline-block;
            text-shadow: 0 0 10px rgba(14, 165, 233, 0.2);
        }

        .section-description {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 20px;
        }

        .dropdown-element {
            margin-top: 14px;
        }

        .dropdown-toggle-btn {
            background: linear-gradient(135deg, #131d35 0%, #0a1020 100%);
            color: var(--text-main);
            cursor: pointer;
            padding: 16px 22px;
            width: 100%;
            border: 1px solid var(--border-primary);
            text-align: left;
            font-size: 1.05rem;
            font-weight: 600;
            border-radius: 14px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all var(--transition-speed);
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        .dropdown-toggle-btn:hover {
            background: linear-gradient(135deg, #1c2b4e 0%, #111a30 100%);
            border-color: var(--accent-blue);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px var(--accent-glow);
        }

        .dropdown-panel {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s cubic-bezier(0.4, 0, 0.2, 1), padding 0.3s ease;
            background-color: var(--bg-secondary);
            border-radius: 0 0 14px 14px;
            padding: 0 22px;
            border: 1px solid transparent;
        }

        .dropdown-panel.expanded {
            max-height: 1200px;
            padding: 22px;
            margin-top: 4px;
            border-color: var(--border-primary);
            box-shadow: inset 0 4px 10px rgba(0,0,0,0.4);
        }

        .dropdown-panel p, .dropdown-panel ul {
            color: #d1d5db;
            font-size: 0.95rem;
            margin-bottom: 10px;
        }

        .dropdown-panel ul {
            padding-left: 22px;
        }

        .dropdown-panel li {
            margin-bottom: 6px;
        }

        .notice-box {
            background: rgba(14, 165, 233, 0.1);
            border-left: 4px solid var(--accent-blue);
            padding: 14px;
            margin-top: 15px;
            border-radius: 0 10px 10px 0;
            font-size: 0.9rem;
            color: #ffffff;
            box-shadow: inset 0 0 10px rgba(14,165,233,0.05);
        }

        .staff-grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .staff-profile-card {
            background: linear-gradient(135deg, #131d36 0%, #0a1122 100%);
            border: 1px solid var(--border-primary);
            padding: 30px 20px;
            border-radius: 18px;
            text-align: center;
            transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1), border-color 0.4s ease, box-shadow 0.4s ease;
            box-shadow: 0 8px 25px rgba(0,0,0,0.5);
            position: relative;
            overflow: hidden;
        }

        .staff-profile-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 4px;
            background: var(--accent-blue);
            box-shadow: 0 0 15px var(--accent-blue);
            transition: height 0.3s ease;
        }

        .staff-profile-card:hover {
            transform: translateY(-8px) scale(1.02);
            border-color: var(--accent-blue);
            box-shadow: 0 16px 40px var(--accent-glow);
        }

        .staff-profile-card:hover::before {
            height: 6px;
        }

        .staff-avatar-wrapper {
            width: 95px;
            height: 95px;
            margin: 0 auto 18px auto;
            position: relative;
            border-radius: 50%;
            padding: 3px;
            background: linear-gradient(135deg, var(--accent-blue), #818cf8);
            box-shadow: 0 0 25px var(--accent-glow);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .staff-profile-card:hover .staff-avatar-wrapper {
            transform: scale(1.08) rotate(3deg);
            box-shadow: 0 0 35px rgba(56, 189, 248, 0.6);
        }

        .staff-avatar-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 50%;
            border: 3px solid var(--bg-card);
            background-color: #0b1329;
            display: block;
        }

        .avatar-fallback {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: linear-gradient(135deg, #1e293b, #0f172a);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.2rem;
            border: 3px solid var(--bg-card);
            color: var(--accent-blue);
            text-shadow: 0 0 10px var(--accent-glow);
        }

        .staff-profile-card h3 {
            font-size: 1.25rem;
            margin-bottom: 6px;
            color: var(--text-main);
        }

        .staff-role-badge {
            color: var(--accent-blue);
            font-size: 0.75rem;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            margin-bottom: 14px;
            display: inline-block;
            background: rgba(14, 165, 233, 0.12);
            padding: 5px 14px;
            border-radius: 20px;
            border: 1px solid rgba(14, 165, 233, 0.2);
            transition: background 0.3s ease, transform 0.3s ease;
        }

        .staff-profile-card:hover .staff-role-badge {
            background: rgba(14, 165, 233, 0.25);
            transform: scale(1.05);
        }

        .staff-contacts-info {
            font-size: 0.9rem;
            color: var(--text-muted);
            word-break: break-all;
        }

        .staff-contacts-info a {
            color: var(--accent-blue);
            text-decoration: none;
            font-weight: 600;
            transition: color 0.3s ease;
        }

        .staff-contacts-info a:hover {
            color: var(--accent-blue-hover);
            text-decoration: underline;
        }

        .chart-box-wrapper {
            position: relative;
            width: 100%;
            height: 380px;
            background: linear-gradient(135deg, #090f1d 0%, #050914 100%);
            padding: 20px;
            border-radius: 16px;
            border: 1px solid var(--border-primary);
            margin-top: 15px;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.5);
        }

        .table-box-wrapper {
            width: 100%;
            overflow-x: auto;
            margin-top: 20px;
            border-radius: 16px;
            border: 1px solid var(--border-primary);
            background-color: var(--bg-secondary);
            box-shadow: inset 0 0 15px rgba(0,0,0,0.5);
        }

        .analytics-table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
            font-size: 0.95rem;
            white-space: nowrap;
        }

        .analytics-table th, .analytics-table td {
            padding: 16px 20px;
            border-bottom: 1px solid var(--border-primary);
            color: #f8fafc !important;
        }

        .analytics-table th {
            background-color: #111b33 !important;
            color: var(--accent-blue) !important;
            font-weight: 600;
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        .analytics-table tbody tr {
            background-color: #080d1a !important;
            transition: background-color 0.3s ease;
        }

        .analytics-table tr:nth-child(even) {
            background-color: #0b1222 !important;
        }

        .analytics-table tr:hover {
            background-color: rgba(14, 165, 233, 0.15) !important;
        }

        .status-up { color: var(--success-color); font-weight: bold; text-shadow: 0 0 8px rgba(34,197,94,0.3); }
        .status-stable { color: var(--accent-blue); font-weight: bold; text-shadow: 0 0 8px rgba(14,165,233,0.3); }

        .event-detailed-card {
            background: linear-gradient(135deg, rgba(14, 165, 233, 0.12), rgba(13, 21, 39, 0.95));
            border: 1px solid var(--accent-blue);
            border-radius: 16px;
            padding: 28px;
            margin-top: 25px;
            box-shadow: 0 0 30px var(--accent-glow);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .event-detailed-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 0 40px rgba(14, 165, 233, 0.45);
        }

        .event-detailed-card h3 {
            color: var(--accent-blue);
            font-size: 1.4rem;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .event-detailed-card p {
            color: #d1d5db;
            font-size: 0.95rem;
            margin-bottom: 14px;
            line-height: 1.6;
        }

        .event-benefits-list {
            list-style-type: none;
            padding-left: 0;
            margin-bottom: 20px;
        }

        .event-benefits-list li {
            position: relative;
            padding-left: 24px;
            margin-bottom: 8px;
            color: #e2e8f0;
            font-size: 0.95rem;
        }

        .event-benefits-list li::before {
            content: "✔";
            position: absolute;
            left: 0;
            color: var(--success-color);
            font-weight: bold;
        }

        .event-schedule-container {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-top: 15px;
            border-top: 1px solid var(--border-primary);
            padding-top: 15px;
        }

        .schedule-badge {
            background: #111b33;
            border: 1px solid var(--accent-blue);
            color: #ffffff;
            padding: 10px 18px;
            border-radius: 12px;
            font-weight: bold;
            font-size: 1rem;
            box-shadow: 0 0 15px rgba(14, 165, 233, 0.25);
            display: flex;
            align-items: center;
            gap: 6px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .schedule-badge:hover {
            transform: scale(1.05);
            box-shadow: 0 0 25px rgba(14, 165, 233, 0.5);
        }

        .owner-news-branch {
            background: linear-gradient(135deg, #0d1527 0%, #090e1c 100%);
            border: 1px dashed var(--accent-blue);
            border-radius: 18px;
            padding: 28px;
            margin-top: 35px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            transition: border-color 0.3s ease;
        }

        .owner-news-branch:hover {
            border-color: #38bdf8;
        }

        .owner-news-branch h3 {
            color: var(--accent-blue);
            font-size: 1.25rem;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .owner-news-branch p {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 10px;
            line-height: 1.6;
        }

        .portal-footer {
            text-align: center;
            padding: 25px 20px;
            background: linear-gradient(135deg, #0d1527 0%, #080d1a 100%);
            border: 1px solid var(--border-primary);
            border-radius: 18px;
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
    </style>
</head>
<body>

    <div class="main-container">
        
        <header class="portal-header animate-on-scroll">
            <h1>🏛️ Офіційний Портал Судової Системи Ukraine RP</h1>
            <p>Централізований державний реєстр судових проваджень, регламентів, звітності та керівного складу колегії</p>
        </header>

        <div class="hero-info-box animate-on-scroll">
            <h2>⚖️ СУД ІНФО UKRAINE RP ⚖️</h2>
            <p>Головний інформаційний центр судової системи! Тут зібрані всі офіційні правила дотримання законів, регламенти захисту прав громадян, розклад засідань та інструкції з взаємодії з державними органами на нашому сервері.</p>
            <p>Наша мета — забезпечити максимальну прозорість, справедливість та високий рівень рольової гри (RP) для кожного гравця Ukraine RP.</p>
        </div>

        <section class="content-section animate-on-scroll">
            <h2 class="section-title">📈 Біржа Активності та Статистика Суду</h2>
            <p class="section-description">Інтерактивна динаміка розгляду позовів, засідань та звернень громадян за звітні періоди:</p>
            <div class="chart-box-wrapper">
                <canvas id="courtStockChart"></canvas>
            </div>
        </section>

        <section class="content-section animate-on-scroll">
            <h2 class="section-title">⚖️ Нормативно-правова база та Правила Сервера</h2>
            <p class="section-description">Детальні інструкції щодо поведінки, етики та законності дій на сервері:</p>
            
            <div class="dropdown-element">
                <button class="dropdown-toggle-btn">
                    <span>📜 Загальна етика та правила поведінки в суді</span> 
                    <span>▼</span>
                </button>
                <div class="dropdown-panel">
                    <p><strong>Головні норми поведінки для учасників та гостей засідання:</strong></p>
                    <ul>
                        <li><strong>Форма звернення:</strong> До судді слід звертатися виключно офіційно та шанобливо — <em>«Ваша Честь»</em> або <em>«Шановний Судде»</em>.</li>
                        <li><strong>Порядок у залі:</strong> Заборонено перебивати виступи інших сторін, викрикувати, провокувати конфлікти або вести себе деструктивно.</li>
                        <li><strong>Рольова взаємодія:</strong> Усі аргументи повинні подаватися виключно через якісні RP-описи та докази (фрапси, скріншоти, свідчення очевидців).</li>
                    </ul>
                    <div class="notice-box">
                        <strong>⚠️ Важливо:</strong> Порушення регламенту розглядається як неувага до суду та карається сервером або видаленням із зали засідань.
                    </div>
                </div>
            </div>

            <div class="dropdown-element">
                <button class="dropdown-toggle-btn">
                    <span>🛡️ Правила обшуку та законність дій держструктур</span> 
                    <span>▼</span>
                </button>
                <div class="dropdown-panel">
                    <p><strong>Стандарти проведення процесуальних дій:</strong></p>
                    <ul>
                        <li>Обшук або затримання вважаються легітимними лише за наявності вагомої RP-підстави та правильного відігравання через команди <code>/me</code>, <code>/do</code>.</li>
                        <li>Будь-які докази, зібрані з порушенням серверних правил або чинного законодавства, визнаються судом недійсними.</li>
                        <li>Кожен громадянин має право на виклик адвоката та оскарження неправомірних дій у судовому порядку.</li>
                    </ul>
                </div>
            </div>

            <div class="dropdown-element">
                <button class="dropdown-toggle-btn">
                    <span>🤖 Про офіційний Судовий Бот Ukraine RP</span> 
                    <span>▼</span>
                </button>
                <div class="dropdown-panel">
                    <p>Наш інтегрований судовий бот створений для автоматизації подачі позовів, перевірки статусів справ та оперативної комунікації з громадянами.</p>
                    <p><strong>Основні можливості бота:</strong></p>
                    <ul>
                        <li>Миттєва подача електронної заяви до суду.</li>
                        <li>Сповіщення про дати та час призначених засідань.</li>
                        <li>Швидкий доступ до контактів суддів та адвокатів.</li>
                    </ul>
                </div>
            </div>
        </section>

        <section class="content-section animate-on-scroll">
            <h2 class="section-title">🏛️ Колектив суду та Адвокатура</h2>
            <p class="section-description">Офіційний кадровий склад керівництва, суддівської колегії та представників захисту:</p>
            
            <div class="staff-grid-container">
                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="Arseniy_zabanen" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '⚖️'}))">
                    </div>
                    <h3>Arseniy_zabanen</h3>
                    <div class="staff-role-badge">Головний Суддя (ГС)</div>
                    <div class="staff-contacts-info">Roblox: Arseniy_zabanen<br>TG: <a href="https://t.me/Samyry228" target="_blank">@Samyry228</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="mummu228kuku" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '🛡️'}))">
                    </div>
                    <h3>mummu228kuku</h3>
                    <div class="staff-role-badge">Заступник</div>
                    <div class="staff-contacts-info">Roblox: mummu228kuku<br>TG: <a href="https://t.me/here_everyone" target="_blank">@here_everyone</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="svervanchick" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '📜'}))">
                    </div>
                    <h3>svervanchick</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: svervanchick<br>TG: <a href="https://t.me/Svervanchik" target="_blank">@Svervanchik</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="Huhaidjopy" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '🏛️'}))">
                    </div>
                    <h3>Huhaidjopy</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: Huhaidjopy<br>TG: <a href="https://t.me/bewewewewewe" target="_blank">@bewewewewewe</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="Mr_Zver3000" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '⚡'}))">
                    </div>
                    <h3>Mr_Zver3000</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: Mr_Zver3000<br>TG: <a href="https://t.me/GreyFild_OFF" target="_blank">@GreyFild_OFF</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="Zaj_zuda3" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '💼'}))">
                    </div>
                    <h3>Zaj_zuda3</h3>
                    <div class="staff-role-badge">Адвокат</div>
                    <div class="staff-contacts-info">Roblox: Zaj_zuda3<br>TG: <a href="https://t.me/Dz7xj" target="_blank">@Dz7xj</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="heehrhrhl18" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '🔍'}))">
                    </div>
                    <h3>heehrhrhl18</h3>
                    <div class="staff-role-badge">Стажер-суддя</div>
                    <div class="staff-contacts-info">Roblox: heehrhrhl18<br>TG: <a href="https://t.me/hehr18_UR" target="_blank">@hehr18_UR</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-wrapper">
                        <img src="https://via.placeholder.com/150" alt="Itz_raose" onerror="this.replaceWith(Object.assign(document.createElement('div'), {className: 'avatar-fallback', innerText: '🔍'}))">
                    </div>
                    <h3>Itz_raose</h3>
                    <div class="staff-role-badge">Стажер-суддя</div>
                    <div class="staff-contacts-info">Roblox: Itz_raose<br>TG: <a href="https://t.me/ob1zyan" target="_blank">@ob1zyan</a></div>
                </div>
            </div>
        </section>

        <section class="content-section animate-on-scroll">
            <h2 class="section-title">📊 Детальна архівна таблиця звітів та порушень</h2>
            <p class="section-description">У звітах нижче зібрано повну статистику розгляду справ, аналіз порушень серверних регламентів та ефективність роботи колегії:</p>

            <div class="table-box-wrapper">
                <table class="analytics-table">
                    <thead>
                        <tr>
                            <th>Звітний період</th>
                            <th>Опрацьовано справ</th>
                            <th>Порушення регламентів</th>
                            <th>Статус системи</th>
                            <th>Головна подія періоду</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>4 липня – 3 серпня 2026</strong></td>
                            <td><span class="status-up">573 справи</span></td>
                            <td>9 інцидентів (Пункт 16)</td>
                            <td><span class="status-up">⚡ Штатний режим</span></td>
                            <td>Оброблено 161 звіт (502 години роботи).</td>
                        </tr>
                        <tr>
                            <td><strong>Червень – Липень 2026</strong></td>
                            <td><span class="status-up">570 справ</span></td>
                            <td>38 інцидентів</td>
                            <td><span class="status-up">🚀 Пік активності</span></td>
                            <td>Максимальна продуктивність колегії.</td>
                        </tr>
                        <tr>
                            <td><strong>Травень – Червень 2026</strong></td>
                            <td>310 справ</td>
                            <td>21 інцидент</td>
                            <td><span class="status-stable">⚖️ Стабільний режим</span></td>
                            <td>Якісне виконання регламентів.</td>
                        </tr>
                        <tr>
                            <td><strong>Січень – Лютий 2026</strong></td>
                            <td>329 засідань</td>
                            <td>29 інцидентів</td>
                            <td><span class="status-stable">🤖 Цифровізація</span></td>
                            <td>Запуск інформаційного бота.</td>
                        </tr>
                        <tr>
                            <td><strong>Грудень 2025 – Січень 2026</strong></td>
                            <td><span class="status-up">657 справ</span></td>
                            <td>52 інциденти</td>
                            <td><span class="status-up">⚡ Рекорд</span></td>
                            <td>Найвище навантаження в історії.</td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <div class="event-detailed-card">
                <h3>🏛️ Івент: День Відкритих Дверей Суду</h3>
                <p><strong>Чому цей івент корисний для гравців?</strong> День відкритих дверей — це унікальна можливість зазирнути за лаштунки судової системи, зрозуміти свої права та навчитися грамотно захищати себе в рольових ситуаціях без порушення правил сервера.</p>
                
                <p><strong>Переваги участі:</strong></p>
                <ul class="event-benefits-list">
                    <li>Живе спілкування з досвідченими суддями та адвокатами.</li>
                    <li>Розбір реальних кейсів та процесуальних помилок.</li>
                    <li>Унікальний ігровий досвід та гарний настрій.</li>
                </ul>

                <p><strong>Графік проведення івенту:</strong></p>
                <div class="event-schedule-container">
                    <span class="schedule-badge">📅 09 число місяця</span>
                    <span class="schedule-badge">📅 17 число місяця</span>
                    <span class="schedule-badge">📅 29 число місяця</span>
                </div>
            </div>

            <div class="owner-news-branch">
                <h3>📢 Новини та оновлення від керівництва суду</h3>
                <p>У цій гілці суд та власник сайту публікують актуальні внутрішні новини, майбутні оновлення судової системи, а також корисні поради щодо покращення рольової гри на сервері. Слідкуйте за оновленнями порталу, щоб бути в курсі найважливіших державних подій Ukraine RP!</p>
            </div>
        </section>

        <footer class="portal-footer animate-on-scroll">
            <p>&copy; 2026 Офіційний Портал Судової Системи Ukraine RP. Усі права захищені.</p>
        </footer>
    </div>

</body>
</html>
