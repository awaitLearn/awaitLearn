
<head>
<link rel="stylesheet" href="styles.css">
</head>
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
