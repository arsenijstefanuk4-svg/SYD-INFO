<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Судова Система</title>
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
            padding: 2rem 1rem;
            text-align: center;
            border-bottom: 2px solid var(--border-color);
        }

        h1 {
            margin: 0 0 0.5rem 0;
            color: var(--accent-color);
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

        /* Випадаючі списки (акордеон) */
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
            transition: max-height 0.3s ease-out;
            background-color: rgba(15, 23, 42, 0.5);
            border-radius: 0 0 8px 8px;
        }

        .dropdown-content.show {
            max-height: 300px;
            padding: 1rem;
            margin-top: 5px;
        }

        /* Список працівників */
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
            margin: 0 0 0.5rem 0;
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

        /* Таблиця подій */
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

        /* Адаптивність для телефонів */
        @media (max-width: 600px) {
            h1 { font-size: 1.5rem; }
            .container { padding: 1rem 0.5rem; }
            .section { padding: 1rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>Офіційний Сайт Суду</h1>
        <p>Справедливість, порядок та законність</p>
    </header>

    <div class="container">

        <div class="section">
            <h2>Про Суд</h2>
            <p>Ласкаво просимо на офіційну сторінку судової системи! Тут ви можете ознайомитися з керівництвом, правилами поведінки на засіданнях та розкладом відкритих дверей.</p>
            
            <button class="dropdown-btn"><span>⚖️ Основна інформація та правила</span> <span>▼</span></button>
            <div class="dropdown-content">
                <p><strong>Головні завдання суду:</strong> Розгляд справ, вирішення конфліктів та захист прав громадян.</p>
                <p><strong>Як себе поводити в суді:</strong></p>
                <ul>
                    <li>Дотримуватися повної тиші та порядку.</li>
                    <li>Вставати під час появи судді.</li>
                    <li>Звертатися до судді виключно "Ваша Честь".</li>
                    <li>Заборонено перебивати учасників процесу та використовувати нецензурну лексику.</li>
                </ul>
            </div>
        </div>

        <div class="section">
            <h2>Працівники суду</h2>
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
                    <div class="contacts">TG: <a href="https://t.me/Dz7xj" target="_blank">@Dz7xj</a></div>
                </div>

            </div>
        </div>

        <div class="section">
            <h2>Івент: День відкритих дверей</h2>
            <p>Запрошуємо всіх охочих відвідати наш суд, подивитися як проходять засідання та задати свої питання керівництву!</p>
            
            <table>
                <thead>
                    <tr>
                        <th>День тижня</th>
                        <th>Дата</th>
                        <th>Час (МСК/Київ)</th>
                        <th>Опис події</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>П'ятниця</td>
                        <td>Вибрана дата 1</td>
                        <td>18:00</td>
                        <td>Екскурсія залою суду та знайомство з суддями</td>
                    </tr>
                    <tr>
                        <td>Субота</td>
                        <td>Вибрана дата 2</td>
                        <td>16:00</td>
                        <td>Симуляція показового судового засідання</td>
                    </tr>
                    <tr>
                        <td>Неділя</td>
                        <td>Вибрана дата 3</td>
                        <td>15:00</td>
                        <td>Питання та відповіді від Головного Судді</td>
                    </tr>
                </tbody>
            </table>
        </div>

    </div>

    <footer>
        <p>&copy; 2026 Судова Система. Всі права захищені.</p>
    </footer>

    <script>
        // Скрипт для випадаючого списку
        const dropdownBtn = document.querySelector('.dropdown-btn');
        const dropdownContent = document.querySelector('.dropdown-content');

        dropdownBtn.addEventListener('click', function() {
            dropdownContent.classList.toggle('show');
            if (dropdownContent.classList.contains('show')) {
                this.querySelector('span:last-child').textContent = '▲';
            } else {
                this.querySelector('span:last-child').textContent = '▼';
            }
        });
    </script>

</body>
</html>
