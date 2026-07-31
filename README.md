<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Офіційний Портал Судової Системи — Повна Розширена Версія</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* ==========================================================================
           1. CSS RESET, ROOT VARIABLES & BASE STYLES
           ========================================================================== */
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
            --danger-color: #ef4444;
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

        /* ==========================================================================
           2. HEADER COMPONENT STYLING
           ========================================================================== */
        .portal-header {
            background: linear-gradient(135deg, #0b101d 0%, #151d30 100%);
            border: 1px solid var(--border-primary);
            border-bottom: 4px solid var(--accent-blue);
            padding: 35px 20px;
            text-align: center;
            border-radius: 18px;
            margin-bottom: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6);
            position: relative;
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

        /* ==========================================================================
           3. SECTION & CONTENT BOXES
           ========================================================================== */
        .content-section {
            background-color: var(--bg-card);
            border: 1px solid var(--border-primary);
            border-radius: 18px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            transition: border-color var(--transition-speed), box-shadow var(--transition-speed);
        }

        .content-section:hover {
            border-color: rgba(14, 165, 233, 0.4);
            box-shadow: 0 15px 40px rgba(14, 165, 233, 0.1);
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

        /* ==========================================================================
           4. DROPDOWN ACCORDION MODULES
           ========================================================================== */
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
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
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
            max-height: 1000px;
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

        /* ==========================================================================
           5. STAFF & TEAM GRID CARDS (з робочими аватарами)
           ========================================================================== */
        .staff-grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .staff-profile-card {
            background-color: var(--bg-card-hover);
            border: 1px solid var(--border-primary);
            padding: 25px 15px;
            border-radius: 16px;
            text-align: center;
            transition: transform var(--transition-speed), border-color var(--transition-speed), box-shadow var(--transition-speed);
            box-shadow: 0 6px 20px rgba(0,0,0,0.4);
        }

        .staff-profile-card:hover {
            transform: translateY(-6px);
            border-color: var(--accent-blue);
            box-shadow: 0 10px 30px var(--accent-glow);
        }

        .staff-avatar-img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--accent-blue);
            margin-bottom: 15px;
            background-color: var(--bg-primary);
            box-shadow: 0 0 15px var(--accent-glow);
        }

        .staff-profile-card h3 {
            font-size: 1.15rem;
            margin-bottom: 6px;
            color: var(--text-main);
        }

        .staff-role-badge {
            color: var(--accent-blue);
            font-size: 0.75rem;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            margin-bottom: 12px;
            display: inline-block;
            background: rgba(14, 165, 233, 0.1);
            padding: 4px 10px;
            border-radius: 20px;
        }

        .staff-contacts-info {
            font-size: 0.85rem;
            color: var(--text-muted);
            word-break: break-all;
        }

        .staff-contacts-info a {
            color: var(--accent-blue);
            text-decoration: none;
            font-weight: 600;
            transition: color 0.2s;
        }

        .staff-contacts-info a:hover {
            color: var(--accent-blue-hover);
            text-decoration: underline;
        }

        /* ==========================================================================
           6. CHART & ANALYTICS MODULES
           ========================================================================== */
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
            color: var(--text-main);
        }

        .analytics-table th {
            background-color: #151d30;
            color: var(--accent-blue);
            font-weight: 600;
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        .analytics-table tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.015);
        }

        .analytics-table tr:hover {
            background-color: rgba(14, 165, 233, 0.06);
        }

        .status-up { color: var(--success-color); font-weight: bold; }
        .status-stable { color: var(--accent-blue); font-weight: bold; }

        /* ==========================================================================
           7. FOOTER COMPONENT
           ========================================================================== */
        .portal-footer {
            text-align: center;
            padding: 25px 20px;
            background-color: var(--bg-card);
            border: 1px solid var(--border-primary);
            border-radius: 16px;
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 40px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.4);
        }
    </style>
</head>
<body>

    <div class="main-container">
        
        <header class="portal-header">
            <h1>🏛️ Офіційний Портал Судової Системи</h1>
            <p>Централізований державний реєстр судових проваджень, регламентів, звітності та керівного складу колегії</p>
        </header>

        <section class="content-section">
            <h2 class="section-title">📈 Біржа Активності та Статистика Суду</h2>
            <p class="section-description">Інтерактивна динаміка розгляду позовів, засідань та звернень громадян за звітні періоди:</p>
            <div class="chart-box-wrapper">
                <canvas id="courtStockChart"></canvas>
            </div>
        </section>

        <section class="content-section">
            <h2 class="section-title">⚖️ Нормативно-правова база та Регламент</h2>
            <p class="section-description">Ознайомтеся з правилами судочинства та основними процесуальними процесами:</p>
            
            <div class="dropdown-element">
                <button class="dropdown-toggle-btn">
                    <span>🛡️ Що таке обшук в RP і чому він законний?</span> 
                    <span>▼</span>
                </button>
                <div class="dropdown-panel">
                    <p><strong>Законність процедури:</strong> Обшук є стандартною процесуальною дією уповноважених правоохоронних органів. Якщо вона виконується згідно з правилами сервера (з використанням команд <code>/me</code>, <code>/do</code> та за наявності вагомої підстави чи санкції), вона є повністю законною.</p>
                    <p><strong>Доказова база:</strong> Будь-які заборонені предмети, виявлені під час правильного RP-обшуку, вважаються легітимними доказами у судовому засіданні.</p>
                    <div class="notice-box">
                        <strong>💡 Зверніть увагу:</strong> Порушення інструкцій проведення з боку силових структур робить результати обшуку недійсними в суді.
                    </div>
                </div>
            </div>

            <div class="dropdown-element">
                <button class="dropdown-toggle-btn">
                    <span>👔 Етика та правила поведінки в залі суду</span> 
                    <span>▼</span>
                </button>
                <div class="dropdown-panel">
                    <p><strong>Загальні вимоги до учасників:</strong></p>
                    <ul>
                        <li>Дотримуйтеся абсолютної тиші та порядку під час проведення судового засідання.</li>
                        <li>Звертайтеся до судді виключно за офіційним регламентом («Ваша Честь»).</li>
                        <li>Категорично заборонено переривати виступи сторін, сперечатися без дозволу або викрикувати.</li>
                    </ul>
                    <p>За порушення регламенту суду порушник може бути притягнутий до відповідальності за неповагу.</p>
                </div>
            </div>

            <div class="dropdown-element">
                <button class="dropdown-toggle-btn">
                    <span>👥 Повноваження та обов'язки суддівського корпусу</span> 
                    <span>▼</span>
                </button>
                <div class="dropdown-panel">
                    <p>Судді здійснюють правосуддя, розглядають цивільні та кримінальні позови, борються з проявами корупції та виносять виважені, об'єктивні рішення на користь дотримання закону.</p>
                </div>
            </div>
        </section>

        <section class="content-section">
            <h2 class="section-title">🏛️ Колектив суду та Адвокатура</h2>
            <p class="section-description">Офіційний кадровий склад керівництва, суддівської колегії та представників захисту:</p>
            
            <div class="staff-grid-container">
                
                <div class="staff-profile-card">
                    <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=200&auto=format&fit=crop&q=80" alt="Arseniy_zabanen" class="staff-avatar-img">
                    <h3>Arseniy_zabanen</h3>
                    <div class="staff-role-badge">Головний Суддя (ГС)</div>
                    <div class="staff-contacts-info">Roblox: Arseniy_zabanen<br>TG: <a href="https://t.me/Samyry228" target="_blank">@Samyry228</a></div>
                </div>

                <div class="staff-profile-card">
                    <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=200&auto=format&fit=crop&q=80" alt="mummu228kuku" class="staff-avatar-img">
                    <h3>mummu228kuku</h3>
                    <div class="staff-role-badge">Заступник</div>
                    <div class="staff-contacts-info">Roblox: mummu228kuku<br>TG: <a href="https://t.me/here_everyone" target="_blank">@here_everyone</a></div>
                </div>

                <div class="staff-profile-card">
                    <img src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=200&auto=format&fit=crop&q=80" alt="svervanchick" class="staff-avatar-img">
                    <h3>svervanchick</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: svervanchick<br>TG: <a href="https://t.me/Svervanchik" target="_blank">@Svervanchik</a></div>
                </div>

                <div class="staff-profile-card">
                    <img src="https://images.unsplash.com/photo-1492562080023-ab3db95bfbce?w=200&auto=format&fit=crop&q=80" alt="Huhaidjopy" class="staff-avatar-img">
                    <h3>Huhaidjopy</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: Huhaidjopy<br>TG: <a href="https://t.me/bewewewewewe" target="_blank">@bewewewewewe</a></div>
                </div>

                <div class="staff-profile-card">
                    <img src="https://images.unsplash.com/photo-1522075469751-3a6694fb2f61?w=200&auto=format&fit=crop&q=80" alt="Mr_Zver3000" class="staff-avatar-img">
                    <h3>Mr_Zver3000</h3>
                    <div class="staff-role-badge">Суддя</div>
                    <div class="staff-contacts-info">Roblox: Mr_Zver3000<br>TG: <a href="https://t.me/Mr_Zver3000" target="_blank">@Mr_Zver3000</a></div>
                </div>

                <div class="staff-profile-card">
                    <img src="https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?w=200&auto=format&fit=crop&q=80" alt="Zaj_zuda3" class="staff-avatar-img">
                    <h3>Zaj_zuda3</h3>
                    <div class="staff-role-badge">Адвокат</div>
                    <div class="staff-contacts-info">Roblox: Zaj_zuda3<br>TG: <a href="https://t.me/Dz7xj" target="_blank">@Dz7xj</a></div>
                </div>

            </div>
        </section>

        <section class="content-section">
            <h2 class="section-title">📊 Детальна архівна таблиця звітів суду</h2>
            <div class="table-box-wrapper">
                <table class="analytics-table">
                    <thead>
                        <tr>
                            <th>Звітний період</th>
                            <th>Опрацьовано справ</th>
                            <th>Корупційні справи</th>
                            <th>Статус системи</th>
                            <th>Головна подія періоду</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>Червень – Липень 2026</strong></td>
                            <td><span class="status-up">570 справ</span></td>
                            <td>23 випадки</td>
                            <td><span class="status-up">🚀 Пік активності</span></td>
                            <td>Максимальна продуктивність колегії.</td>
                        </tr>
                        <tr>
                            <td><strong>Травень – Червень 2026</strong></td>
                            <td>310 справ</td>
                            <td>13 випадків</td>
                            <td><span class="status-stable">⚖️ Стабільний режим</span></td>
                            <td>Якісне виконання регламентів.</td>
                        </tr>
                        <tr>
                            <td><strong>Січень – Лютий 2026</strong></td>
                            <td>329 засідань</td>
                            <td>26 випадків</td>
                            <td><span class="status-stable">🤖 Цифровізація</span></td>
                            <td>Запуск інформаційного бота.</td>
                        </tr>
                        <tr>
                            <td><strong>Грудень 2025 – Січень 2026</strong></td>
                            <td><span class="status-up">657 справ</span></td>
                            <td>43 випадки</td>
                            <td><span class="status-up">⚡ Рекорд</span></td>
                            <td>Найвище навантаження в історії.</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <footer class="portal-footer">
            <p>&copy; 2026 Офіційний Портал Судової Системи. Усі права захищені.</p>
        </footer>

    </div>

    <script>
        // Скрипт для роботи випадаючих списків (акордеонів)
        document.querySelectorAll('.dropdown-toggle-btn').forEach(button => {
            button.addEventListener('click', function() {
                const panel = this.nextElementSibling;
                panel.classList.toggle('expanded');
                const arrowIndicator = this.querySelector('span:last-child');
                arrowIndicator.textContent = panel.classList.contains('expanded') ? '▲' : '▼';
            });
        });

        // Ініціалізація та побудова графіка активності за допомогою Chart.js
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
