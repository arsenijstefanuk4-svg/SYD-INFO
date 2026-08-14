from pathlib import Path
import re

src = Path("/mnt/data/Ukraine_RP_court_updated.html")
out = Path("/mnt/data/Ukraine_RP_court_final.html")
html = src.read_text(encoding="utf-8")

# Remove the 3 people from blacklist, keeping ONLY heehrhrhl18.
for name in ["Mr_Zver3000", "Itz_raose", "svervanchick"]:
    pattern = re.compile(
        rf'\s*<div class="blacklist-card">\s*'
        rf'<div class="blacklist-icon">.*?</div>\s*'
        rf'<h3>{re.escape(name)}</h3>.*?</div>\s*',
        re.S
    )
    html, count = pattern.subn("\n", html)
    if count == 0:
        # tolerate a previous formatting variation
        pass

# Improve visual system: glow, glass, animated borders, scanline, headings.
extra_css = r"""
        /* ===== PREMIUM VISUAL UPGRADE ===== */
        :root {
            --neon-blue: #38bdf8;
            --neon-purple: #a78bfa;
            --neon-cyan: #22d3ee;
            --neon-red: #ff4d6d;
        }

        body {
            background:
                radial-gradient(circle at 15% 15%, rgba(14,165,233,.16), transparent 28%),
                radial-gradient(circle at 85% 80%, rgba(139,92,246,.14), transparent 30%),
                radial-gradient(circle at 50% 45%, rgba(34,211,238,.05), transparent 35%),
                #020617;
        }

        body::before {
            animation: floatGlow1 9s ease-in-out infinite alternate, hueDrift 12s linear infinite;
        }

        body::after {
            animation: floatGlow2 11s ease-in-out infinite alternate-reverse, hueDrift 15s linear infinite reverse;
        }

        @keyframes hueDrift {
            0% { filter: blur(80px) hue-rotate(0deg); }
            50% { filter: blur(95px) hue-rotate(35deg); }
            100% { filter: blur(80px) hue-rotate(0deg); }
        }

        .main-container {
            position: relative;
        }

        .content-section,
        .event-detailed-card,
        .owner-news-branch,
        .portal-footer {
            position: relative;
            isolation: isolate;
        }

        .content-section::before,
        .event-detailed-card::before,
        .owner-news-branch::before {
            content: "";
            position: absolute;
            inset: 0;
            border-radius: inherit;
            background: linear-gradient(115deg, transparent 20%, rgba(56,189,248,.08) 50%, transparent 80%);
            transform: translateX(-120%);
            animation: lightSweep 7s ease-in-out infinite;
            pointer-events: none;
            z-index: -1;
        }

        @keyframes lightSweep {
            0%, 45% { transform: translateX(-120%); }
            65%, 100% { transform: translateX(120%); }
        }

        .section-title {
            position: relative;
            text-shadow:
                0 0 8px rgba(56,189,248,.5),
                0 0 24px rgba(56,189,248,.25);
            animation: titleGlow 3s ease-in-out infinite alternate;
        }

        .section-title::after {
            content: "";
            position: absolute;
            left: 0;
            bottom: -2px;
            width: 42%;
            height: 2px;
            background: linear-gradient(90deg, var(--neon-blue), transparent);
            box-shadow: 0 0 12px var(--neon-blue);
            animation: titleLine 2.5s ease-in-out infinite alternate;
        }

        @keyframes titleGlow {
            from { filter: brightness(1); }
            to { filter: brightness(1.3); }
        }

        @keyframes titleLine {
            from { width: 30%; opacity: .55; }
            to { width: 70%; opacity: 1; }
        }

        .dropdown-toggle-btn {
            position: relative;
            overflow: hidden;
            box-shadow: inset 0 0 0 1px rgba(56,189,248,.03), 0 8px 25px rgba(0,0,0,.25);
        }

        .dropdown-toggle-btn::before {
            content: "";
            position: absolute;
            top: 0;
            left: -120%;
            width: 70%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,.12), transparent);
            transform: skewX(-20deg);
            transition: none;
            animation: buttonShine 5s ease-in-out infinite;
        }

        @keyframes buttonShine {
            0%, 55% { left: -120%; }
            80%, 100% { left: 140%; }
        }

        .dropdown-element {
            animation: dropIn .7s cubic-bezier(.16,1,.3,1) both;
        }

        .dropdown-element:nth-child(2) { animation-delay: .08s; }
        .dropdown-element:nth-child(3) { animation-delay: .16s; }
        .dropdown-element:nth-child(4) { animation-delay: .24s; }
        .dropdown-element:nth-child(5) { animation-delay: .32s; }

        @keyframes dropIn {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .chart-box-wrapper {
            border-color: rgba(56,189,248,.45);
            box-shadow:
                inset 0 0 45px rgba(0,0,0,.9),
                0 0 25px rgba(14,165,233,.18),
                0 0 70px rgba(14,165,233,.08);
            animation: chartFrame 3s ease-in-out infinite alternate;
        }

        @keyframes chartFrame {
            from { border-color: rgba(56,189,248,.3); }
            to { border-color: rgba(167,139,250,.65); }
        }

        /* ЗБІЙ біржі */
        .market-glitch {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            margin-left: 10px;
            padding: 5px 11px;
            border: 1px solid rgba(255,77,109,.45);
            border-radius: 999px;
            background: rgba(255,77,109,.10);
            color: #ff8da1;
            font-size: .72rem;
            font-weight: 900;
            letter-spacing: 1px;
            text-transform: uppercase;
            box-shadow: 0 0 18px rgba(255,77,109,.15);
            animation: glitchBadge 1.8s steps(2,end) infinite;
        }

        .market-glitch::before {
            content: "●";
            color: #ff4d6d;
            text-shadow: 0 0 10px #ff4d6d;
            animation: glitchDot .65s infinite alternate;
        }

        @keyframes glitchBadge {
            0%, 78%, 100% { transform: translateX(0); opacity: .85; }
            80% { transform: translateX(-2px); }
            84% { transform: translateX(2px); }
            88% { transform: translateX(-1px); opacity: 1; }
        }

        @keyframes glitchDot {
            from { opacity: .35; }
            to { opacity: 1; }
        }

        /* Чорний список — тільки heehrhrhl18 */
        .blacklist-section {
            background:
                radial-gradient(circle at 90% 10%, rgba(239,68,68,.14), transparent 30%),
                linear-gradient(135deg, rgba(69,10,10,.32), rgba(7,12,24,.96));
            border: 1px solid rgba(239,68,68,.4);
            box-shadow:
                0 20px 55px rgba(0,0,0,.7),
                0 0 35px rgba(239,68,68,.08),
                inset 0 0 40px rgba(239,68,68,.04);
        }

        .blacklist-card {
            max-width: 420px;
        }

        .blacklist-card h3 {
            text-shadow: 0 0 15px rgba(255,120,120,.35);
        }

        /* Фонові декоративні лінії */
        .main-container::before,
        .main-container::after {
            content: "";
            position: fixed;
            top: 0;
            bottom: 0;
            width: 1px;
            background: linear-gradient(transparent, rgba(56,189,248,.25), transparent);
            pointer-events: none;
            z-index: -1;
        }

        .main-container::before { left: 3vw; }
        .main-container::after { right: 3vw; }

        /* Поважаємо reduced motion */
        @media (prefers-reduced-motion: reduce) {
            *, *::before, *::after {
                animation-duration: .01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: .01ms !important;
            }
        }
"""
html = html.replace("    </style>", extra_css + "\n    </style>", 1)

# Change stock title to include a glitch badge.
html = html.replace(
    '<h2 class="section-title">📈 Біржа Активності та Статистика Суду</h2>',
    '<h2 class="section-title">📈 Біржа Активності та Статистика Суду <span class="market-glitch">ЗБІЙ СИСТЕМИ</span></h2>',
    1
)

# Replace the current chart script with a controlled 12-second chaotic jump animation,
# then settle exactly on the target values.
script_pattern = re.compile(
    r'            // Налаштування та запуск графіка.*?            const chartCanvas = document\.getElementById\(\'courtStockChart\'\);.*?\n        \}\);',
    re.S
)

new_script = r"""            // ===== БІРЖА: 12-СЕКУНДНИЙ КОНТРОЛЬОВАНИЙ ЗБІЙ =====
            const ctx = document.getElementById('courtStockChart').getContext('2d');
            const chartGradient = ctx.createLinearGradient(0, 0, 0, 400);
            chartGradient.addColorStop(0, 'rgba(14, 165, 233, 0.55)');
            chartGradient.addColorStop(1, 'rgba(14, 165, 233, 0.0)');

            const marketLabels = ['Січень', 'Лютий', 'Березень', 'Квітень', 'Травень', 'Червень', 'Липень', 'Серпень (+)', 'Вересень (План)'];
            const finalMarketData = [210, 260, 329, 390, 440, 570, 573, 640, 710];

            const marketChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: marketLabels,
                    datasets: [{
                        label: 'Динаміка успішно розглянутих справ',
                        data: [...finalMarketData],
                        borderColor: '#38bdf8',
                        borderWidth: 4,
                        pointBackgroundColor: '#818cf8',
                        pointBorderColor: '#ffffff',
                        pointBorderWidth: 2,
                        pointRadius: 6,
                        pointHoverRadius: 10,
                        backgroundColor: chartGradient,
                        fill: true,
                        tension: 0.42
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    animation: {
                        duration: 1100,
                        easing: 'easeOutQuart'
                    },
                    plugins: {
                        legend: {
                            labels: {
                                color: '#f8fafc',
                                font: { size: 13, family: "'Segoe UI', Roboto, sans-serif" }
                            }
                        },
                        tooltip: {
                            backgroundColor: 'rgba(3, 7, 18, .96)',
                            titleColor: '#38bdf8',
                            bodyColor: '#f8fafc',
                            borderColor: '#38bdf8',
                            borderWidth: 1,
                            padding: 12
                        }
                    },
                    scales: {
                        x: {
                            grid: { color: 'rgba(30, 41, 59, 0.5)' },
                            ticks: { color: '#94a3b8', font: { size: 12 } }
                        },
                        y: {
                            grid: { color: 'rgba(30, 41, 59, 0.5)' },
                            ticks: { color: '#94a3b8', font: { size: 12 } }
                        }
                    }
                }
            });

            const marketStart = performance.now();
            let marketFinished = false;

            function marketGlitchFrame(now) {
                if (marketFinished) return;

                const elapsed = now - marketStart;
                const progress = Math.min(elapsed / 12000, 1);

                if (progress < 0.88) {
                    // Спочатку слабко, потім сильні "стрибки", далі знову стабілізація.
                    const chaos = Math.sin(progress * Math.PI) * (110 + 150 * Math.sin(progress * 5.5) ** 2);

                    marketChart.data.datasets[0].data = finalMarketData.map((value, i) => {
                        const wave =
                            Math.sin(elapsed / 145 + i * 1.7) * chaos +
                            Math.cos(elapsed / 75 + i * 2.1) * chaos * 0.42;
                        const randomKick = (Math.random() - 0.5) * chaos * 0.75;
                        return Math.max(40, value + wave + randomKick);
                    });

                    // Ефект "збою": бірюзовий → фіолетовий → червоний → назад до синього.
                    const hue = (190 + progress * 360 + Math.sin(elapsed / 180) * 35) % 360;
                    const lineColor = `hsl(${hue}, 100%, 68%)`;
                    const fillColor = `hsla(${hue}, 100%, 55%, .22)`;

                    marketChart.data.datasets[0].borderColor = lineColor;
                    marketChart.data.datasets[0].backgroundColor = fillColor;
                    marketChart.data.datasets[0].pointBackgroundColor = lineColor;

                    ctx.canvas.style.filter =
                        `drop-shadow(0 0 ${10 + Math.abs(Math.sin(elapsed / 120)) * 18}px ${lineColor})`;

                    marketChart.update('none');
                    requestAnimationFrame(marketGlitchFrame);
                } else {
                    marketFinished = true;

                    // Фінальний "зліт" закінчується точним поверненням на свої місця.
                    marketChart.data.datasets[0].data = [...finalMarketData];
                    marketChart.data.datasets[0].borderColor = '#38bdf8';
                    marketChart.data.datasets[0].backgroundColor = chartGradient;
                    marketChart.data.datasets[0].pointBackgroundColor = '#818cf8';

                    marketChart.update({
                        duration: 1450,
                        easing: 'easeOutElastic'
                    });

                    setTimeout(() => {
                        ctx.canvas.style.filter = 'drop-shadow(0 0 12px rgba(56,189,248,.45))';
                    }, 1450);
                }
            }

            requestAnimationFrame(marketGlitchFrame);
        });"""

if not script_pattern.search(html):
    raise RuntimeError("Не знайдено поточний блок JS графіка для заміни")
html = script_pattern.sub(new_script, html, count=1)

out.write_text(html, encoding="utf-8")
print(out)
print("Готово: чорний список залишено лише для heehrhrhl18; три інші просто прибрані з активного складу.")
print("Біржа: 12 секунд хаотичної анімації + кольоровий glitch + точне повернення до фінальних значень.")
