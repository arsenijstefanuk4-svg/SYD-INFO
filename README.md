<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Технічні роботи — Ukraine RP</title>
    <style>
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        :root {
            --bg-primary: #030712;
            --bg-secondary: #090f1d;
            --accent-blue: #0ea5e9;
            --accent-glow: rgba(14, 165, 233, 0.35);
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: linear-gradient(135deg, #020617 0%, #090d1f 50%, #030712 100%);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .maintenance-card {
            background: linear-gradient(135deg, rgba(13, 21, 39, 0.95) 0%, rgba(8, 13, 26, 0.95) 100%);
            border: 2px solid var(--accent-blue);
            border-radius: 24px;
            padding: 50px 30px;
            max-width: 600px;
            width: 100%;
            text-align: center;
            box-shadow: 0 0 50px var(--accent-glow);
            position: relative;
            overflow: hidden;
        }

        .maintenance-icon {
            font-size: 4rem;
            margin-bottom: 20px;
            animation: bounce 2s infinite ease-in-out;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        h1 {
            font-size: clamp(1.8rem, 4vw, 2.5rem);
            color: var(--accent-blue);
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 20px var(--accent-glow);
        }

        p {
            color: var(--text-muted);
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        .status-badge {
            display: inline-block;
            background: rgba(14, 165, 233, 0.15);
            color: var(--accent-blue);
            border: 1px solid rgba(14, 165, 233, 0.3);
            padding: 8px 20px;
            border-radius: 30px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 0.9rem;
            box-shadow: 0 0 15px rgba(14, 165, 233, 0.2);
        }
    </style>
</head>
<body>

    <div class="maintenance-card">
        <div class="maintenance-icon">🛠️</div>
        <h1>Технічні роботи</h1>
        <p>Наразі на сайті проводяться планові технічні оновлення та покращення. Ми працюємо над тим, щоб зробити сервіс ще кращим. Дякуємо за ваше розуміння!</p>
        <div class="status-badge">Скоро повернемося</div>
    </div>

</body>
</html>
