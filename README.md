<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Судова Система | Офіційний Сайт</title>
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --text-color: #f8fafc;
            --accent-color: #38bdf8;
            --accent-hover: #0ea5e9;
            --border-color: #334155;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }

        header {
            background: linear-gradient(135deg, #1e293b, #0f172a);
            padding: 2.5rem 1rem;
            text-align: center;
            border-bottom: 2px solid var(--border-color);
        }

        h1 {
            margin: 0 0 0.5rem 0;
            color: var(--accent-color);
            font-size: 2.2rem;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        .section {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 1.5rem;
            margin-bottom: 2rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }

        h2 {
            border-bottom: 2px solid var(--accent-color);
            padding-bottom: 0.5rem;
            margin-top: 0;
            color: var(--accent-color);
        }

        /* Випадаюча кнопка (Акордеон) */
        .dropdown-btn {
            background-color: #334155;
            color: white;
            cursor: pointer;
            padding: 1rem;
            width: 100%;
            border: none;
            text-align: left;
            outline: none;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 8px;
            margin-top: 1rem;
            transition: background 0.3s;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .dropdown-btn:hover {
            background-color: var(--accent-hover);
        }

        .dropdown-content {
            padding: 0 1rem;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease-out;
            background-color: rgba(15, 23, 42, 0.5);
            border-radius: 0 0 8px 8px;
        }

        .dropdown-content.show {
            max-height: 500px;
            padding: 1rem;
            margin-top: 5px;
        }

        /* Сітка працівників суду */
        .staff-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }

        .staff-card {
            background-color: #0f172a;
            border: 1px solid var(--border-color);
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
        }

        .staff-card h3 {
            margin: 0 0 0.3rem 0;
            color: var(--text-color);
        }

        .role {
            color: var(--accent-color);
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        .contacts {
            font-size: 0.85rem;
            color: #94a3b8;
        }

        .contacts a {
            color: var(--accent-color);
            text-decoration: none;
        }

        .contacts a:hover {
            text-decoration: underline;
        }

        /* Таблиця івентів */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }

        th, td {
            border: 1px solid var(--border-color);
            padding: 0.75rem;
            text-align: left;
        }

        th {
            background-color: #334155;
            color: var(--accent-color);
        }

        tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.02);
        }

        ul {
            padding-left: 20px;
        }

        footer {
            text-align: center;
            padding: 1.5rem;
            background-color: #1e293b;
            border-top: 1px solid var(--border-color);
            color: #94a3b8;
            font-size: 0.9rem;
        }

        /* Адаптивність під мобільні пристрої */
        @media (max-width: 600px) {
            h1 { font-size: 1.6rem; }
            .container { padding: 1rem 0.5rem; }
            .section { padding: 1rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>🏛️ Офіційна Судова Система</h1>
        <p>Справедливість, порядок та законність у кожному засіданні</p>
    </header>

    <div class="container">

        <div class="section">
            <h2>Про Суд та Правила</h2>
            <p>Ласкаво просимо на офіційний портал судової системи. Тут ви можете дізнатися все про роботу наших суддів, ознайомитися з розкладом заходів та правилами поведінки.</p>
            
            <button class="dropdown-btn"><span>⚖️ Натисніть, щоб відкрити інформацію про суд і правила поведінки</span> <span>▼</span></button>
            <div class="dropdown-content">
                <p><strong>Хто ми:</strong> Наш Telegram-канал створений Головним Суддею та його Заступником для координації та інформування гравців.</p>
                <p><strong>Як себе поводити в суді:</strong></p>
                <ul>
                    <li>Ставтеся до всіх із повагою, дотримуйтесь порядку та поводьтеся адекватно.</li>
                    <li>Дотримуйтесь повної тиші, не перебивайте учасників судового процесу.</li>
                    <li>Вставайте під час появи судді та звертайтеся до нього належним чином.</li>
                    <li>Використання нецензурної лексики чи провокації суворо заборонені.</li>
                </ul>
            </div>
        </div>

        <div class="section">
            <h2>Колектив суду</h2>
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
            <h2>🏛️ День відкритих дверей у суді!</h2>
            <p>Наш суд відкриває свої двері для всіх охочих! Це чудовий шанс познайомитися з професією, особливо якщо в майбутньому ви плануєте подаватися на відкритий набір на посаду судді або в охорону.</p>
            <p><strong>⏰ Коли:</strong> З 10:00 ранку до 22:00 вечора протягом 3 днів.</p>
            
            <table>
                <thead>
                    <tr>
                        <th>День івенту</th>
                        <th>Час</th>
                        <th>Що буде на заході</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>День 1</strong> (П'ятниця)</td>
                        <td>10:00 – 22:00</td>
                        <td>Екскурсія судом, знайомство з роботою суддів зсередини.</td>
                    </tr>
                    <tr>
                        <td><strong>День 2</strong> (Субота)</td>
                        <td>10:00 – 22:00</td>
                        <td>Детальні пояснення судових процесів та відповіді на запитання.</td>
                    </tr>
                    <tr>
                        <td><strong>День 3</strong> (Неділя)</td>
                        <td>10:00 – 22:00</td>
                        <td>Фінальні відкриті консультації для майбутніх кандидатів на посади.</td>
                    </tr>
                </tbody>
            </table>
        </div>

    </div>

    <footer>
        <p>&copy; 2026 Судова Система. Всі права захищені.</p>
    </footer>

    <script>
        // Скрипт для розгортання інформації по кліку на кнопку
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
