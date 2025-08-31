<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>await - GitHub Profile</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600&family=Inter:wght@300;400;500;600;700&display=swap');
        
        :root {
            --bg-primary: #0d1117;
            --bg-secondary: #161b22;
            --accent-primary: #58a6ff;
            --accent-secondary: #f778ba;
            --text-primary: #f0f6fc;
            --text-secondary: #c9d1d9;
            --card-bg: rgba(22, 27, 34, 0.8);
            --gradient: linear-gradient(135deg, #58a6ff, #f778ba);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background-color: var(--bg-primary);
            color: var(--text-primary);
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 15% 50%, rgba(88, 166, 255, 0.1) 0%, transparent 25%),
                radial-gradient(circle at 85% 30%, rgba(247, 120, 186, 0.1) 0%, transparent 25%);
        }
        
        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        header {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
            padding-top: 2rem;
        }
        
        .avatar {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid transparent;
            background: var(--gradient) border-box;
            mask: 
                linear-gradient(#fff 0 0) padding-box, 
                linear-gradient(#fff 0 0);
            mask-composite: exclude;
            -webkit-mask-composite: xor;
            margin: 0 auto 1.5rem;
            box-shadow: 0 0 30px rgba(88, 166, 255, 0.3);
            transition: transform 0.5s ease;
        }
        
        .avatar:hover {
            transform: scale(1.05);
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 0.5rem;
            background: var(--gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: 700;
        }
        
        .subtitle {
            font-size: 1.3rem;
            color: var(--text-secondary);
            margin-bottom: 1.5rem;
            font-weight: 300;
        }
        
        .tagline {
            display: inline-block;
            background: var(--card-bg);
            padding: 0.5rem 1.2rem;
            border-radius: 30px;
            font-size: 1.1rem;
            margin-bottom: 2rem;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }
        
        .bio {
            max-width: 600px;
            margin: 0 auto 2rem;
            text-align: center;
            color: var(--text-secondary);
            font-size: 1.1rem;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-bottom: 3rem;
        }
        
        .stat-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 1.5rem;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }
        
        .stat-value {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            background: var(--gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .stat-label {
            color: var(--text-secondary);
            font-size: 1rem;
        }
        
        .skills {
            margin-bottom: 3rem;
        }
        
        .section-title {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            position: relative;
            display: inline-block;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 50px;
            height: 3px;
            background: var(--gradient);
            border-radius: 3px;
        }
        
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
        }
        
        .skill-item {
            background: var(--card-bg);
            padding: 1rem;
            border-radius: 12px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease;
        }
        
        .skill-item:hover {
            transform: translateY(-3px);
        }
        
        .projects {
            margin-bottom: 3rem;
        }
        
        .project-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }
        
        .project-title {
            font-size: 1.4rem;
            margin-bottom: 0.5rem;
            color: var(--accent-primary);
        }
        
        .project-desc {
            color: var(--text-secondary);
            margin-bottom: 1rem;
        }
        
        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }
        
        .tech-tag {
            background: rgba(88, 166, 255, 0.15);
            color: var(--accent-primary);
            padding: 0.3rem 0.7rem;
            border-radius: 20px;
            font-size: 0.85rem;
            font-family: 'Fira Code', monospace;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-top: 2rem;
        }
        
        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--card-bg);
            color: var(--text-primary);
            text-decoration: none;
            font-size: 1.5rem;
            transition: transform 0.3s ease, background 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .social-link:hover {
            transform: translateY(-5px);
            background: var(--gradient);
        }
        
        .floating-icons {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .floating-icon {
            position: absolute;
            font-size: 1.5rem;
            opacity: 0.1;
            color: var(--accent-primary);
            animation: float 15s infinite linear;
        }
        
        @keyframes float {
            0% {
                transform: translateY(0) rotate(0deg);
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
            }
        }
        
        .typewriter {
            overflow: hidden;
            border-right: 0.15em solid var(--accent-primary);
            white-space: nowrap;
            margin: 0 auto;
            letter-spacing: 0.15em;
            animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: var(--accent-primary) }
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 1.5rem;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .subtitle {
                font-size: 1.1rem;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .avatar {
                width: 150px;
                height: 150px;
            }
        }
        
        .coffee-counter {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            margin-top: 1rem;
            font-size: 1.2rem;
        }
        
        .coffee-icon {
            color: #ffa657;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>
    <div class="floating-icons">
        <div class="floating-icon" style="top: 10%; left: 5%;">⚡</div>
        <div class="floating-icon" style="top: 20%; left: 90%;">🐱</div>
        <div class="floating-icon" style="top: 40%; left: 15%;">🚀</div>
        <div class="floating-icon" style="top: 60%; left: 80%;">💻</div>
        <div class="floating-icon" style="top: 80%; left: 10%;">✨</div>
        <div class="floating-icon" style="top: 30%; left: 70%;">🔧</div>
        <div class="floating-icon" style="top: 70%; left: 30%;">🎯</div>
    </div>
    
    <div class="container">
        <header>
            <img src="https://avatars.githubusercontent.com/u/placeholder" alt="await" class="avatar">
            <h1>await</h1>
            <p class="subtitle">Software Engineer & Coffee Enthusiast</p>
            <div class="tagline">
                <span class="typewriter">Hello, I'm SocketSomeone your Software Engineer</span>
            </div>
            <p class="bio">
                You just found my profile! I'm a kitten who loves coffee and bugs! (*:ω*)♦<br>
                Passionate about creating elegant solutions to complex problems.
            </p>
            <div class="coffee-counter">
                <span class="coffee-icon">☕</span>
                <span id="coffee-count">1274</span>
                <span>cups of coffee and counting...</span>
            </div>
        </header>
        
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-value" id="repos">42</div>
                <div class="stat-label">Repositories</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="contributions">1.2k</div>
                <div class="stat-label">Contributions</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="followers">327</div>
                <div class="stat-label">Followers</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">∞</div>
                <div class="stat-label">Bugs Fixed</div>
            </div>
        </div>
        
        <section class="skills">
            <h2 class="section-title">My Tech Stack</h2>
            <div class="skills-grid">
                <div class="skill-item">JavaScript/TypeScript</div>
                <div class="skill-item">Python</div>
                <div class="skill-item">Node.js</div>
                <div class="skill-item">React</div>
                <div class="skill-item">Vue.js</div>
                <div class="skill-item">PostgreSQL</div>
                <div class="skill-item">Docker</div>
                <div class="skill-item">AWS</div>
            </div>
        </section>
        
        <section class="projects">
            <h2 class="section-title">Featured Projects</h2>
            <div class="project-card">
                <h3 class="project-title">AsyncFlow</h3>
                <p class="project-desc">A powerful asynchronous workflow engine built with Node.js and TypeScript.</p>
                <div class="tech-stack">
                    <span class="tech-tag">TypeScript</span>
                    <span class="tech-tag">Node.js</span>
                    <span class="tech-tag">Redis</span>
                </div>
            </div>
            <div class="project-card">
                <h3 class="project-title">KittyHelper</h3>
                <p class="project-desc">AI-powered assistant for developers with cute kitten interface.</p>
                <div class="tech-stack">
                    <span class="tech-tag">Python</span>
                    <span class="tech-tag">FastAPI</span>
                    <span class="tech-tag">React</span>
                </div>
            </div>
            <div class="project-card">
                <h3 class="project-title">CoffeeScript</h3>
                <p class="project-desc">A programming language that compiles to JavaScript (not the existing one).</p>
                <div class="tech-stack">
                    <span class="tech-tag">Rust</span>
                    <span class="tech-tag">LLVM</span>
                    <span class="tech-tag">WASM</span>
                </div>
            </div>
        </section>
        
        <div class="social-links">
            <a href="https://github.com/await" class="social-link" aria-label="GitHub">
                <span>🐙</span>
            </a>
            <a href="#" class="social-link" aria-label="Twitter">
                <span>🐦</span>
            </a>
            <a href="#" class="social-link" aria-label="LinkedIn">
                <span>💼</span>
            </a>
            <a href="#" class="social-link" aria-label="Blog">
                <span>✍️</span>
            </a>
        </div>
    </div>

    <script>
        // Анимация счетчиков
        function animateValue(id, start, end, duration) {
            const obj = document.getElementById(id);
            let startTimestamp = null;
            const step = (timestamp) => {
                if (!startTimestamp) startTimestamp = timestamp;
                const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                const value = Math.floor(progress * (end - start) + start);
                obj.innerHTML = value.toLocaleString();
                if (progress < 1) {
                    window.requestAnimationFrame(step);
                }
            };
            window.requestAnimationFrame(step);
        }
        
        // Запуск анимации при загрузке страницы
        document.addEventListener('DOMContentLoaded', function() {
            animateValue('repos', 0, 42, 2000);
            animateValue('contributions', 0, 1200, 2500);
            animateValue('followers', 0, 327, 1800);
            
            // Случайное увеличение счетчика кофе
            setInterval(() => {
                const coffeeCount = document.getElementById('coffee-count');
                let count = parseInt(coffeeCount.innerText);
                coffeeCount.innerText = count + 1;
            }, 17000);
        });
        
        // Создание плавающих иконок
        function createFloatingIcons() {
            const icons = ['⚡', '🐱', '🚀', '💻', '✨', '🔧', '🎯', '🐞', '☕', '❤️'];
            const container = document.querySelector('.floating-icons');
            
            for (let i = 0; i < 15; i++) {
                const icon = document.createElement('div');
                icon.className = 'floating-icon';
                icon.innerText = icons[Math.floor(Math.random() * icons.length)];
                icon.style.left = `${Math.random() * 100}%`;
                icon.style.top = `${Math.random() * 100}%`;
                icon.style.animationDuration = `${15 + Math.random() * 20}s`;
                icon.style.animationDelay = `-${Math.random() * 20}s`;
                container.appendChild(icon);
            }
        }
        
        createFloatingIcons();
    </script>
</body>
</html>
