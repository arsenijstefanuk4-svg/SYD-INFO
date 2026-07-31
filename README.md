<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Офіційний Портал Судової Системи</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --bg-gradient: radial-gradient(circle at top center, #1a233a 0%, #0a0e17 70%);
            --card-bg: rgba(17, 24, 39, 0.75);
            --card-hover: rgba(31, 41, 55, 0.85);
            --text-color: #f3f4f6;
            --text-muted: #9ca3af;
            --accent-color: #38bdf8;
            --accent-glow: rgba(56, 189, 248, 0.35);
            --border-color: rgba(75, 85, 99, 0.4);
            --green: #4ade80;
            --red: #f87171;
        }

        *, *::before, *::after {
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: var(--bg-gradient);
            background-attachment: fixed;
            color: var(--text-color);
            margin: 0;
            padding: 0;
            line-height: 1.6;
            min-height: 100vh;
            overflow-x: hidden;
        }

        header {
            background: linear-gradient(135deg, rgba(30, 27, 75, 0.9), rgba(15, 23, 42, 0.95));
            padding: 3rem 1rem;
            text-align: center;
            border-bottom: 2px solid var(--accent-color);
            box-shadow: 0 15px 35px rgba(0,0,0,0.6);
            backdrop-filter: blur(10px);
        }

        h1 {
            margin: 0;
            color: var(--accent-color);
            font-size: 2.4rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 25px var(--accent-glow);
            word-break: break-word;
        }

        header p {
            color: var(--text-muted);
            font-size: 1.05rem;
            margin-top: 0.6rem;
            word-break: break-word;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 2rem 1rem;
            width: 100%;
        }

        .section {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            backdrop-filter: blur(12px);
            border-radius: 20px;
            padding: 2rem;
            margin-bottom: 2.5rem;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
            transition: transform 0.3s ease;
        }

        .section:hover {
            border-color: rgba(56, 189, 248, 0.3);
        }

        h2 {
            border-bottom: 2px solid var(--accent-color);
            padding-bottom: 0.6rem;
            margin-top: 0;
            color: var(--accent-color);
            font-size: 1.6rem;
            word-break: break-word;
            display: inline-block;
        }

        /* Випадаючі списки (акордеони) */
        .dropdown-btn {
            background: linear-gradient(135deg, rgba(30, 41, 59, 0.8), rgba(51, 65, 85, 0.9));
            color: white;
            cursor: pointer;
            padding: 1.1rem 1.4rem;
            width: 100%;
            border: 1px solid var(--border-color);
            text-align: left;
            font-size: 1.05rem;
            font-weight: 600;
            border-radius: 12px;
            margin-top: 1.2rem;
            transition: all 0.3s ease;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .dropdown-btn:hover {
            background: linear-gradient(135deg, rgba(51, 65, 85, 0.9), rgba(71, 85, 105, 0.95));
            border-color: var(--accent-color);
            transform: translateY(-2px);
        }

        .dropdown-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease-out, padding 0.3s ease;
            background-color: rgba(15, 23, 42, 0.85);
            border-radius: 0 0 12px 12px;
            padding: 0 1.4rem;
        }

        .dropdown-content.show {
            max-height: 1200px;
            padding: 1.4rem;
            margin-top: 5px;
            border: 1px solid var(--border-color);
            border-top: none;
        }

        /* Картки працівників */
        .staff-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }

        .staff-card {
            background: var(--card-hover);
            border: 1px solid var(--border-color);
            padding: 1.5rem 1rem;
            border-radius: 16px;
            text-align: center;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .staff-card:hover {
            transform: translateY(-6px);
            border-color: var(--accent-color);
            box-shadow: 0 8px 25px var(--accent-glow);
        }

        .avatar {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--accent-color);
            margin-bottom: 1rem;
            background-color: #0b0f19;
            box-shadow: 0 0 15px var(--accent-glow);
        }

        .staff-card h3 {
            margin: 0.4rem 0;
            font-size: 1.15rem;
            color: #ffffff;
            word-break: break-word;
        }

        .role {
            color: var(--accent-color);
            font-size: 0.8rem;
            margin-bottom: 0.8rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1.5px;
        }

        .contacts {
            font-size: 0.85rem;
            color: var(--text-muted);
            word-break: break-all;
        }

        .contacts a {
            color: var(--accent-color);
            text-decoration: none;
            font-weight: 600;
        }

        .contacts a:hover {
            text-decoration: underline;
        }

        /* Графік активності */
        .chart-container {
            position: relative;
            width: 100%;
            height: 320px;
            margin-top: 1.5rem;
            background: rgba(15, 23, 42, 0.7);
            padding: 1rem;
            border-radius: 16px;
            border: 1px solid var(--border-color);
        }

        /* Таблиці */
        .table-container {
            width: 100%;
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
            margin-top: 1.5rem;
            border-radius: 14px;
            border: 1px solid var(--border-color);
            background-color: rgba(15, 23, 42, 0.8);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
            font-size: 0.9rem;
            white-space: nowrap;
        }

        th, td {
            padding: 1rem;
            border-bottom: 1px solid var(--border-color);
            color: #ffffff;
        }

        th {
            background-color: rgba(30, 41, 59, 0.9);
            color: var(--accent-color);
            font-weight: 600;
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.015);
        }

        tr:hover {
            background-color: rgba(56, 189, 248, 0.07);
        }

        .badge-up { color: var(--green); font-weight: bold; }
        .badge-down { color: var(--red); font-weight: bold; }
        .badge-stable { color: var(--accent-color); font-weight: bold; }

        ul { padding-left: 20px; color: var(--text-muted); }
        li { margin-bottom: 0.6rem; color: #ffffff; word-break: break-word; }

        p { word-break: break-word; }

        .info-box {
            background: rgba(56, 189, 248, 0.08);
            border-left: 4px solid var(--accent-color);
            padding: 1rem;
            margin: 1.2rem 0;
            border-radius: 0 10px 10px 0;
            color: #ffffff;
            word-break: break-word;
        }

        footer {
            text-align: center;
            padding: 2rem 1rem;
            background-color: rgba(10, 14, 23, 0.95);
            border-top: 1px solid var(--border-color);
            color: var(--text-muted);
            font-size: 0.9rem;
            word-break: break-word;
        }
    </style>
</head>
<body>

    <header>
        <h1>🏛️ Офіційний Портал Судової Системи</h1>
        <p>Законність, правопорядок, статистика та роз'яснення RP-процесів</p>
    </header>

    <div class="container">

        <div class="section">
            <h2>📈 Біржа Активності Суду</h2>
            <p style="color: var(--text-muted);">Інтерактивний графік відображає злети, падіння та піки продуктивності судової системи:</p>
            
            <div class="chart-container">
                <canvas id="courtStockChart"></canvas>
            </div>
            <p style="font-size: 0.82rem; color: var(--text-muted); text-align: center; margin-top: 1rem;">* Значення показують загальну кількість засідань та звернень.</p>
        </div>

        <div class="section">
            <h2>⚖️ Регламент, Правила та Процедури суду</h2>
            <p style="color: var(--text-muted);">Виберіть розділ, щоб ознайомитися з правилами та механікою гри:</p>
            
            <button class="dropdown-btn">
                <span>🛡️ Що таке обшук в RP і чому він законний?</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Законність процедури:</strong> Обшук — це стандартна процесуальна дія поліції. Якщо він проводиться суворо за правилами сервера (з використанням <code>/me</code>, <code>/do</code> та наявною на те причиною), він є повністю легітимним.</p>
                <p><strong>Доказана база:</strong> Знайдені під час правильного RP-обшуку нелегальні предмети є прямим доказом правопорушення.</p>
                <div class="info-box">
                    <strong>💡 Порада для гри:</strong> Якщо все зроблено за RP — ніякого порушення немає!
                </div>
            </div>

            <button class="dropdown-btn">
                <span>👔 Як треба і як не треба поводити себе в суді</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Як треба робити:</strong></p>
                <ul>
                    <li>Ставитися до всіх учасників з повагою, дотримуватися тиші.</li>
                    <li>Вставати під час появи судді та звертатися за регламентом.</li>
                </ul>
                <p><strong>Як категорично не можна:</strong></p>
                <ul>
                    <li>Перебивати суддю або інших учасників процесу.</li>
                    <li>Вчиняти провокації в офіційному чаті бота <code>@CourtUR_bot</code>.</li>
                </ul>
            </div>

            <button class="dropdown-btn">
                <span>👥 Обов'язки суддів та державних адвокатів</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Хто такі судді та їх обов'язки:</strong></p>
                <p>Судді проводять відкриті чи закриті засідання, розглядають позови, борються з корупцією (пункт 16) та виносять законні вироки.</p>
                <p><strong>Хто такі державні адвокати:</strong></p>
                <p>Адвокати захищають права обвинувачених громадян, готують контраргументи та представляють інтереси клієнтів у суді.</p>
            </div>
        </div>

        <div class="section">
            <h2>🏛️ Колектив суду та Адвокатура</h2>
            <div class="staff-grid">
                
                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-B4A15A631FE87B6BD4B20C3E2BB3AECC-Png/150/150/AvatarHeadshot/noFilter" alt="Arseniy_zabanen" class="avatar" onerror="this.src='https://via.placeholder.com/90/111827/38bdf8?text=GS'">
                    <h3>Arseniy_zabanen</h3>
                    <div class="role">Головний Суддя (ГС)</div>
                    <div class="contacts">Roblox: Arseniy_zabanen<br>TG: <a href="https://t.me/Samyry228" target="_blank">@Samyry228</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-11111111111111111111111111111111-Png/150/150/AvatarHeadshot/noFilter" alt="mummu228kuku" class="avatar" onerror="this.src='https://via.placeholder.com/90/111827/38bdf8?text=Zast'">
                    <h3>mummu228kuku</h3>
                    <div class="role">Заступник</div>
                    <div class="contacts">Roblox: mummu228kuku<br>TG: <a href="https://t.me/here_everyone" target="_blank">@here_everyone</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-22222222222222222222222222222222-Png/150/150/AvatarHeadshot/noFilter" alt="svervanchick" class="avatar" onerror="this.src='https://via.placeholder.com/90/111827/38bdf8?text=Judge'">
                    <h3>svervanchick</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">Roblox: svervanchick<br>TG: <a href="https://t.me/Svervanchik" target="_blank">@Svervanchik</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-33333333333333333333333333333333-Png/150/150/AvatarHeadshot/noFilter" alt="Huhaidjopy" class="avatar" onerror="this.src='https://via.placeholder.com/90/111827/38bdf8?text=Judge'">
                    <h3>Huhaidjopy</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">Roblox: Huhaidjopy<br>TG: <a href="https://t.me/bewewewewewe" target="_blank">@bewewewewewe</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-55555555555555555555555555555555-Png/150/150/AvatarHeadshot/noFilter" alt="Mr_Zver3000" class="avatar" onerror="this.src='https://via.placeholder.com/90/111827/38bdf8?text=Zver'">
                    <h3>Mr_Zver3000</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">Roblox: Mr_Zver3000<br>TG: <a href="https://t.me/Mr_Zver3000" target="_blank">@Mr_Zver3000</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-66666666666666666666666666666666-Png/150/150/AvatarHeadshot/noFilter" alt="Zaj_zuda3" class="avatar" onerror="this.src='https://via.placeholder.com/90/111827/38bdf8?text=Lawyer'">
                    <h3>Zaj_zuda3</h3>
                    <div class="role">Адвокат</div>
                    <div class="contacts">Roblox: Zaj_zuda3<br>TG: <a href="https://t.me/Dz7xj" target="_blank">@Dz7xj</a></div>
                </div>

            </div>
        </div>

        <div class="section">
            <h2>📊 Детальна таблиця еволюції суду</h2>
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Звітний період</th>
                            <th>Справ / Засідань</th>
                            <th>Корупція (П. 16)</th>
                            <th>Тренд / Статус</th>
                            <th>Головні події</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>Червень – Липень 2026</strong></td>
                            <td><span class="badge-up">570 справ</span></td>
                            <td>23 випадки</td>
                            <td><span class="badge-up">🚀 Пік</span></td>
                            <td>Максимальна продуктивність.</td>
                        </tr>
                        <tr>
                            <td><strong>Травень – Червень 2026</strong></td>
                            <td>310 справ</td>
                            <td>13 випадків</td>
                            <td><span class="badge-stable">⚖️ Стабільність</span></td>
                            <td>Якісний RP-процес.</td>
                        </tr>
                        <tr>
                            <td><strong>Січень – Лютий 2026</strong></td>
                            <td>329 засідань</td>
                            <td>26 випадків</td>
                            <td><span class="badge-stable">🤖 Цифровізація</span></td>
                            <td>Запуск бота <code>@CourtUR_bot</code>.</td>
                        </tr>
                        <tr>
                            <td><strong>Грудень 2025 – Січень 2026</strong></td>
                            <td><span class="badge-up">657 справ</span></td>
                            <td>43 випадки</td>
                            <td><span class="badge-up">⚡ Рекорд</span></td>
                            <td>Найвище навантаження в історії.</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

    </div>

    <footer>
        <p>&copy; 2026 Судова Система | Усі права захищені.</p>
    </footer>

    <script>
        const dropdownBtns = document.querySelectorAll('.dropdown-btn');
        dropdownBtns.forEach(btn => {
            btn.addEventListener('click', function() {
                const content = this.nextElementSibling;
                content.classList.toggle('show');
                const spanArrow = this.querySelector('span:last-child');
                spanArrow.textContent = content.classList.contains('show') ? '▲' : '▼';
            });
        });

        const ctx = document.getElementById('courtStockChart').getContext('2d');
        const courtStockChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: ['Вер-Жов 2025', 'Гру-Січ 2025/26', 'Січ-Лют 2026', 'Бер-Квіт 2026', 'Трав-Черв 2026', 'Черв-Лип 2026'],
                datasets: [{
                    label: 'Активність суду',
                    data: [359, 657, 329, 215, 310, 570],
                    borderColor: '#38bdf8',
                    backgroundColor: 'rgba(56, 189, 248, 0.15)',
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
                        grid: { color: 'rgba(55, 65, 81, 0.4)' },
                        ticks: { color: '#9ca3af' }
                    },
                    y: {
                        grid: { color: 'rgba(55, 65, 81, 0.4)' },
                        ticks: { color: '#9ca3af' }
                    }
                }
            }
        });
    </script>

</body>
</html>
