<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Офіційний Портал Судової Системи</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --bg-color: #0b0f19;
            --card-bg: #131c31;
            --card-hover: #1e293b;
            --text-color: #ffffff;
            --text-muted: #94a3b8;
            --accent-color: #38bdf8;
            --accent-glow: rgba(56, 189, 248, 0.4);
            --border-color: #334155;
            --green: #4ade80;
            --red: #f87171;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }

        header {
            background: linear-gradient(135deg, #1e1b4b, #0f172a, #0b0f19);
            padding: 3.5rem 1rem;
            text-align: center;
            border-bottom: 3px solid var(--accent-color);
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
        }

        h1 {
            margin: 0;
            color: var(--accent-color);
            font-size: 2.8rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 20px var(--accent-glow);
        }

        header p {
            color: var(--text-muted);
            font-size: 1.15rem;
            margin-top: 0.5rem;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        .section {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 2rem;
            margin-bottom: 2.5rem;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
        }

        h2 {
            border-bottom: 2px solid var(--accent-color);
            padding-bottom: 0.6rem;
            margin-top: 0;
            color: var(--accent-color);
            font-size: 1.8rem;
        }

        h3 {
            color: #ffffff;
            margin-top: 1.5rem;
        }

        /* Випадаючі списки (акордеони) */
        .dropdown-btn {
            background: linear-gradient(135deg, #1e293b, #334155);
            color: white;
            cursor: pointer;
            padding: 1.2rem;
            width: 100%;
            border: 1px solid var(--border-color);
            text-align: left;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 10px;
            margin-top: 1rem;
            transition: all 0.3s;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        }

        .dropdown-btn:hover {
            background: linear-gradient(135deg, #334155, #475569);
            border-color: var(--accent-color);
            transform: translateY(-2px);
        }

        .dropdown-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease-out, padding 0.3s ease;
            background-color: #0f172a;
            border-radius: 0 0 10px 10px;
            padding: 0 1.2rem;
        }

        .dropdown-content.show {
            max-height: 800px;
            padding: 1.2rem;
            margin-top: 5px;
            border: 1px solid var(--border-color);
            border-top: none;
        }

        /* Картки працівників */
        .staff-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 1.2rem;
            margin-top: 1.2rem;
        }

        .staff-card {
            background-color: var(--card-hover);
            border: 1px solid var(--border-color);
            padding: 1.5rem 1rem;
            border-radius: 12px;
            text-align: center;
            transition: all 0.3s;
        }

        .staff-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            box-shadow: 0 6px 20px var(--accent-glow);
        }

        .avatar {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid var(--accent-color);
            margin-bottom: 0.8rem;
            background-color: #0b0f19;
        }

        .staff-card h3 {
            margin: 0.3rem 0;
            font-size: 1.2rem;
            color: #ffffff;
        }

        .role {
            color: var(--accent-color);
            font-size: 0.85rem;
            margin-bottom: 0.8rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .contacts {
            font-size: 0.9rem;
            color: var(--text-muted);
        }

        .contacts a {
            color: var(--accent-color);
            text-decoration: none;
            font-weight: 600;
        }

        .contacts a:hover {
            text-decoration: underline;
        }

        /* Графік активності (Біткоїн-стиль) */
        .chart-container {
            position: relative;
            width: 100%;
            height: 380px;
            margin-top: 1.5rem;
            background: #0f172a;
            padding: 1rem;
            border-radius: 12px;
            border: 1px solid var(--border-color);
        }

        /* Таблиці */
        .table-container {
            overflow-x: auto;
            margin-top: 1.5rem;
            border-radius: 10px;
            border: 1px solid var(--border-color);
            background-color: #0f172a;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
            font-size: 0.95rem;
            white-space: nowrap;
        }

        th, td {
            padding: 1rem;
            border-bottom: 1px solid var(--border-color);
            color: #ffffff;
        }

        th {
            background-color: #1e293b;
            color: var(--accent-color);
            font-weight: 600;
            text-transform: uppercase;
            font-size: 0.85rem;
            letter-spacing: 1px;
        }

        tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.02);
        }

        tr:hover {
            background-color: rgba(56, 189, 248, 0.08);
        }

        .badge-up { color: var(--green); font-weight: bold; }
        .badge-down { color: var(--red); font-weight: bold; }
        .badge-stable { color: var(--accent-color); font-weight: bold; }

        ul { padding-left: 20px; color: var(--text-muted); }
        li { margin-bottom: 0.5rem; color: #ffffff; }

        .info-box {
            background: rgba(56, 189, 248, 0.08);
            border-left: 4px solid var(--accent-color);
            padding: 1rem;
            margin: 1rem 0;
            border-radius: 0 8px 8px 0;
            color: #ffffff;
        }

        footer {
            text-align: center;
            padding: 2rem;
            background-color: #0b0f19;
            border-top: 1px solid var(--border-color);
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .section { padding: 1.2rem; }
            th, td { padding: 0.75rem; font-size: 0.85rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>🏛️ Офіційний Портал Суду</h1>
        <p>Законність, правопорядок, статистика та роз'яснення RP-процесів</p>
    </header>

    <div class="container">

        <div class="section">
            <h2>📈 Біржа Активності Суду (Динаміка та Піки)</h2>
            <p style="color: var(--text-muted);">Інтерактивний графік відображає злети, падіння та піки продуктивності судової системи (за аналогією з криптовалютним ринком):</p>
            
            <div class="chart-container">
                <canvas id="courtStockChart"></canvas>
            </div>
            <p style="font-size: 0.85rem; color: var(--text-muted); text-align: center; margin-top: 0.8rem;">* Значення показують загальну кількість засідань та звернень за звітний період.</p>
        </div>

        <div class="section">
            <h2>⚖️ Регламент, Правила та Процедури суду</h2>
            <p style="color: var(--text-muted);">Виберіть розділ, щоб ознайомитися з правилами та механікою гри на сервері:</p>
            
            <button class="dropdown-btn">
                <span>🛡️ Що таке обшук в RP і чому він законний?</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Законність процедури:</strong> Обшук — це стандартна процесуальна дія поліції. Якщо він проводиться суворо за правилами сервера (з використанням <code>/me</code>, <code>/do</code>, правильних відігровок та наявною на те причиною чи регламентом фракції), він є повністю легітимним.</p>
                <p><strong>Доказана база:</strong> Знайдені під час правильного RP-обшуку нелегальні предмети (зброя без ліцензії, контрабанда) є прямим доказом правопорушення. З цього моменту слова гравця про «невинність» втрачають сенс.</p>
                <div class="info-box">
                    <strong>💡 Порада для гри:</strong> Якщо хтось із гравців стверджує, що обшук без якихось надзвархпотужних доказів є «порушенням» (NonRP) — не ведіться! Якщо все зроблено за RP — ніякого порушення немає!
                </div>
            </div>

            <button class="dropdown-btn">
                <span>👔 Як треба і як не треба поводити себе в суді</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Як треба робити:</strong></p>
                <ul>
                    <li>Ставитися до всіх учасників з повагою, дотримуватися тиші та адекватності.</li>
                    <li>Вставати під час появи судді та звертатися до нього виключно за регламентом.</li>
                    <li>Надавати чіткі докази та аргументи під час виступу.</li>
                </ul>
                <p><strong>Як категорично не можна:</strong></p>
                <ul>
                    <li>Перебивати суддю або інших учасників процесу.</li>
                    <li>Використовувати нецензурну лексику, ображати присутніх (пункт 1.2 правил).</li>
                    <li>Ігнорувати засідання (непредставлення — пункт 14.5).</li>
                </ul>
            </div>

            <button class="dropdown-btn">
                <span>👥 Обов'язки суддів та державних адвокатів</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Хто такі судді та їх обов'язки:</strong></p>
                <p>Судді — це гаранти справедливості на сервері. Вони проводять відкриті чи закриті засідання, розглядають позови, вивчають докази, борються з корупцією (пункт 16) та виносять законні вироки й вердикти.</p>
                <p><strong>Хто такі державні адвокати та як вони працюють:</strong></p>
                <p>Адвокати захищають права обвинувачених громадян, готують контраргументи, аналізують законність затримань чи обшуків поліцією та представляють інтереси клієнтів у суді для пом'якшення покарання або повного виправдання.</p>
            </div>
        </div>

        <div class="section">
            <h2>🏛️ Колектив суду та Адвокатура</h2>
            <div class="staff-grid">
                
                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-B4A15A631FE87B6BD4B20C3E2BB3AECC-Png/150/150/AvatarHeadshot/noFilter" alt="Arseniy_zabanen" class="avatar" onerror="this.src='https://via.placeholder.com/90/131c31/38bdf8?text=AZ'">
                    <h3>Arseniy_zabanen</h3>
                    <div class="role">Головний Суддя</div>
                    <div class="contacts">TG: <a href="https://t.me/Samyry228" target="_blank">@Samyry228</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-11111111111111111111111111111111-Png/150/150/AvatarHeadshot/noFilter" alt="mummu228kuku" class="avatar" onerror="this.src='https://via.placeholder.com/90/131c31/38bdf8?text=MK'">
                    <h3>mummu228kuku</h3>
                    <div class="role">Заступник Головного Судді</div>
                    <div class="contacts">TG: <a href="https://t.me/here_everyone" target="_blank">@here_everyone</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-22222222222222222222222222222222-Png/150/150/AvatarHeadshot/noFilter" alt="svervanchick" class="avatar" onerror="this.src='https://via.placeholder.com/90/131c31/38bdf8?text=SV'">
                    <h3>svervanchick</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">TG: <a href="https://t.me/Svervanchik" target="_blank">@Svervanchik</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-33333333333333333333333333333333-Png/150/150/AvatarHeadshot/noFilter" alt="Huhaidjopy" class="avatar" onerror="this.src='https://via.placeholder.com/90/131c31/38bdf8?text=H'">
                    <h3>Huhaidjopy</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">TG: <a href="https://t.me/bewewewewewe" target="_blank">@bewewewewewe</a></div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-55555555555555555555555555555555-Png/150/150/AvatarHeadshot/noFilter" alt="Mr_Zver3000" class="avatar" onerror="this.src='https://via.placeholder.com/90/131c31/38bdf8?text=Z'">
                    <h3>Mr_Zver3000</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">Roblox Role</div>
                </div>

                <div class="staff-card">
                    <img src="https://tr.rbxcdn.com/30DAY-AvatarHeadshot-66666666666666666666666666666666-Png/150/150/AvatarHeadshot/noFilter" alt="Zaj_zuda3" class="avatar" onerror="this.src='https://via.placeholder.com/90/131c31/38bdf8?text=ZZ'">
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
                            <td><span class="badge-up">570 справ</span> (+83.8%)</td>
                            <td>23 випадки</td>
                            <td><span class="badge-up">🚀 Пік активності</span></td>
                            <td>677 годин роботи, максимальна продуктивність.</td>
                        </tr>
                        <tr>
                            <td><strong>Травень – Червень 2026</strong></td>
                            <td>310 справ (-18.4%)</td>
                            <td>13 випадків</td>
                            <td><span class="badge-stable">⚖️ Стабільність</span></td>
                            <td>Якісний RP-процес, стабільне закриття звернень.</td>
                        </tr>
                        <tr>
                            <td><strong>Квітень – Травень 2026</strong></td>
                            <td>380 справ (+76.7%)</td>
                            <td>17 випадків</td>
                            <td><span class="badge-up">📈 Зростання</span></td>
                            <td>Зниження корупційних ризиків, посилення контролю.</td>
                        </tr>
                        <tr>
                            <td><strong>Березень – Квітень 2026</strong></td>
                            <td>215 справ (+13.1%)</td>
                            <td>10 випадків</td>
                            <td><span class="badge-stable">🤝 Кооперація</span></td>
                            <td>Співпраця з СБС, ДБР, НАБС. Відхід заступниці (@JonDR_9620R) з рекордом 572 справи.</td>
                        </tr>
                        <tr>
                            <td><strong>Лютий – Березень 2026</strong></td>
                            <td>190 справ (-42.2%)</td>
                            <td>17 випадків</td>
                            <td><span class="badge-down">📉 Спад навантаження</span></td>
                            <td>Боротьба з ухиленням (п. 23), часті порушення Зеленої Зони (п. 33).</td>
                        </tr>
                        <tr>
                            <td><strong>Січень – Лютий 2026</strong></td>
                            <td>329 засідань (-49.9%)</td>
                            <td>26 випадків</td>
                            <td><span class="badge-stable">🤖 Цифровізація</span></td>
                            <td>Адаптація до оновлень Roblox, запуск судового бота `@CourtUR_bot`.</td>
                        </tr>
                        <tr>
                            <td><strong>Грудень 2025 – Січень 2026</strong></td>
                            <td><span class="badge-up">657 справ</span> (Рекорд)</td>
                            <td>43 випадки</td>
                            <td><span class="badge-up">⚡ Гігантський пік</span></td>
                            <td>Найвище навантаження на суд за всю історію сервера.</td>
                        </tr>
                        <tr>
                            <td><strong>Вересень – Жовтень 2025</strong></td>
                            <td>230 – 359 справ</td>
                            <td>23–29 вироків</td>
                            <td><span class="badge-stable">🛡️ Захист Зони</span></td>
                            <td>Масові депортації за порушення пункту 33 (Green Zone).</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <div class="section">
            <h2>🚪 День відкритих дверей у суді (3 дні івенту)</h2>
            <p style="color: var(--text-muted);">Запрошуємо всіх гравців на відкритий івент! Ви зможете особисто побачити, як працюють судді, та підготуватися до майбутнього набору на посади.</p>
            <p><strong>⏰ Час проведення щодня:</strong> з 10:00 до 22:00.</p>
            
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>День івенту</th>
                            <th>Час</th>
                            <th>Програма заходу</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>День 1</strong> (П'ятниця)</td>
                            <td>10:00 – 22:00</td>
                            <td>Екскурсія судом, знайомство з роботою суддівського корпусу.</td>
                        </tr>
                        <tr>
                            <td><strong>День 2</strong> (Субота)</td>
                            <td>10:00 – 22:00</td>
                            <td>Пояснення внутрішніх процесів, розбір складних справ та відкритий діалог.</td>
                        </tr>
                        <tr>
                            <td><strong>День 3</strong> (Неділя)</td>
                            <td>10:00 – 22:00</td>
                            <td>Фінальні консультації для майбутніх кандидатів на посади суддів та охорони.</td>
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
        // Скрипт для випадаючих блоків
        const dropdownBtns = document.querySelectorAll('.dropdown-btn');
        dropdownBtns.forEach(btn => {
            btn.addEventListener('click', function() {
                const content = this.nextElementSibling;
                content.classList.toggle('show');
                const spanArrow = this.querySelector('span:last-child');
                if (content.classList.contains('show')) {
                    spanArrow.textContent = '▲';
                } else {
                    spanArrow.textContent = '▼';
                }
            });
        });

        // Графік активності (Bitcoin стиль)
        const ctx = document.getElementById('courtStockChart').getContext('2d');
        const courtStockChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: [
                    'Вер-Жов 2025', 
                    'Гру-Січ 2025/26', 
                    'Січ-Лют 2026', 
                    'Лют-Бер 2026', 
                    'Бер-Квіт 2026', 
                    'Квіт-Трав 2026', 
                    'Трав-Черв 2026', 
                    'Черв-Лип 2026'
                ],
                datasets: [{
                    label: 'Індекс активності та справ суду',
                    data: [359, 657, 329, 190, 215, 380, 310, 570],
                    borderColor: '#38bdf8',
                    backgroundColor: 'rgba(56, 189, 248, 0.15)',
                    borderWidth: 3,
                    fill: true,
                    tension: 0.35,
                    pointBackgroundColor: '#38bdf8',
                    pointBorderColor: '#ffffff',
                    pointRadius: 6,
                    pointHoverRadius: 9
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        labels: { color: '#ffffff', font: { size: 13 } }
                    },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                return ' Результат: ' + context.parsed.y + ' справ/засідань';
                            }
                        }
                    }
                },
                scales: {
                    x: {
                        grid: { color: 'rgba(51, 65, 85, 0.6)' },
                        ticks: { color: '#94a3b8' }
                    },
                    y: {
                        grid: { color: 'rgba(51, 65, 85, 0.6)' },
                        ticks: { color: '#94a3b8' }
                    }
                }
            }
        });
    </script>

</body>
</html>
