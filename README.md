<!DOCTYPE html>
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
            --bg-primary: #050811;
            --bg-secondary: #0b101d;
            --bg-card: #111827;
            --bg-card-hover: #192338;
            --border-primary: #1f293d;
            --border-accent: #0ea5e9;
            --accent-blue: #0ea5e9;
            --accent-blue-hover: #38bdf8;
            --accent-glow: rgba(14, 165, 233, 0.25);
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --success-color: #22c55e;
            --warning-color: #f59e0b;
            --transition-speed: 0.3s;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-primary);
            color: var(--text-main);
            line-height: 1.7;
            padding: 25px;
            overflow-x: hidden;
        }

        .main-container {
            max-width: 1250px;
            margin: 0 auto;
        }

        .portal-header {
            background: linear-gradient(135deg, #0b101d 0%, #151d30 100%);
            border: 1px solid var(--border-primary);
            border-bottom: 4px solid var(--accent-blue);
            padding: 35px 20px;
            text-align: center;
            border-radius: 18px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6);
        }

        .portal-header h1 {
            color: var(--accent-blue);
            font-size: 2.4rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 10px;
            text-shadow: 0 0 20px var(--accent-glow);
        }

        .portal-header p {
            color: var(--text-muted);
            font-size: 1.05rem;
            max-width: 800px;
            margin: 0 auto;
        }

        /* Величезний та красивий блок СУД ІНФО */
        .hero-info-box {
            background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 100%);
            border: 2px solid var(--accent-blue);
            border-radius: 20px;
            padding: 40px 30px;
            margin-bottom: 30px;
            text-align: center;
            box-shadow: 0 0 35px rgba(14, 165, 233, 0.3);
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
            text-shadow: 0 0 30px rgba(56, 189, 248, 0.4);
        }

        .hero-info-box p {
            color: #cbd5e1;
            font-size: 1.15rem;
            max-width: 950px;
            margin: 0 auto 15px auto;
            line-height: 1.8;
        }

        .content-section {
            background-color: var(--bg-card);
            border: 1px solid var(--border-primary);
            border-radius: 18px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }

        .section-title {
            color: var(--accent-blue);
            font-size: 1.6rem;
            margin-bottom: 18px;
            border-bottom: 2px solid var(--border-primary);
            padding-bottom: 10px;
            display: inline-block;
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
            background: linear-gradient(135deg, #151d30 0%, #0e1322 100%);
            color: var(--text-main);
            cursor: pointer;
            padding: 15px 20px;
            width: 100%;
            border: 1px solid var(--border-primary);
            text-align: left;
            font-size: 1.05rem;
            font-weight: 600;
            border-radius: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all var(--transition-speed);
        }

        .dropdown-toggle-btn:hover {
            background: linear-gradient(135deg, #1c2744 0%, #151d30 100%);
            border-color: var(--accent-blue);
            transform: translateY(-2px);
        }

        .dropdown-panel {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease-out, padding 0.3s ease;
            background-color: var(--bg-secondary);
            border-radius: 0 0 12px 12px;
            padding: 0 20px;
            border: 1px solid transparent;
        }

        .dropdown-panel.expanded {
            max-height: 1200px;
            padding: 20px;
            margin-top: 4px;
            border-color: var(--border-primary);
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
            background: rgba(14, 165, 233, 0.08);
            border-left: 4px solid var(--accent-blue);
            padding: 14px;
            margin-top: 15px;
            border-radius: 0 8px 8px 0;
            font-size: 0.9rem;
            color: #ffffff;
        }

        .staff-grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .staff-profile-card {
            background: linear-gradient(135deg, #151d30 0%, #0e1322 100%);
            border: 1px solid var(--border-primary);
            padding: 30px 20px;
            border-radius: 16px;
            text-align: center;
            transition: transform var(--transition-speed), border-color var(--transition-speed), box-shadow var(--transition-speed);
            box-shadow: 0 6px 20px rgba(0,0,0,0.4);
            position: relative;
            overflow: hidden;
        }

        .staff-profile-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 4px;
            background: var(--accent-blue);
        }

        .staff-profile-card:hover {
            transform: translateY(-6px);
            border-color: var(--accent-blue);
            box-shadow: 0 10px 30px var(--accent-glow);
        }

        .staff-avatar-placeholder {
            width: 75px;
            height: 75px;
            background: rgba(14, 165, 233, 0.15);
            border: 2px solid var(--accent-blue);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            margin: 0 auto 15px auto;
            box-shadow: 0 0 15px var(--accent-glow);
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
            background: rgba(14, 165, 233, 0.1);
            padding: 4px 12px;
            border-radius: 20px;
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
        }

        .staff-contacts-info a:hover {
            color: var(--accent-blue-hover);
            text-decoration: underline;
        }

        .chart-box-wrapper {
            position: relative;
            width: 100%;
            height: 350px;
            background-color: var(--bg-secondary);
            padding: 15px;
            border-radius: 14px;
            border: 1px solid var(--border-primary);
            margin-top: 15px;
        }

        .table-box-wrapper {
            width: 100%;
            overflow-x: auto;
            margin-top: 20px;
            border-radius: 14px;
            border: 1px solid var(--border-primary);
            background-color: var(--bg-secondary);
        }

        .analytics-table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
            font-size: 0.95rem;
            white-space: nowrap;
        }

        .analytics-table th, .analytics-table td {
            padding: 14px 18px;
            border-bottom: 1px solid var(--border-primary);
            color: #f8fafc !important;
        }

        .analytics-table th {
            background-color: #151d30 !important;
            color: var(--accent-blue) !important;
            font-weight: 600;
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        .analytics-table tbody tr {
            background-color: #0b101d !important;
        }

        .analytics-table tr:nth-child(even) {
            background-color: #0f1626 !important;
        }

        .analytics-table tr:hover {
            background-color: rgba(14, 165, 233, 0.1) !important;
        }

        .status-up { color: var(--success-color); font-weight: bold; }
        .status-stable { color: var(--accent-blue); font-weight: bold; }

        .event-detailed-card {
            background: linear-gradient(135deg, rgba(14, 165, 233, 0.1), rgba(15, 23, 42, 0.95));
            border: 1px solid var(--accent-blue);
            border-radius: 14px;
            padding: 25px;
            margin-top: 25px;
            box-shadow: 0 0 25px var(--accent-glow);
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
            background: #151d30;
            border: 1px solid var(--accent-blue);
            color: #ffffff;
            padding: 10px 18px;
            border-radius: 10px;
            font-weight: bold;
            font-size: 1rem;
            box-shadow: 0 0 10px rgba(14, 165, 233, 0.2);
            display: flex;
            align-items: center;
            gap: 6px;
        }

        /* Блок новин від власника / суду внизу */
        .owner-news-branch {
            background: linear-gradient(135deg, #111827 0%, #0d1527 100%);
            border: 1px dashed var(--accent-blue);
            border-radius: 16px;
            padding: 25px;
            margin-top: 35px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
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
            background-color: var(--bg-card);
            border: 1px solid var(--border-primary);
            border-radius: 16px;
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 30px;
        }
    </style>
</head>
<body>

    <div class="main-container">
        
        <header class="portal-header">
            <h1>🏛️ Офіційний Портал Судової Системи Ukraine RP</h1>
            <p>Централізований державний реєстр судових проваджень, регламентів, звітності та керівного складу колегії</p>
        </header>

        <div class="hero-info-box">
            <h2>⚖️ СУД ІНФО UKRAINE RP ⚖️</h2>
            <p>Головний інформаційний центр судової системи! Тут зібрані всі офіційні правила дотримання законів, регламенти захисту прав громадян, розклад засідань та інструкції з взаємодії з державними органами на нашому сервері.</p>
            <p>Наша мета — забезпечити максимальну прозорість, справедливість та високий рівень рольової гри (RP) для кожного гравця Ukraine RP.</p>
        </div>

        <section class="content-section">
            <h2 class="section-title">📈 Біржа Активності та Статистика Суду</h2>
            <p class="section-description">Інтерактивна динаміка розгляду позовів, засідань та звернень громадян за звітні періоди:</p>
            <div class="chart-box-wrapper">
                <canvas id="courtStockChart"></canvas>
            </div>
        </section>

        <section class="content-section">
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

        <section class="content-section">
            <h2 class="section-title">🏛️ Колектив суду та Адвокатура</h2>
            <p class="section-description">Офіційний кадровий склад керівництва, суддівської колегії та представників захисту:</p>
            
            <div class="staff-grid-container">
                <div class="staff-profile-card">
                    <div class="staff-avatar-placeholder">⚖️</div>
                    <h3>Arseniy_zabanen</h3>
                    <div class="staff-role-badge">Головний Суддя (ГС)</div>
                    <div class="staff-contacts-info">Roblox: Arseniy_zabanen<br>TG: <a href="https://t.me/Samyry228" target="_blank">@Samyry228</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-placeholder">🏛️</div>
                    <h3>mummu228kuku</h3>
                    <div class="staff-role-badge">Заступник</div>
                    <div class="staff-contacts-info">Roblox: mummu228kuku<br>TG: <a href="https://t.me/here_everyone" target="_blank">@here_everyone</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-placeholder">📜</div>
                    <h3>svervanchick</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: svervanchick<br>TG: <a href="https://t.me/Svervanchik" target="_blank">@Svervanchik</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-placeholder">⚖️</div>
                    <h3>Huhaidjopy</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: Huhaidjopy<br>TG: <a href="https://t.me/bewewewewewe" target="_blank">@bewewewewewe</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-placeholder">🛡️</div>
                    <h3>Mr_Zver3000</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: Mr_Zver3000<br>TG: <a href="https://t.me/Mr_Zver3000" target="_blank">@Mr_Zver3000</a></div>
                </div>

                <div class="staff-profile-card">
                    <div class="staff-avatar-placeholder">💼</div>
                    <h3>Zaj_zuda3</h3>
                    <div class="staff-role-badge">Адвокат</div>
                    <div class="staff-contacts-info">Roblox: Zaj_zuda3<br>TG: <a href="https://t.me/Dz7xj" target="_blank">@Dz7xj</a></div>
                </div>
            </div>
        </section>

        <section class="content-section">
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

        <footer class="portal-footer">
            <p>&copy; 2026 Офіційний Портал Судової Системи Ukraine RP. Усі права захищені.</p>
        </footer>

    </div>

    <script>
        document.querySelectorAll('.dropdown-toggle-btn').forEach(button => {
            button.addEventListener('click', function() {
                const panel = this.nextElementSibling;
                panel.classList.toggle('expanded');
                const arrowIndicator = this.querySelector('span:last-child');
                arrowIndicator.textContent = panel.classList.contains('expanded') ? '▲' : '▼';
            });
        });

        const chartCanvasContext = document.getElementById('courtStockChart').getContext('2d');
        const courtStockChart = new Chart(chartCanvasContext, {
            type: 'line',
            data: {
                labels: ['Вер-Жов 2025', 'Гру-Січ 2025/26', 'Січ-Лют 2026', 'Бер-Квіт 2026', 'Трав-Черв 2026', 'Черв-Лип 2026'],
                datasets: [{
                    label: 'Кількість судових справ',
                    data: [359, 657, 329, 215, 310, 570],
                    borderColor: '#0ea5e9',
                    backgroundColor: 'rgba(14, 165, 233, 0.15)',
                    borderWidth: 3,
                    fill: true,
                    tension: 0.35,
                    pointRadius: 5,
                    pointBackgroundColor: '#0ea5e9'
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        labels: { color: '#ffffff', font: { family: 'Segoe UI' } }
                    }
                },
                scales: {
                    x: {
                        grid: { color: 'rgba(31, 41, 61, 0.4)' },
                        ticks: { color: '#94a3b8' }
                    },
                    y: {
                        grid: { color: 'rgba(31, 41, 61, 0.4)' },
                        ticks: { color: '#94a3b8' }
                    }
                }
            }
        });
    </script>
</body>
</html>
