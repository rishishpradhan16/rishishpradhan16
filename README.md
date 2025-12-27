<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rishi - Engineer & Builder</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            background: #0a0a0a;
            color: #fff;
            overflow-x: hidden;
            line-height: 1.6;
        }

        .cursor-follower {
            position: fixed;
            width: 400px;
            height: 400px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(0, 255, 170, 0.15) 0%, transparent 70%);
            pointer-events: none;
            z-index: 1;
            transition: transform 0.2s ease-out;
            mix-blend-mode: screen;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 2rem;
            position: relative;
            z-index: 2;
        }

        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 4rem 0;
            position: relative;
        }

        .glitch-wrapper {
            position: relative;
            display: inline-block;
        }

        .hero h1 {
            font-size: clamp(3rem, 8vw, 7rem);
            font-weight: 900;
            letter-spacing: -0.03em;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, #00ffaa 0%, #00d4ff 50%, #7c3aed 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 5s ease infinite;
            background-size: 200% 200%;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .hero .tagline {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            color: #a0a0a0;
            max-width: 900px;
            margin-bottom: 3rem;
            line-height: 1.5;
        }

        .hero .tagline strong {
            color: #00ffaa;
            font-weight: 600;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin: 3rem 0;
        }

        .stat-card {
            background: linear-gradient(135deg, rgba(0, 255, 170, 0.05) 0%, rgba(0, 212, 255, 0.05) 100%);
            border: 1px solid rgba(0, 255, 170, 0.2);
            border-radius: 16px;
            padding: 1.5rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 255, 170, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .stat-card:hover::before {
            left: 100%;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            border-color: #00ffaa;
            box-shadow: 0 10px 40px rgba(0, 255, 170, 0.2);
        }

        .stat-card .icon {
            font-size: 2rem;
            margin-bottom: 0.5rem;
        }

        .stat-card h3 {
            font-size: 1rem;
            color: #00ffaa;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            margin-bottom: 0.5rem;
        }

        .stat-card p {
            color: #a0a0a0;
            font-size: 0.95rem;
        }

        .section {
            padding: 5rem 0;
            position: relative;
        }

        .section-title {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 800;
            margin-bottom: 3rem;
            background: linear-gradient(135deg, #fff 0%, #00ffaa 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
            gap: 1rem;
            margin: 2rem 0;
        }

        .tech-item {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 1.2rem 1rem;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .tech-item::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(0, 255, 170, 0.1);
            transform: translate(-50%, -50%);
            transition: width 0.5s ease, height 0.5s ease;
        }

        .tech-item:hover::after {
            width: 300px;
            height: 300px;
        }

        .tech-item:hover {
            border-color: #00ffaa;
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(0, 255, 170, 0.3);
        }

        .tech-item span {
            position: relative;
            z-index: 1;
            font-weight: 500;
            color: #e0e0e0;
        }

        .philosophy-box {
            background: linear-gradient(135deg, rgba(124, 58, 237, 0.1) 0%, rgba(0, 212, 255, 0.1) 100%);
            border-left: 4px solid #00ffaa;
            padding: 2.5rem;
            border-radius: 12px;
            margin: 3rem 0;
            position: relative;
            overflow: hidden;
        }

        .philosophy-box::before {
            content: '"';
            position: absolute;
            top: -20px;
            left: 20px;
            font-size: 8rem;
            color: rgba(0, 255, 170, 0.1);
            font-family: Georgia, serif;
        }

        .philosophy-box p {
            font-size: 1.3rem;
            line-height: 1.8;
            color: #d0d0d0;
            margin-bottom: 1rem;
            position: relative;
            z-index: 1;
        }

        .philosophy-box .motto {
            font-size: 1.1rem;
            color: #00ffaa;
            font-weight: 600;
            letter-spacing: 0.05em;
        }

        .cta-section {
            text-align: center;
            padding: 6rem 0;
        }

        .cta-button {
            display: inline-block;
            padding: 1.2rem 3rem;
            background: linear-gradient(135deg, #00ffaa 0%, #00d4ff 100%);
            color: #0a0a0a;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 700;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0, 255, 170, 0.3);
        }

        .cta-button::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.6s ease, height 0.6s ease;
        }

        .cta-button:hover::before {
            width: 300px;
            height: 300px;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 50px rgba(0, 255, 170, 0.5);
        }

        .cta-button span {
            position: relative;
            z-index: 1;
        }

        .floating-shapes {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .shape {
            position: absolute;
            border-radius: 50%;
            opacity: 0.03;
            animation: float 20s infinite ease-in-out;
        }

        .shape:nth-child(1) {
            width: 300px;
            height: 300px;
            background: linear-gradient(135deg, #00ffaa, #00d4ff);
            top: 10%;
            left: 10%;
            animation-delay: 0s;
        }

        .shape:nth-child(2) {
            width: 400px;
            height: 400px;
            background: linear-gradient(135deg, #7c3aed, #00d4ff);
            top: 60%;
            right: 10%;
            animation-delay: -5s;
        }

        .shape:nth-child(3) {
            width: 250px;
            height: 250px;
            background: linear-gradient(135deg, #00ffaa, #7c3aed);
            bottom: 10%;
            left: 30%;
            animation-delay: -10s;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(50px, -50px) rotate(120deg); }
            66% { transform: translate(-30px, 30px) rotate(240deg); }
        }

        .card-3d {
            background: rgba(15, 15, 15, 0.8);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2.5rem;
            backdrop-filter: blur(20px);
            transition: all 0.3s ease;
        }

        .card-3d:hover {
            transform: translateZ(20px) rotateX(2deg) rotateY(2deg);
            border-color: #00ffaa;
            box-shadow: 0 20px 60px rgba(0, 255, 170, 0.2);
        }

        @media (max-width: 768px) {
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .tech-grid {
                grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            }
        }
    </style>
</head>
<body>
    <div class="cursor-follower" id="cursorFollower"></div>
    <div class="floating-shapes">
        <div class="shape"></div>
        <div class="shape"></div>
        <div class="shape"></div>
    </div>

    <div class="container">
        <section class="hero">
            <div class="glitch-wrapper">
                <h1>👋 Hey — I'm Rishi</h1>
            </div>
            <p class="tagline">
                <strong>Figure-it-out mindset.</strong> If it matters, I'll build it, automate it, or power it with AI — and make it work.
            </p>

            <div class="stats-grid">
                <div class="stat-card">
                    <div class="icon">🧠</div>
                    <h3>Automation</h3>
                    <p>Testing • Backend • Systems</p>
                </div>
                <div class="stat-card">
                    <div class="icon">⚡</div>
                    <h3>Solo Builder</h3>
                    <p>Apps • Workflows • Growth</p>
                </div>
                <div class="stat-card">
                    <div class="icon">🤖</div>
                    <h3>AI-Powered</h3>
                    <p>Faster, Smarter, Better</p>
                </div>
                <div class="stat-card">
                    <div class="icon">🚀</div>
                    <h3>Ship Fast</h3>
                    <p>Real-world Solutions</p>
                </div>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">🚀 What I Love Building</h2>
            <div class="card-3d">
                <div class="stats-grid">
                    <div class="stat-card">
                        <h3>Automation</h3>
                        <p>Frameworks & logical workflows that eliminate repetitive tasks</p>
                    </div>
                    <div class="stat-card">
                        <h3>Products</h3>
                        <p>Real-world apps & internal tools that solve actual problems</p>
                    </div>
                    <div class="stat-card">
                        <h3>Growth Systems</h3>
                        <p>Content engines & systems that scale organically</p>
                    </div>
                    <div class="stat-card">
                        <h3>Experiments</h3>
                        <p>Wild ideas that turn into working solutions</p>
                    </div>
                </div>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">🛠 Tech & Tools</h2>
            <div class="tech-grid">
                <div class="tech-item"><span>Automation</span></div>
                <div class="tech-item"><span>Java</span></div>
                <div class="tech-item"><span>Selenium</span></div>
                <div class="tech-item"><span>TestNG</span></div>
                <div class="tech-item"><span>Android</span></div>
                <div class="tech-item"><span>Gradle</span></div>
                <div class="tech-item"><span>AdMob</span></div>
                <div class="tech-item"><span>Git</span></div>
                <div class="tech-item"><span>Jenkins</span></div>
                <div class="tech-item"><span>CI/CD</span></div>
                <div class="tech-item"><span>AI Tools</span></div>
                <div class="tech-item"><span>Prompts</span></div>
            </div>
            <p style="text-align: center; color: #a0a0a0; margin-top: 2rem; font-style: italic;">
                If the work demands a new tool — I learn it and ship.
            </p>
        </section>

        <section class="section">
            <h2 class="section-title">📌 Core Philosophy</h2>
            <div class="philosophy-box">
                <p>Learn fast. Break things. Understand systems.</p>
                <p>Then rebuild — cleaner, faster, and stronger.</p>
                <p class="motto">Consistency × Curiosity × Execution</p>
            </div>
        </section>

        <section class="cta-section">
            <h2 class="section-title">📬 Let's Connect</h2>
            <p style="font-size: 1.2rem; color: #a0a0a0; margin-bottom: 2rem;">
                If you're building something meaningful — I'd love to talk.
            </p>
            <a href="mailto:your.email@example.com" class="cta-button">
                <span>Get In Touch →</span>
            </a>
        </section>
    </div>

    <script>
        const follower = document.getElementById('cursorFollower');
        let mouseX = 0, mouseY = 0;
        let followerX = 0, followerY = 0;

        document.addEventListener('mousemove', (e) => {
            mouseX = e.clientX;
            mouseY = e.clientY;
        });

        function animate() {
            const dx = mouseX - followerX;
            const dy = mouseY - followerY;
            
            followerX += dx * 0.1;
            followerY += dy * 0.1;
            
            follower.style.transform = `translate(${followerX - 200}px, ${followerY - 200}px)`;
            
            requestAnimationFrame(animate);
        }

        animate();

        const cards = document.querySelectorAll('.stat-card, .tech-item, .card-3d');
        cards.forEach(card => {
            card.addEventListener('mouseenter', () => {
                card.style.transform = 'translateY(-8px) scale(1.02)';
            });
            card.addEventListener('mouseleave', () => {
                card.style.transform = 'translateY(0) scale(1)';
            });
        });
    </script>
</body>
</html>
