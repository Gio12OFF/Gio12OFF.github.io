
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BSE Team</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1e3a8a, #3b82f6, #60a5fa);
            color: white;
            min-height: 100vh;
            overflow: hidden;
        }

        /* Стили для начального экрана */
        #welcomeScreen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #1e40af, #2563eb, #3b82f6);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            transition: opacity 0.8s ease, transform 0.8s ease;
        }

        .welcome-content {
            text-align: center;
            padding: 40px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            max-width: 500px;
            animation: welcomeFadeIn 1.5s ease-out;
        }

        .welcome-title {
            font-size: 3.5rem;
            margin-bottom: 20px;
            background: linear-gradient(to right, #bfdbfe, #dbeafe);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 2px 10px rgba(0,0,0,0.2);
        }

        .welcome-subtitle {
            font-size: 1.3rem;
            margin-bottom: 40px;
            opacity: 0.9;
        }

        .welcome-btn {
            padding: 15px 40px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            background: linear-gradient(45deg, #2563eb, #3b82f6);
            color: white;
            box-shadow: 0 4px 15px rgba(37, 99, 235, 0.4);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .welcome-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(37, 99, 235, 0.6);
            animation: pulse 1.5s infinite;
        }

        /* Стили для основного сайта */
        #mainSite {
            display: none;
            opacity: 0;
            transition: opacity 0.8s ease;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }

        header {
            padding: 40px 0;
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
            background: linear-gradient(to right, #bfdbfe, #dbeafe);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 40px;
        }

        .cube-container {
            width: 200px;
            height: 200px;
            margin: 0 auto 40px;
        }

        .cube {
            width: 100%;
            height: 100%;
            border-radius: 15px;
            box-shadow: 0 0 25px rgba(0,0,0,0.4);
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            background: linear-gradient(45deg, #2563eb, #3b82f6);
        }

        .cube:hover {
            transform: scale(1.05);
            box-shadow: 0 0 35px rgba(37, 99, 235, 0.6);
        }

        .cube-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 15px;
        }

        .buttons-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 40px 0;
            flex-wrap: wrap;
        }

        .btn {
            padding: 15px 30px;
            font-size: 1.1rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
            min-width: 200px;
        }

        .btn-discord {
            background: linear-gradient(45deg, #2563eb, #3b82f6);
            box-shadow: 0 4px 15px rgba(37, 99, 235, 0.4);
        }

        .btn-discord:hover {
            animation: pulse 1s infinite;
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(37, 99, 235, 0.6);
        }

        .btn-about {
            background: linear-gradient(45deg, #1d4ed8, #2563eb);
            box-shadow: 0 4px 15px rgba(29, 78, 216, 0.4);
        }

        .btn-about:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(29, 78, 216, 0.6);
        }

        .owner-info {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            margin: 30px auto;
            max-width: 600px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            text-align: left;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            display: none;
        }

        .owner-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .owner-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            margin-right: 20px;
            border: 3px solid #bfdbfe;
            box-shadow: 0 0 15px rgba(191, 219, 254, 0.5);
        }

        .owner-details {
            flex: 1;
        }

        .owner-name {
            font-size: 1.6rem;
            font-weight: bold;
            margin-bottom: 5px;
            background: linear-gradient(to right, #bfdbfe, #dbeafe);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .owner-role {
            font-size: 1.1rem;
            opacity: 0.9;
            margin-bottom: 8px;
        }

        .owner-description {
            margin-top: 15px;
            line-height: 1.5;
        }

        .floating-elements {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            overflow: hidden;
            z-index: -1;
        }

        .floating-element {
            position: absolute;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: float 15s infinite linear;
        }

        .floating-element:nth-child(1) {
            width: 80px;
            height: 80px;
            top: 10%;
            left: 10%;
            animation-duration: 20s;
        }

        .floating-element:nth-child(2) {
            width: 120px;
            height: 120px;
            top: 60%;
            left: 80%;
            animation-duration: 25s;
        }

        .floating-element:nth-child(3) {
            width: 60px;
            height: 60px;
            top: 80%;
            left: 20%;
            animation-duration: 15s;
        }

        .floating-element:nth-child(4) {
            width: 100px;
            height: 100px;
            top: 30%;
            left: 70%;
            animation-duration: 30s;
        }

        footer {
            margin-top: 60px;
            padding: 20px;
            opacity: 0.7;
        }

        /* Анимации */
        @keyframes welcomeFadeIn {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0% { transform: scale(1) translateY(-3px); }
            50% { transform: scale(1.05) translateY(-3px); }
            100% { transform: scale(1) translateY(-3px); }
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
            100% { transform: translateY(0) rotate(360deg); }
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

        .fade-in {
            animation: fadeInUp 0.6s ease-out;
        }

        @media (max-width: 768px) {
            .welcome-title {
                font-size: 2.5rem;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .cube-container {
                width: 150px;
                height: 150px;
            }
            
            .owner-avatar {
                width: 60px;
                height: 60px;
            }
            
            .owner-name {
                font-size: 1.3rem;
            }
            
            .buttons-container {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 100%;
                max-width: 300px;
            }
        }
    </style>
</head>
<body>
    <!-- Начальный экран -->
    <div id="welcomeScreen">
        <div class="welcome-content">
            <h1 class="welcome-title">Welcome to BSE Team</h1>
            <p class="welcome-subtitle">Присоединяйтесь к нашему сообществу</p>
            <button class="welcome-btn" onclick="showMainSite()">About Us</button>
        </div>
    </div>

    <!-- Основной сайт -->
    <div id="mainSite">
        <div class="floating-elements">
            <div class="floating-element"></div>
            <div class="floating-element"></div>
            <div class="floating-element"></div>
            <div class="floating-element"></div>
        </div>

        <div class="container">
            <header class="fade-in">
                <h1>BSE Team</h1>
                <p class="subtitle">Сообщество разработчиков и энтузиастов</p>
            </header>

            <div class="cube-container fade-in">
                <div class="cube">
                    <img src="https://media.discordapp.net/attachments/1419673724000407674/1427289960335151144/f4d57eaf-234f-4015-b0c2-76ab7c10cf33c.jpg?ex=68ee52dc&is=68ed015c&hm=0512a812ad1879bfb2542d4a36fb87736f7f7d7276ceac059c7e1a512a429fb9&=&format=webp" alt="BSE Team" class="cube-image">
                </div>
            </div>

            <div class="buttons-container">
                <button class="btn btn-discord" onclick="joinDiscord()">Присоединиться к серверу</button>
                <button class="btn btn-about" onclick="showOwnerInfo()">Информация о создателе</button>
            </div>

            <div id="ownerInfo" class="owner-info fade-in">
                <div class="owner-header">
                    <img src="https://cdn.discordapp.com/attachments/1363219380703461618/1427296719468494929/ff20a57a8a3053b148ad6c76b4a6bb57.gif?ex=68ee5927&is=68ed07a7&hm=e4c13a27e5a4e40be2d7ccc0dec883304b2ebf06eb25420b2a3e93026376b995&" alt="g1oof Avatar" class="owner-avatar">
                    <div class="owner-details">
                        <div class="owner-name">g1oof</div>
                        <div class="owner-role">Владелец сервера & Разработчик сайта</div>
                        <div class="owner-role">Основатель BSE Team</div>
                    </div>
                </div>
                <div class="owner-description">
                    <p>Создатель и вдохновитель сообщества BSE Team. Активный разработчик с многолетним опытом в создании интерактивных веб-проектов, игровых модов и комьюнити-менеджменте. Всегда открыт к новым идеям и сотрудничеству!</p>
                </div>
            </div>

            <footer class="fade-in">
                <p>BSE Team | Site developer: g1oof</p>
            </footer>
        </div>
    </div>

    <script>
        // Функция для показа основного сайта
        function showMainSite() {
            const welcomeScreen = document.getElementById('welcomeScreen');
            const mainSite = document.getElementById('mainSite');
            
            // Анимация исчезновения начального экрана
            welcomeScreen.style.opacity = '0';
            welcomeScreen.style.transform = 'scale(1.1)';
            
            setTimeout(() => {
                welcomeScreen.style.display = 'none';
                mainSite.style.display = 'block';
                
                // Анимация появления основного сайта
                setTimeout(() => {
                    mainSite.style.opacity = '1';
                    
                    // Анимация появления элементов
                    const elements = document.querySelectorAll('.fade-in');
                    elements.forEach((element, index) => {
                        element.style.animationDelay = `${index * 0.2}s`;
                    });
                }, 50);
            }, 800);
        }

        // Функция для присоединения к Discord
        function joinDiscord() {
            window.open('https://discord.gg/hGh7FYteYw', '_blank');
            
            // Анимация кнопки
            const button = event.target;
            button.style.transform = 'scale(0.95)';
            setTimeout(() => {
                button.style.transform = '';
            }, 150);
            
            createRipple(button);
        }

        // Функция для показа информации о создателе
        function showOwnerInfo() {
            const ownerInfo = document.getElementById('ownerInfo');
            
            if (ownerInfo.style.display === 'none' || ownerInfo.style.display === '') {
                ownerInfo.style.display = 'block';
                ownerInfo.classList.add('fade-in');
            } else {
                ownerInfo.style.display = 'none';
            }
            
            // Анимация кнопки
            const button = event.target;
            button.style.transform = 'scale(0.95)';
            setTimeout(() => {
                button.style.transform = '';
            }, 150);
            
            createRipple(button);
        }

        // Функция для создания ripple-эффекта
        function createRipple(button) {
            const ripple = document.createElement('span');
            const rect = button.getBoundingClientRect();
            const size = Math.max(rect.width, rect.height);
            const x = event.clientX - rect.left - size / 2;
            const y = event.clientY - rect.top - size / 2;
            
            ripple.style.width = ripple.style.height = size + 'px';
            ripple.style.left = x + 'px';
            ripple.style.top = y + 'px';
            ripple.classList.add('ripple');
            
            // Стили для ripple-эффекта
            ripple.style.position = 'absolute';
            ripple.style.borderRadius = '50%';
            ripple.style.backgroundColor = 'rgba(255, 255, 255, 0.5)';
            ripple.style.transform = 'scale(0)';
            ripple.style.animation = 'ripple-animation 0.6s linear';
            ripple.style.pointerEvents = 'none';
            
            button.style.position = 'relative';
            button.style.overflow = 'hidden';
            button.appendChild(ripple);
            
            // Удаляем ripple после анимации
            setTimeout(() => {
                ripple.remove();
            }, 600);
        }

        // Добавляем стили для ripple-анимации
        const style = document.createElement('style');
        style.textContent = `
            @keyframes ripple-animation {
                from {
                    transform: scale(0);
                    opacity: 1;
                }
                to {
                    transform: scale(4);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
