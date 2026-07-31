<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Офіційний Портал Судової Системи - Повна версія</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* ==========================================================================
           1. CSS RESET & GLOBAL VARIABLES
           ========================================================================== */
        * { box-sizing: border-box; margin: 0; padding: 0; }
        :root {
            --bg-body: #05070c;
            --bg-card: #0e1322;
            --bg-card-hover: #161e33;
            --border-color: #1f293d;
            --accent-blue: #0ea5e9;
            --accent-hover: #38bdf8;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --success: #22c55e;
            --warning: #f59e0b;
            --danger: #ef4444;
        }

        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: var(--bg-body);
            color: var(--text-main);
            line-height: 1.6;
            padding: 20px;
        }

        .main-wrapper {
            max-width: 1200px;
            margin: 0 auto;
        }

        /* ==========================================================================
           2. HEADER COMPONENT
           ========================================================================== */
        header {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 30px;
            text-align: center;
            border-bottom: 4px solid var(--accent-blue);
            border-radius: 16px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        header h1 {
            color: var(--accent-blue);
            font-size: 28px;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 8px;
        }

        header p {
            color: var(--text-muted);
            font-size: 15px;
        }

        /* ==========================================================================
           3. SECTION STYLING
           ========================================================================== */
        .section-box {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.4);
        }

        .section-box h2 {
            color: var(--accent-blue);
            font-size: 20px;
            margin-bottom: 15px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
        }

        .section-box p {
            color: var(--text-muted);
            font-size: 14px;
            margin-bottom: 15px;
        }

        /* ==========================================================================
           4. DROPDOWN / ACCORDION MODULES
           ========================================================================== */
        .dropdown-btn {
            background: #151d30;
            color: var(--text-main);
            cursor: pointer;
            padding: 14px 18px;
            width: 100%;
            border: 1px solid var(--border-color);
            text-align: left;
            font-size: 16px;
            font-weight: 600;
            border-radius: 10px;
            margin-top: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: background 0.2s;
        }

        .dropdown-btn:hover {
            background: #1c2744;
            border-color: var(--accent-blue);
        }

        .dropdown-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease, padding 0.3s ease;
            background: #090d18;
            border-radius: 0 0 10px 10px;
            padding: 0 18px;
            border: 1px solid transparent;
        }

        .dropdown-content.show {
            max-height: 800px;
            padding: 18px;
            margin-top: 4px;
            border-color: var(--border-color);
        }

        .dropdown-content p, .dropdown-content ul {
            color: #d1d5db;
            font-size: 14px;
        }

        .dropdown-content ul {
            padding-left: 20px;
            margin-top: 8px;
        }

        .dropdown-content li {
            margin-bottom: 6px;
        }

        .info-alert {
            background: rgba(14, 165, 233, 0.08);
            border-left: 4px solid var(--accent-blue);
            padding: 12px;
            margin-top: 12px;
            border-radius: 0 8px 8px 0;
            font-size: 13px;
            color: #ffffff;
        }

        /* ==========================================================================
           5. STAFF & TEAM GRID
           ========================================================================== */
        .staff-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .staff-card {
            background: var(--bg-card-hover);
            border: 1px solid var(--border-color);
            padding: 20px;
            border-radius: 14px;
            text-align: center;
            transition: transform 0.2s, border-color 0.2s;
        }

        .staff-card:hover {
            transform: translateY(-4px);
            border-color: var(--accent-blue);
        }

        .avatar-img {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--accent-blue);
            margin-bottom: 12px;
            background: #05070c;
        }

        .staff-card h3 {
            font-size: 17px;
            margin-bottom: 4px;
            color: var(--text-main);
        }

        .staff-role {
            color: var(--accent-blue);
            font-size: 12px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 10px;
        }

        .staff-contacts {
            font-size: 13px;
            color: var(--text-muted);
        }

        .staff-contacts a {
            color: var(--accent-blue);
            text-decoration: none;
            font-weight: 600;
        }

        .staff-contacts a:hover {
            text-decoration: underline;
        }

        /* ==========================================================================
           6. CHARTS & DATA TABLES
           ========================================================================== */
        .chart-wrapper {
            position: relative;
            width: 100%;
            height: 320px;
            background: #090d18;
            padding: 15px;
            border-radius: 12px;
            border: 1px solid var(--border-color);
        }

        .table-wrapper {
            width: 100%;
            overflow-x: auto;
            margin-top: 15px;
            border-radius: 10px;
            border: 1px solid var(--border-color);
            background: #090d18;
        }

        data-table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
            font-size: 14px;
            white-space: nowrap;
        }

        th, td {
            padding: 12px 15px;
            border-bottom: 1px solid var(--border-color);
            color: var(--text-main);
        }

        th {
            background-color: #151d30;
            color: var(--accent-blue);
            font-weight: 600;
            text-transform: uppercase;
            font-size: 12px;
            letter-spacing: 1px;
        }

        tr:hover {
            background-color: rgba(14, 165, 233, 0.05);
        }

        .badge-positive { color: var(--success); font-weight: bold; }
        .badge-neutral { color: var(--accent-blue); font-weight: bold; }

        /* ==========================================================================
           7. FOOTER COMPONENT
           ========================================================================== */
        footer {
            text-align: center;
            padding: 20px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            color: var(--text-muted);
            font-size: 13px;
            margin-top: 30px;
        }
    </style>
</head>
<body>

    <div class="main-wrapper">
        
        <header>
            <h1>🏛️ Офіційний Портал Судової Системи</h1>
            <p>Державний реєстр справ, роз'яснення регламентів, статистика та склад колегії</p>
        </header>

        <div class="section-box">
            <h2>📈 Статистика та Активність Суду</h2>
            <p>Графік відображає динаміку розгляду судових справ та позовів за звітні періоди:</p>
            <div class="chart-wrapper">
                <canvas id="courtStockChart"></canvas>
            </div>
        </div>

        <div class="section-box">
            <h2>⚖️ Нормативно-правова база та Регламент</h2>
            <p>Ознайомьтеся з основними положеннями та інструкціями для учасників судових процесів:</p>
            
            <button class="dropdown-btn">
                <span>🛡️ Що таке обшук в RP і чому він законний?</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Законність процедури:</strong> Обшук — це стандартна процесуальна дія уповноважених співробітників правоохоронних органів. Якщо процедура проводиться суворо відповідно до правил сервера (з використанням команд <code>/me</code>, <code>/do</code> та за наявності обґрунтованої підстави чи ордера), вона є повністю легітимною.</p>
                <p><strong>Доказова база:</strong> Усі речові докази, знайдені в ході регламентованого обшуку, мають юридичну силу в суді.</p>
                <div class="info-alert">
                    <strong>💡 Важливо:</strong> Порушення правил проведення обшуку з боку держслужбовців тягне за собою визнання доказів недійсними.
                </div>
            </div>

            <button class="dropdown-btn">
                <span>👔 Етика та правила поведінки в залі суду</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Дотримання порядку:</strong></p>
                <ul>
                    <li>Усі присутні зобов'язані дотримуватися тиші та ставитися з повагою до суду.</li>
                    <li>Звертатися до судді слід виключно за встановленою формою («Ваша Честь»).</li>
                    <li>Категорично заборонено переривати виступи сторін або викрикувати з місця.</li>
                </ul>
                <p>За порушення порядку суддя має право накласти штраф або видалити порушника із зали засідань.</p>
            </div>

            <button class="dropdown-btn">
                <span>👥 Повноваження та обов'язки суддівського корпусу</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p>Судді здійснюють правосуддя, проводять відкриті та закриті засідання, розглядають позови громадян та держструктур, а також виносять об'єктивні вироки на основі зібраних доказів.</p>
            </div>
        </div>

        <div class="section-box">
            <h2>🏛️ Колектив суду та Адвокатура</h2>
            <p>Офіційний список керівництва, суддів та представників захисту:</p>
            
            <div class="staff-grid">
                
                <div class="staff-card">
                    <img src="https://via.placeholder.com/90/0e1322/0ea5e9?text=GS" alt="Arseniy_zabanen" class="avatar-img">
                    <h3>Arseniy_zabanen</h3>
                    <div class="staff-role">Головний Суддя</div>
                    <div class="staff-contacts">Roblox: Arseniy_zabanen<br>TG: <a href="https://t.me/Samyry228" target="_blank">@Samyry228</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://via.placeholder.com/90/0e1322/0ea5e9?text=Zast" alt="mummu228kuku" class="avatar-img">
                    <h3>mummu228kuku</h3>
                    <div class="staff-role">Заступник</div>
                    <div class="staff-contacts">Roblox: mummu228kuku<br>TG: <a href="https://t.me/here_everyone" target="_blank">@here_everyone</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://via.placeholder.com/90/0e1322/0ea5e9?text=Judge" alt="svervanchick" class="avatar-img">
                    <h3>svervanchick</h3>
                    <div class="staff-role">Суддя</div>
                    <div class="staff-contacts">Roblox: svervanchick<br>TG: <a href="https://t.me/Svervanchik" target="_blank">@Svervanchik</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://via.placeholder.com/90/0e1322/0ea5e9?text=Judge" alt="Huhaidjopy" class="avatar-img">
                    <h3>Huhaidjopy</h3>
                    <div class="staff-role">Суддя</div>
                    <div class="staff-contacts">Roblox: Huhaidjopy<br>TG: <a href="https://t.me/bewewewewewe" target="_blank">@bewewewewewe</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://via.placeholder.com/90/0e1322/0ea5e9?text=Zver" alt="Mr_Zver3000" class="avatar-img">
                    <h3>Mr_Zver3000</h3>
                    <div class="staff-role">Суддя</div>
                    <div class="staff-contacts">Roblox: Mr_Zver3000<br>TG: <a href="https://t.me/Mr_Zver3000" target="_blank">@Mr_Zver3000</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://via.placeholder.com/90/0e1322/0ea5e9?text=Lawyer" alt="Zaj_zuda3" class="avatar-img">
                    <h3>Zaj_zuda3</h3>
                    <div class="staff-role">Адвокат</div>
                    <div class="staff-contacts">Roblox: Zaj_zuda3<br>TG: <a href="https://t.me/Dz7xj" target="_blank">@Dz7xj</a></div>
                </div>

            </div>
        </div>

        <div class="section-box">
            <h2>📊 Архів судових звітів та аналітика</h2>
            <div class="table-wrapper">
                <table style="width: 100%; border-collapse: collapse;">
                    <thead>
                        <tr>
                            <th>Звітний період</th>
                            <th>Кількість справ</th>
                            <th>Випадки корупції</th>
                            <th>Статус системи</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>Червень – Липень 2026</strong></td>
                            <td><span class="badge-positive">570 справ</span></td>
                            <td>23 випадки</td>
                            <td><span class="badge-positive">🚀 Пік активності</span></td>
                        </tr>
                        <tr>
                            <td><strong>Травень – Червень 2026</strong></td>
                            <td>310 справ</td>
                            <td>13 випадків</td>
                            <td><span class="badge-neutral">⚖️ Стабільний режим</span></td>
                        </tr>
                        <tr>
                            <td><strong>Січень – Лютий 2026</strong></td>
                            <td>329 засідань</td>
                            <td>26 випадків</td>
                            <td><span class="badge-neutral">🤖 Цифровізація</span></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <footer>
            <p>&copy; 2026 Офіційний Портал Судової Системи. Усі права захищені.</p>
        </footer>

    </div>

    <script>
        // Акордеон випадаючих списків
        document.querySelectorAll('.dropdown-btn').forEach(button => {
            button.addEventListener('click', function() {
                const content = this.nextElementSibling;
                content.classList.toggle('show');
                const arrow = this.querySelector('span:last-child');
                arrow.textContent = content.classList.contains('show') ? '▲' : '▼';
            });
        });

        // Ініціалізація графіка Chart.js
        const ctx = document.getElementById('courtStockChart').getContext('2d');
        new Chart(ctx, {
            type: 'line',
            data: {
                labels: ['Вер-Жов 2025', 'Гру-Січ 2025/26', 'Січ-Лют 2026', 'Бер-Квіт 2026', 'Трав-Черв 2026', 'Черв-Лип 2026'],
                datasets: [{
                    label: 'Розглянуті справи',
                    data: [359, 657, 329, 215, 310, 570],
                    borderColor: '#0ea5e9',
                    backgroundColor: 'rgba(14, 165, 233, 0.15)',
                    borderWidth: 3,
                    fill: true,
                    tension: 0.35,
                    pointRadius: 5
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { labels: { color: '#ffffff' } }
                },
                scales: {
                    x: {
                        grid: { color: 'rgba(31, 41, 61, 0.5)' },
                        ticks: { color: '#94a3b8' }
                    },
                    y: {
                        grid: { color: 'rgba(31, 41, 61, 0.5)' },
                        ticks: { color: '#94a3b8' }
                    }
                }
            }
        });
    </script>
</body>
</html>
