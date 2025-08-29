
[index.html](https://github.com/user-attachments/files/22040224/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GameDev Portfolio - Level Up Your Career</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Orbitron:wght@400;700;900&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            --primary-color: #00ff88;
            --secondary-color: #ff006e;
            --accent-color: #ffbe0b;
            --bg-dark: #0a0a0a;
            --bg-medium: #1a1a1a;
            --bg-light: #2a2a2a;
            --text-primary: #ffffff;
            --text-secondary: #a0a0a0;
        }
        
        body {
            font-family: 'Orbitron', monospace;
            background-color: var(--bg-dark);
            color: var(--text-primary);
            overflow-x: hidden;
            cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><rect x="8" y="8" width="16" height="16" fill="%2300ff88" opacity="0.8"/></svg>') 16 16, auto;
        }
        
        /* Pixelated background */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0, 255, 136, 0.03) 2px, rgba(0, 255, 136, 0.03) 4px),
                repeating-linear-gradient(90deg, transparent, transparent 2px, rgba(0, 255, 136, 0.03) 2px, rgba(0, 255, 136, 0.03) 4px);
            pointer-events: none;
            z-index: 1;
        }
        
        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(26, 26, 26, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            z-index: 1000;
            border-bottom: 2px solid var(--primary-color);
            box-shadow: 0 4px 20px rgba(0, 255, 136, 0.3);
        }
        
        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-family: 'Press Start 2P', cursive;
            font-size: 1rem;
            color: var(--primary-color);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
        
        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }
        
        .nav-links a {
            color: var(--text-secondary);
            text-decoration: none;
            font-size: 0.9rem;
            text-transform: uppercase;
            position: relative;
            transition: all 0.3s ease;
        }
        
        .nav-links a:hover {
            color: var(--primary-color);
            text-shadow: 0 0 10px var(--primary-color);
        }
        
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-color);
            transition: width 0.3s ease;
        }
        
        .nav-links a:hover::after {
            width: 100%;
        }
        
        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            background: radial-gradient(circle at center, rgba(0, 255, 136, 0.1) 0%, transparent 70%);
        }
        
        .hero-content {
            text-align: center;
            z-index: 2;
            animation: fadeInUp 1s ease-out;
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .game-title {
            font-family: 'Press Start 2P', cursive;
            font-size: 3rem;
            color: var(--primary-color);
            margin-bottom: 1rem;
            text-shadow: 
                0 0 20px var(--primary-color),
                0 0 40px var(--primary-color),
                0 0 60px var(--primary-color);
            animation: glitch 2s infinite;
        }
        
        @keyframes glitch {
            0%, 100% { text-shadow: 0 0 20px var(--primary-color); }
            20% { text-shadow: -2px 0 var(--secondary-color), 2px 0 var(--accent-color); }
            40% { text-shadow: 2px 0 var(--secondary-color), -2px 0 var(--accent-color); }
        }
        
        .subtitle {
            font-size: 1.5rem;
            color: var(--text-secondary);
            margin-bottom: 2rem;
        }
        
        .start-button {
            font-family: 'Press Start 2P', cursive;
            font-size: 1rem;
            padding: 1rem 2rem;
            background: linear-gradient(45deg, var(--primary-color), var(--accent-color));
            color: var(--bg-dark);
            border: none;
            cursor: pointer;
            text-transform: uppercase;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            box-shadow: 0 4px 20px rgba(0, 255, 136, 0.4);
        }
        
        .start-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 30px rgba(0, 255, 136, 0.6);
        }
        
        .start-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s ease;
        }
        
        .start-button:hover::before {
            left: 100%;
        }
        
        /* Floating elements */
        .floating-element {
            position: absolute;
            font-size: 2rem;
            color: var(--primary-color);
            opacity: 0.3;
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }
        
        .floating-element:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
        .floating-element:nth-child(2) { top: 60%; right: 10%; animation-delay: 2s; }
        .floating-element:nth-child(3) { bottom: 20%; left: 20%; animation-delay: 4s; }
        
        /* Character Profile Section */
        .character-profile {
            padding: 5rem 2rem;
            background: var(--bg-medium);
            position: relative;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .section-title {
            font-family: 'Press Start 2P', cursive;
            font-size: 2rem;
            text-align: center;
            color: var(--primary-color);
            margin-bottom: 3rem;
            text-shadow: 0 0 20px var(--primary-color);
        }
        
        .profile-container {
            display: grid;
            grid-template-columns: 300px 1fr;
            gap: 3rem;
            align-items: center;
        }
        
        .character-avatar {
            width: 300px;
            height: 300px;
            background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            border-radius: 20px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0, 255, 136, 0.3);
            animation: rotate 20s linear infinite;
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        .character-avatar::before {
            content: '🎮';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 8rem;
            animation: bounce 2s ease-in-out infinite;
        }
        
        @keyframes bounce {
            0%, 100% { transform: translate(-50%, -50%) scale(1); }
            50% { transform: translate(-50%, -50%) scale(1.1); }
        }
        
        .character-stats {
            background: var(--bg-light);
            padding: 2rem;
            border-radius: 15px;
            border: 2px solid var(--primary-color);
            box-shadow: 0 5px 20px rgba(0, 255, 136, 0.2);
        }
        
        .stat-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .stat-label {
            font-weight: 700;
            color: var(--text-secondary);
        }
        
        .stat-bar {
            width: 200px;
            height: 20px;
            background: var(--bg-dark);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }
        
        .stat-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
            border-radius: 10px;
            position: relative;
            overflow: hidden;
            animation: fillBar 2s ease-out;
        }
        
        @keyframes fillBar {
            from { width: 0; }
        }
        
        .stat-fill::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            animation: shimmer 2s infinite;
        }
        
        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        
        /* Skills Section */
        .skills-section {
            padding: 5rem 2rem;
            background: var(--bg-dark);
        }
        
        .power-ups-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }
        
        .power-up-card {
            background: var(--bg-medium);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            border: 2px solid transparent;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .power-up-card::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color), var(--accent-color));
            border-radius: 15px;
            opacity: 0;
            transition: opacity 0.3s ease;
            z-index: -1;
        }
        
        .power-up-card:hover::before {
            opacity: 1;
        }
        
        .power-up-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 255, 136, 0.3);
        }
        
        .power-up-icon {
            font-size: 3rem;
            color: var(--primary-color);
            margin-bottom: 1rem;
            animation: spin 3s linear infinite;
        }
        
        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        .power-up-name {
            font-weight: 700;
            margin-bottom: 0.5rem;
            color: var(--accent-color);
        }
        
        .power-up-level {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }
        
        /* Projects Section */
        .projects-section {
            padding: 5rem 2rem;
            background: var(--bg-medium);
        }
        
        .levels-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }
        
        .level-card {
            background: var(--bg-light);
            border-radius: 15px;
            overflow: hidden;
            border: 2px solid var(--primary-color);
            transition: all 0.3s ease;
            position: relative;
        }
        
        .level-card:hover {
            transform: scale(1.05);
            box-shadow: 0 15px 40px rgba(0, 255, 136, 0.4);
        }
        
        .level-preview {
            height: 200px;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            position: relative;
            overflow: hidden;
        }
        
        .level-preview::before {
            content: '🎯';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 4rem;
            animation: pulse 2s infinite;
        }
        
        .level-info {
            padding: 1.5rem;
        }
        
        .level-name {
            font-weight: 700;
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: var(--primary-color);
        }
        
        .level-description {
            color: var(--text-secondary);
            margin-bottom: 1rem;
            line-height: 1.6;
        }
        
        .level-stats {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .difficulty {
            display: flex;
            gap: 0.3rem;
        }
        
        .difficulty-star {
            color: var(--accent-color);
        }
        
        .play-button {
            background: var(--primary-color);
            color: var(--bg-dark);
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 5px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .play-button:hover {
            background: var(--accent-color);
            transform: scale(1.1);
        }
        
        /* Contact Section */
        .contact-section {
            padding: 5rem 2rem;
            background: var(--bg-dark);
            position: relative;
        }
        
        .leaderboard {
            max-width: 600px;
            margin: 0 auto;
            background: var(--bg-medium);
            border-radius: 15px;
            padding: 2rem;
            border: 2px solid var(--primary-color);
        }
        
        .leaderboard-title {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.5rem;
            text-align: center;
            color: var(--primary-color);
            margin-bottom: 2rem;
        }
        
        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }
        
        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }
        
        .form-label {
            color: var(--text-secondary);
            font-size: 0.9rem;
            text-transform: uppercase;
        }
        
        .form-input {
            background: var(--bg-light);
            border: 2px solid transparent;
            padding: 1rem;
            border-radius: 8px;
            color: var(--text-primary);
            font-family: 'Orbitron', monospace;
            transition: all 0.3s ease;
        }
        
        .form-input:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 10px rgba(0, 255, 136, 0.3);
        }
        
        .form-textarea {
            resize: vertical;
            min-height: 120px;
        }
        
        .submit-button {
            background: linear-gradient(45deg, var(--primary-color), var(--accent-color));
            color: var(--bg-dark);
            padding: 1rem 2rem;
            border: none;
            border-radius: 8px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
        }
        
        .submit-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(0, 255, 136, 0.4);
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 3rem;
        }
        
        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            background: var(--bg-light);
            border-radius: 50%;
            color: var(--primary-color);
            font-size: 1.5rem;
            text-decoration: none;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }
        
        .social-link:hover {
            border-color: var(--primary-color);
            transform: translateY(-5px) rotate(360deg);
            box-shadow: 0 5px 20px rgba(0, 255, 136, 0.3);
        }
        
        /* Footer */
        footer {
            background: var(--bg-medium);
            padding: 2rem;
            text-align: center;
            border-top: 2px solid var(--primary-color);
        }
        
        .footer-text {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .game-title {
                font-size: 2rem;
            }
            
            .profile-container {
                grid-template-columns: 1fr;
                text-align: center;
            }
            
            .character-avatar {
                margin: 0 auto;
            }
            
            .stat-bar {
                width: 150px;
            }
            
            .levels-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Loading Screen */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--bg-dark);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }
        
        .loading-text {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.5rem;
            color: var(--primary-color);
            margin-bottom: 2rem;
        }
        
        .loading-bar {
            width: 300px;
            height: 20px;
            background: var(--bg-medium);
            border-radius: 10px;
            overflow: hidden;
            border: 2px solid var(--primary-color);
        }
        
        .loading-progress {
            height: 100%;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
            width: 0;
            animation: loading 2s ease-out forwards;
        }
        
        @keyframes loading {
            to { width: 100%; }
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading-screen" id="loadingScreen">
        <div class="loading-text">LOADING GAME...</div>
        <div class="loading-bar">
            <div class="loading-progress"></div>
        </div>
    </div>

    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <a href="#" class="logo">
                <i class="fas fa-gamepad"></i>
                GAMEDEV PORTFOLIO
            </a>
            <ul class="nav-links">
                <li><a href="#home">HOME</a></li>
                <li><a href="#profile">PROFILE</a></li>
                <li><a href="#skills">SKILLS</a></li>
                <li><a href="#projects">PROJECTS</a></li>
                <li><a href="#contact">CONTACT</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="floating-element">⭐</div>
        <div class="floating-element">🎮</div>
        <div class="floating-element">🏆</div>
        
        <div class="hero-content">
            <h1 class="game-title">GAME DEVELOPER</h1>
            <p class="subtitle">Level Up Your Gaming Experience</p>
            <button class="start-button" onclick="scrollToSection('profile')">
                START GAME
            </button>
        </div>
    </section>

    <!-- Character Profile Section -->
    <section class="character-profile" id="profile">
        <div class="container">
            <h2 class="section-title">CHARACTER PROFILE</h2>
            <div class="profile-container">
                <div class="character-avatar"></div>
                <div class="character-stats">
                    <div class="stat-item">
                        <span class="stat-label">PLAYER NAME:</span>
                        <span style="color: var(--primary-color);">DEV_MASTER</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">LEVEL:</span>
                        <span style="color: var(--accent-color);">42</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">EXPERIENCE:</span>
                        <div class="stat-bar">
                            <div class="stat-fill" style="width: 85%;"></div>
                        </div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">CODING POWER:</span>
                        <div class="stat-bar">
                            <div class="stat-fill" style="width: 90%;"></div>
                        </div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">DESIGN SKILLS:</span>
                        <div class="stat-bar">
                            <div class="stat-fill" style="width: 75%;"></div>
                        </div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">TEAMWORK:</span>
                        <div class="stat-bar">
                            <div class="stat-fill" style="width: 95%;"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section class="skills-section" id="skills">
        <div class="container">
            <h2 class="section-title">POWER-UPS & ABILITIES</h2>
            <div class="power-ups-grid">
                <div class="power-up-card">
                    <div class="power-up-icon">🚀</div>
                    <h3 class="power-up-name">JavaScript</h3>
                    <p class="power-up-level">Level: Expert</p>
                </div>
                <div class="power-up-card">
                    <div class="power-up-icon">🎨</div>
                    <h3 class="power-up-name">CSS/HTML</h3>
                    <p class="power-up-level">Level: Master</p>
                </div>
                <div class="power-up-card">
                    <div class="power-up-icon">⚡</div>
                    <h3 class="power-up-name">React</h3>
                    <p class="power-up-level">Level: Advanced</p>
                </div>
                <div class="power-up-card">
                    <div class="power-up-icon">🔧</div>
                    <h3 class="power-up-name">Node.js</h3>
                    <p class="power-up-level">Level: Advanced</p>
                </div>
                <div class="power-up-card">
                    <div class="power-up-icon">🎯</div>
                    <h3 class="power-up-name">Game Design</h3>
                    <p class="power-up-level">Level: Expert</p>
                </div>
                <div class="power-up-card">
                    <div class="power-up-icon">🌟</div>
                    <h3 class="power-up-name">Unity</h3>
                    <p class="power-up-level">Level: Intermediate</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section class="projects-section" id="projects">
        <div class="container">
            <h2 class="section-title">GAME LEVELS & MISSIONS</h2>
            <div class="levels-grid">
                <div class="level-card">
                    <div class="level-preview"></div>
                    <div class="level-info">
                        <h3 class="level-name">Space Shooter</h3>
                        <p class="level-description">An epic space battle game with particle effects and power-ups</p>
                        <div class="level-stats">
                            <div class="difficulty">
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="far fa-star difficulty-star"></i>
                            </div>
                            <button class="play-button">PLAY</button>
                        </div>
                    </div>
                </div>
                <div class="level-card">
                    <div class="level-preview"></div>
                    <div class="level-info">
                        <h3 class="level-name">Puzzle Quest</h3>
                        <p class="level-description">A mind-bending puzzle adventure with 100+ levels</p>
                        <div class="level-stats">
                            <div class="difficulty">
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="far fa-star difficulty-star"></i>
                                <i class="far fa-star difficulty-star"></i>
                            </div>
                            <button class="play-button">PLAY</button>
                        </div>
                    </div>
                </div>
                <div class="level-card">
                    <div class="level-preview"></div>
                    <div class="level-info">
                        <h3 class="level-name">RPG Adventure</h3>
                        <p class="level-description">An open-world RPG with quests, battles, and exploration</p>
                        <div class="level-stats">
                            <div class="difficulty">
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                                <i class="fas fa-star difficulty-star"></i>
                            </div>
                            <button class="play-button">PLAY</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact-section" id="contact">
        <div class="container">
            <h2 class="section-title">HIGH SCORE LEADERBOARD</h2>
            <div class="leaderboard">
                <h3 class="leaderboard-title">SUBMIT YOUR SCORE</h3>
                <form class="contact-form" onsubmit="handleSubmit(event)">
                    <div class="form-group">
                        <label class="form-label">PLAYER NAME</label>
                        <input type="text" class="form-input" placeholder="Enter your name" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">EMAIL ADDRESS</label>
                        <input type="email" class="form-input" placeholder="your@email.com" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">MESSAGE</label>
                        <textarea class="form-input form-textarea" placeholder="Type your message here..." required></textarea>
                    </div>
                    <button type="submit" class="submit-button">SUBMIT SCORE</button>
                </form>
                
                <div class="social-links">
                    <a href="#" class="social-link"><i class="fab fa-github"></i></a>
                    <a href="#" class="social-link"><i class="fab fa-linkedin"></i></a>
                    <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                    <a href="#" class="social-link"><i class="fab fa-discord"></i></a>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p class="footer-text">© 2024 GAMEDEV PORTFOLIO | GAME OVER? TRY AGAIN!</p>
    </footer>

    <script>
        // Remove loading screen after page loads
        window.addEventListener('load', () => {
            setTimeout(() => {
                const loadingScreen = document.getElementById('loadingScreen');
                loadingScreen.style.opacity = '0';
                setTimeout(() => {
                    loadingScreen.style.display = 'none';
                }, 500);
            }, 2000);
        });

        // Smooth scrolling
        function scrollToSection(sectionId) {
            const section = document.getElementById(sectionId);
            section.scrollIntoView({ behavior: 'smooth' });
        }

        // Handle form submission
        function handleSubmit(event) {
            event.preventDefault();
            const form = event.target;
            const formData = new FormData(form);
            
            // Show success message
            const submitButton = form.querySelector('.submit-button');
            const originalText = submitButton.textContent;
            submitButton.textContent = 'SCORE SUBMITTED!';
            submitButton.style.background = 'var(--accent-color)';
            
            // Reset form
            form.reset();
            
            // Reset button after 3 seconds
            setTimeout(() => {
                submitButton.textContent = originalText;
                submitButton.style.background = '';
            }, 3000);
        }

        // Add parallax effect to floating elements
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const floatingElements = document.querySelectorAll('.floating-element');
            
            floatingElements.forEach((element, index) => {
                const speed = 0.5 + (index * 0.2);
                element.style.transform = `translateY(${scrolled * speed}px) rotate(${scrolled * 0.1}deg)`;
            });
        });

        // Add hover sound effect (visual feedback)
        document.querySelectorAll('a, button').forEach(element => {
            element.addEventListener('mouseenter', () => {
                element.style.transform = 'scale(1.05)';
            });
            
            element.addEventListener('mouseleave', () => {
                element.style.transform = 'scale(1)';
            });
        });

        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe all sections
        document.querySelectorAll('section').forEach(section => {
            section.style.opacity = '0';
            section.style.transform = 'translateY(50px)';
            section.style.transition = 'all 0.8s ease-out';
            observer.observe(section);
        });

        // Typing effect for game title
        const gameTitle = document.querySelector('.game-title');
        const originalText = gameTitle.textContent;
        gameTitle.textContent = '';
        let charIndex = 0;

        function typeWriter() {
            if (charIndex < originalText.length) {
                gameTitle.textContent += originalText.charAt(charIndex);
                charIndex++;
                setTimeout(typeWriter, 100);
            }
        }

        // Start typing effect after loading screen
        setTimeout(typeWriter, 2500);
    </script>
</body>
</html>
