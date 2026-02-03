<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>088 - Чёрный фон с цветами</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #000;
            color: #fff;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }

        .background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at 20% 50%, rgba(40, 0, 60, 0.2) 0%, transparent 50%),
                        radial-gradient(circle at 80% 20%, rgba(80, 0, 0, 0.15) 0%, transparent 50%),
                        radial-gradient(circle at 40% 80%, rgba(0, 40, 80, 0.1) 0%, transparent 50%);
        }

        .flowers-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.7;
        }

        .flower {
            position: absolute;
            opacity: 0;
            animation: flowerAppear 8s infinite;
        }

        .flower:nth-child(1) {
            top: 10%;
            left: 15%;
            animation-delay: 0s;
            font-size: 24px;
            color: #6a0dad;
        }

        .flower:nth-child(2) {
            top: 20%;
            right: 10%;
            animation-delay: 1s;
            font-size: 32px;
            color: #8a2be2;
        }

        .flower:nth-child(3) {
            bottom: 15%;
            left: 20%;
            animation-delay: 2s;
            font-size: 28px;
            color: #9932cc;
        }

        .flower:nth-child(4) {
            bottom: 30%;
            right: 15%;
            animation-delay: 3s;
            font-size: 36px;
            color: #9400d3;
        }

        .flower:nth-child(5) {
            top: 40%;
            left: 10%;
            animation-delay: 4s;
            font-size: 20px;
            color: #ba55d3;
        }

        .flower:nth-child(6) {
            top: 60%;
            right: 20%;
            animation-delay: 5s;
            font-size: 40px;
            color: #da70d6;
        }

        @keyframes flowerAppear {
            0%, 100% {
                opacity: 0;
                transform: scale(0.5) rotate(0deg);
            }
            25% {
                opacity: 0.8;
                transform: scale(1) rotate(90deg);
            }
            50% {
                opacity: 0.8;
                transform: scale(1.1) rotate(180deg);
            }
            75% {
                opacity: 0.6;
                transform: scale(1) rotate(270deg);
            }
        }

        .main-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
            text-align: center;
        }

        .number-container {
            position: relative;
            margin-bottom: 80px;
        }

        .number-088 {
            font-size: 15vw;
            font-weight: 900;
            color: transparent;
            background: linear-gradient(45deg, #fff, #aaa, #fff, #aaa);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            background-clip: text;
            animation: numberGlow 4s ease-in-out infinite, pulse 3s infinite;
            text-shadow: 0 0 30px rgba(255, 255, 255, 0.7);
            letter-spacing: 5px;
        }

        @keyframes numberGlow {
            0%, 100% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
        }

        .links-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 40px;
            width: 100%;
            max-width: 600px;
            margin-top: 20px;
        }

        .discord-link {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            background: linear-gradient(45deg, #5865F2, #7289DA);
            color: white;
            padding: 18px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-size: 1.8rem;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 8px 20px rgba(88, 101, 242, 0.4);
            animation: discordFloat 3s ease-in-out infinite;
            width: 100%;
            max-width: 350px;
        }

        .discord-link:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 25px rgba(88, 101, 242, 0.6);
        }

        @keyframes discordFloat {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }

        .discord-icon {
            font-size: 2.2rem;
        }

        .creators-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            width: 100%;
            margin-top: 20px;
        }

        .creator-card {
            background: rgba(30, 30, 30, 0.8);
            border-radius: 15px;
            padding: 25px;
            width: 100%;
            max-width: 280px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            animation: cardAppear 1s ease-out;
        }

        .creator-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.7);
            border-color: rgba(255, 255, 255, 0.3);
        }

        @keyframes cardAppear {
            0% {
                opacity: 0;
                transform: translateY(30px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .creator-title {
            font-size: 1.4rem;
            margin-bottom: 15px;
            color: #b19cd9;
            font-weight: 600;
        }

        .creator-name {
            font-size: 1.6rem;
            font-weight: 700;
            margin-bottom: 20px;
            color: #fff;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
        }

        .discord-link-small {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            color: #7289DA;
            text-decoration: none;
            padding: 10px 15px;
            border-radius: 8px;
            background-color: rgba(114, 137, 218, 0.1);
            transition: all 0.3s ease;
            font-size: 1rem;
        }

        .discord-link-small:hover {
            background-color: rgba(114, 137, 218, 0.2);
            color: #8ea1e1;
        }

        .footer {
            margin-top: 60px;
            padding: 20px;
            color: rgba(255, 255, 255, 0.5);
            font-size: 0.9rem;
            text-align: center;
        }

        @media (max-width: 768px) {
            .number-088 {
                font-size: 20vw;
            }
            
            .discord-link {
                font-size: 1.5rem;
                padding: 15px 25px;
            }
            
            .creators-container {
                flex-direction: column;
                align-items: center;
            }
            
            .creator-card {
                max-width: 90%;
            }
        }

        .floating-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: floatParticle 15s infinite linear;
        }

        @keyframes floatParticle {
            0% {
                transform: translateY(100vh) translateX(0) rotate(0deg);
            }
            100% {
                transform: translateY(-100px) translateX(100px) rotate(360deg);
            }
        }
    </style>
</head>
<body>
    <div class="background"></div>
    
    <div class="flowers-container">
        <div class="flower">✿</div>
        <div class="flower">❀</div>
        <div class="flower">✾</div>
        <div class="flower">❁</div>
        <div class="flower">✽</div>
        <div class="flower">❃</div>
    </div>
    
    <div class="floating-particles" id="particles"></div>
    
    <div class="main-container">
        <div class="number-container">
            <div class="number-088">088</div>
        </div>
        
        <div class="links-container">
            <a href="https://discord.gg/kFPa2ZcZw5" target="_blank" class="discord-link">
                <i class="fab fa-discord discord-icon"></i>
                Discord сервер
            </a>
            
            <div class="creators-container">
                <div class="creator-card">
                    <div class="creator-title">Создатель</div>
                    <div class="creator-name">g1ooff</div>
                    <a href="https://discord.com/channels/@me/1363219380703461618" target="_blank" class="discord-link-small">
                        <i class="fab fa-discord"></i> Discord аккаунт
                    </a>
                </div>
                
                <div class="creator-card">
                    <div class="creator-title">Со-создатель</div>
                    <div class="creator-name">lolusaythat_38198</div>
                    <a href="https://discord.com/channels/@me/1202228863711858769" target="_blank" class="discord-link-small">
                        <i class="fab fa-discord"></i> Discord аккаунт
                    </a>
                </div>
            </div>
        </div>
        
        <div class="footer">
            Сайт с анимациями на чёрном фоне с цветами
        </div>
    </div>

    <script>
        // Создание плавающих частиц
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particlesCount = 50;
            
            for (let i = 0; i < particlesCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                // Случайные размеры
                const size = Math.random() * 10 + 2;
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                
                // Случайное положение
                particle.style.left = `${Math.random() * 100}vw`;
                
                // Случайная задержка анимации
                particle.style.animationDelay = `${Math.random() * 15}s`;
                
                // Случайная длительность анимации
                particle.style.animationDuration = `${Math.random() * 10 + 10}s`;
                
                // Случайный цвет
                const colors = [
                    'rgba(138, 43, 226, 0.3)',
                    'rgba(153, 50, 204, 0.3)',
                    'rgba(186, 85, 211, 0.3)',
                    'rgba(218, 112, 214, 0.3)'
                ];
                particle.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                
                particlesContainer.appendChild(particle);
            }
        }
        
        // Создание дополнительных цветочков
        function createExtraFlowers() {
            const flowersContainer = document.querySelector('.flowers-container');
            const flowerSymbols = ['❀', '✿', '❁', '✾', '✽', '❃', '🌸', '🌺', '🌼'];
            
            for (let i = 0; i < 12; i++) {
                const flower = document.createElement('div');
                flower.classList.add('flower');
                
                // Случайный символ цветка
                flower.textContent = flowerSymbols[Math.floor(Math.random() * flowerSymbols.length)];
                
                // Случайное положение
                flower.style.top = `${Math.random() * 100}%`;
                flower.style.left = `${Math.random() * 100}%`;
                
                // Случайный размер
                const size = Math.random() * 30 + 15;
                flower.style.fontSize = `${size}px`;
                
                // Случайный цвет
                const colors = ['#6a0dad', '#8a2be2', '#9932cc', '#9400d3', '#ba55d3', '#da70d6'];
                flower.style.color = colors[Math.floor(Math.random() * colors.length)];
                
                // Случайная задержка анимации
                flower.style.animationDelay = `${Math.random() * 8}s`;
                
                // Случайная длительность анимации
                flower.style.animationDuration = `${Math.random() * 5 + 6}s`;
                
                flowersContainer.appendChild(flower);
            }
        }
        
        // Инициализация после загрузки страницы
        document.addEventListener('DOMContentLoaded', function() {
            createParticles();
            createExtraFlowers();
            
            // Добавляем эффект мерцания для числа 088
            const numberElement = document.querySelector('.number-088');
            setInterval(() => {
                numberElement.style.textShadow = `0 0 ${20 + Math.random() * 30}px rgba(255, 255, 255, ${0.5 + Math.random() * 0.5})`;
            }, 1000);
        });
    </script>
</body>
</html>
