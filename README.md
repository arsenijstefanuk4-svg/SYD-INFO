<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Судова Система | Офіційний Портал</title>
    <style>
        :root {
            --bg-color: #0b0f19;
            --card-bg: #111827;
            --card-hover: #1f2937;
            --text-color: #f3f4f6;
            --accent-color: #38bdf8;
            --accent-glow: rgba(56, 189, 248, 0.3);
            --border-color: #374151;
            --gold: #f59e0b;
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
            padding: 3rem 1rem;
            text-align: center;
            border-bottom: 2px solid var(--accent-color);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        h1 {
            margin: 0;
            color: var(--accent-color);
            font-size: 2.8rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 15px var(--accent-glow);
        }

        header p {
            color: #9ca3af;
            font-size: 1.1rem;
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
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
            transition: transform 0.3s ease;
        }

        .section:hover {
            border-color: #4b5563;
        }

        h2 {
            border-bottom: 2px solid var(--accent-color);
            padding-bottom: 0.5rem;
            margin-top: 0;
            color: var(--accent-color);
            font-size: 1.8rem;
        }

        /* Стильна кнопка-акордеон */
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
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
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
            background-color: rgba(15, 23, 42, 0.7);
            border-radius: 0 0 10px 10px;
            padding: 0 1.2rem;
        }

        .dropdown-content.show {
            max-height: 400px;
            padding: 1.2rem;
            margin-top: 5px;
            border: 1px solid var(--border-color);
            border-top: none;
        }

        /* Картки працівників */
        .staff-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.2rem;
            margin-top: 1.2rem;
        }

        .staff-card {
            background-color: var(--card-hover);
            border: 1px solid var(--border-color);
            padding: 1.2rem;
            border-radius: 12px;
            text-align: center;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .staff-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            box-shadow: 0 6px 20px var(--accent-glow);
        }

        .staff-card h3 {
            margin: 0.5rem 0 0.2rem 0;
            font-size: 1.2rem;
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
            color: #94a3b8;
        }

        .contacts a {
            color: var(--accent-color);
            text-decoration: none;
            font-weight: 600;
        }

        .contacts a:hover {
            text-decoration: underline;
        }

        /* Таблиці */
        .table-container {
            overflow-x: auto;
            margin-top: 1.5rem;
            border-radius: 10px;
            border: 1px solid var(--border-color);
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
            background-color: rgba(255, 255, 255, 0.01);
        }

        tr:hover {
            background-color: rgba(56, 189, 248, 0.05);
        }

        .badge-up {
            color: #4ade80;
            font-weight: bold;
        }

        .badge-stable {
            color: var(--accent-color);
            font-weight: bold;
        }

        ul {
            padding-left: 20px;
        }

        li {
            margin-bottom: 0.5rem;
        }

        footer {
            text-align: center;
            padding: 2rem;
            background-color: #0b0f19;
            border-top: 1px solid var(--border-color);
            color: #6b7280;
            font-size: 0.9rem;
        }

        /* Адаптивність для телефонів */
        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .section { padding: 1.2rem; }
            th, td { padding: 0.75rem; font-size: 0.85rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>🏛️ Судова Система Сервера</h1>
        <p>Офіційний портал правосуддя, статистики та безпеки</p>
    </header>

    <div class="container">

        <div class="section">
            <h2>Про Суд та Правила Поведінки</h2>
            <p>Наш суд гарантує справедливий розгляд справ, захист прав гравців та підтримку порядку. Телеграм-канал суду створений Головним Суддею та його Заступником.</p>
            
            <button class="dropdown-btn">
                <span>📜 Натисніть, щоб прочитати правила поведінки в суді</span> 
                <span>▼</span>
            </button>
            <div class="dropdown-content">
                <p><strong>Головні правила під час судового засідання:</strong></p>
                <ul>
                    <li>Ставтеся до всіх учасників із повагою, дотримуйтесь порядку та адекватності.</li>
                    <li>Дотримуйтесь абсолютної тиші, не перебивайте суддю та інших учасників.</li>
                    <li>Вставайте в момент появи судді та звертайтеся до нього виключно за регламентом.</li>
                    <li>Використання нецензурної лексики, образи чи провокації суворо караються.</li>
                </ul>
            </div>
        </div>

        <div class="section">
            <h2>📈 Еволюція та Статистика Суду (Історія Звітів)</h2>
            <p>Як змінювався суд із часом, скільки справ розглядалося та які покращення відбувалися від місяця до місяця:</p>
            
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Звітний період</th>
                            <th>Розглянуто справ</th>
                            <th>Боротьба з корупцією (Пункт 16)</th>
                            <th>Статус / Еволюція суду</th>
                            <th>Головні події та досягнення</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>Червень – Липень 2026</strong></td>
                            <td><span class="badge-up">570 справ</span> (677 годин)</td>
                            <td>23 випадки</td>
                            <td><span class="badge-up">🚀 Прорив / Пік активності</span></td>
                            <td>Максимальна прозорість, висока залученість суддів, стабільний правопорядок.</td>
                        </tr>
                        <tr>
                            <td><strong>Травень – Червень 2026</strong></td>
                            <td>310 справ</td>
                            <td>13 випадків</td>
                            <td><span class="badge-stable">⚖️ Стабільність</span></td>
                            <td>Збереження високої якості RP-процесу, чітке дотримання процедур.</td>
                        </tr>
                        <tr>
                            <td><strong>Квітень – Травень 2026</strong></td>
                            <td>380 справ</td>
                            <td>17 випадків</td>
                            <td><span class="badge-stable">⚖️ Стабільний розвиток</span></td>
                            <td>Зниження корупційних проявів, посилення контролю за гравцями.</td>
                        </tr>
                        <tr>
                            <td><strong>Березень – Квітень 2026</strong></td>
                            <td>215 справ</td>
                            <td>10 випадків</td>
                            <td><span class="badge-stable">🤝 Тісна співпраця</span></td>
                            <td>Спільна робота зі СБС, ДБР та НАБС, відхід заступниці (@JonDR_9620R) з почесним рекордом.</td>
                        </tr>
                        <tr>
                            <td><strong>Лютий – Березень 2026</strong></td>
                            <td>190 справ</td>
                            <td>17 випадків</td>
                            <td><span class="badge-stable">🔍 Посилений контроль</span></td>
                            <td>Боротьба з ухиленням від відповідальності (п. 23), аналіз найчастіших порушень (Green Zone).</td>
                        </tr>
                        <tr>
                            <td><strong>Січень – Лютий 2026</strong></td>
                            <td>329 судових засідань</td>
                            <td>26 випадків</td>
                            <td><span class="badge-up">🤖 Технологічність</span></td>
                            <td>Адаптація до нових правил Roblox, запуск судового бота @CourtUR_bot для апеляцій та позовів.</td>
                        </tr>
                        <tr>
                            <td><strong>Грудень 2025 – Січень 2026</strong></td>
                            <td>657 справ</td>
                            <td>43 випадки</td>
                            <td><span class="badge-up">⚡ Масштабна активність</span></td>
                            <td>Рекордне навантаження на суд, сувора боротьба з корупцією та порушеннями.</td>
                        </tr>
                        <tr>
                            <td><strong>Вересень – Жовтень 2025</strong></td>
                            <td>230 – 359 справ</td>
                            <td>23–29 вироків</td>
                            <td><span class="badge-stable">🛡️ Безпека середовища</span></td>
                            <td>Активна депортація порушників зеленої зони (пункт 33), зміцнення довіри до закону.</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <div class="section">
            <h2>👥 Колектив Суду та Адвокатура</h2>
            <div class="staff-grid">
                
                <div class="staff-card">
                    <h3>Arseniy_zabanen</h3>
                    <div class="role">Головний Суддя</div>
                    <div class="contacts">TG: <a href="https://t.me/Samyry228" target="_blank">@Samyry228</a></div>
                </div>

                <div class="staff-card">
                    <h3>mummu228kuku</h3>
                    <div class="role">Заступник Головного Судді</div>
                    <div class="contacts">TG: <a href="https://t.me/here_everyone" target="_blank">@here_everyone</a></div>
                </div>

                <div class="staff-card">
                    <h3>svervanchick</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">TG: <a href="https://t.me/Svervanchik" target="_blank">@Svervanchik</a></div>
                </div>

                <div class="staff-card">
                    <h3>Huhaidjopy</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">TG: <a href="https://t.me/bewewewewewe" target="_blank">@bewewewewewe</a></div>
                </div>

                <div class="staff-card">
                    <h3>ferd1358</h3>
                    <div class="role">Суддя</div>
                    <div class="contacts">TG: <a href="https://t.me/GreyFild_OFF" target="_blank">@GreyFild_OFF</a></div>
                </div>

                <div class="staff-card">
                    <h3>Mr_Zver3000</h3>
                    <div class="role">Суддя</div>
                </div>

                <div class="staff-card">
                    <h3>Zaj_zuda3</h3>
                    <div class="role">Адвокат</div>
                    <div class="contacts">Roblox: Zaj_zuda3<br>TG: <a href="https://t.me/Dz7xj" target="_blank">@Dz7xj</a></div>
                </div>

            </div>
        </div>

        <div class="section">
            <h2>🚪 День відкритих дверей у суді!</h2>
            <p>Наш суд відкриває свої двері для всіх охочих протягом 3 днів! Це унікальна можливість побачити роботу суддів зсередини (особливо якщо ви плануєте подаватися на набір на посаду судді або в охорону).</p>
            <p><strong>⏰ Час проведення щодня:</strong> з 10:00 ранку до 22:00 вечора.</p>
            
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
        // Скрипт для розгортання акордеона правил
        const dropdownBtn = document.querySelector('.dropdown-btn');
        const dropdownContent = document.querySelector('.dropdown-content');

        dropdownBtn.addEventListener('click', function() {
            dropdownContent.classList.toggle('show');
            const spanArrow = this.querySelector('span:last-child');
            if (dropdownContent.classList.contains('show')) {
                spanArrow.textContent = '▲';
            } else {
                spanArrow.textContent = '▼';
            }
        });
    </script>

</body>
</html>
