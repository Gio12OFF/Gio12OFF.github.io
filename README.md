<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> BSE Team Present </title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #2d1b69, #6b46c1, #9f7aea);
            color: white;
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
            position: relative;
        }

        header {
            padding: 40px 0;
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
            background: linear-gradient(to right, #e9d8fd, #d6bcfa);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: titleGlow 3s ease-in-out infinite alternate;
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 40px;
        }

        .cube-container {
            width: 200px;
            height: 200px;
            position: absolute;
            top: 20px;
            left: 20px;
            z-index: 10;
        }

        .cube {
            width: 100%;
            height: 100%;
            position: relative;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0,0,0,0.5);
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            background: linear-gradient(45deg, #805ad5, #6b46c1);
        }

        .cube:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(159, 122, 234, 0.7);
        }

        .cube-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 10px;
        }

        .content {
            margin-top: 60px;
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
            background: linear-gradient(45deg, #7289da, #5b6eae);
            box-shadow: 0 4px 15px rgba(114, 137, 218, 0.4);
        }

        .btn-discord:hover {
            animation: pulse 1s infinite;
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(114, 137, 218, 0.6);
        }

        .btn-purple {
            background: linear-gradient(45deg, #805ad5, #6b46c1);
            box-shadow: 0 4px 15px rgba(128, 90, 213, 0.4);
        }

        .btn-purple:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(128, 90, 213, 0.6);
        }

        .btn-border {
            background: transparent;
            position: relative;
        }

        .btn-border::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, #9f7aea, #d6bcfa, #9f7aea, #d6bcfa);
            border-radius: 52px;
            z-index: -1;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .btn-border:hover::before {
            opacity: 1;
            animation: gradientMove 2s linear infinite;
            background-size: 400% 400%;
        }

        .floating-elements {
            position: absolute;
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

        .owner-info {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            margin: 30px auto;
            max-width: 500px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            text-align: left;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .owner-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .owner-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            margin-right: 15px;
            border: 2px solid #d6bcfa;
            box-shadow: 0 0 10px rgba(214, 188, 250, 0.5);
        }

        .owner-details {
            flex: 1;
        }

        .owner-name {
            font-size: 1.4rem;
            font-weight: bold;
            margin-bottom: 5px;
            background: linear-gradient(to right, #e9d8fd, #d6bcfa);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .owner-role {
            font-size: 1rem;
            opacity: 0.8;
        }

        .owner-description {
            margin-top: 15px;
            line-height: 1.5;
        }

        footer {
            margin-top: 60px;
            padding: 20px;
            opacity: 0.7;
        }

        @keyframes pulse {
            0% { transform: scale(1) translateY(-3px); }
            50% { transform: scale(1.05) translateY(-3px); }
            100% { transform: scale(1) translateY(-3px); }
        }

        @keyframes gradientMove {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
            100% { transform: translateY(0) rotate(360deg); }
        }

        @keyframes titleGlow {
            0% { text-shadow: 0 0 10px rgba(214, 188, 250, 0.5); }
            100% { text-shadow: 0 0 20px rgba(214, 188, 250, 0.8), 0 0 30px rgba(159, 122, 234, 0.6); }
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
            h1 {
                font-size: 2.2rem;
            }
            
            .cube-container {
                width: 150px;
                height: 150px;
                top: 10px;
                left: 10px;
            }
            
            .content {
                margin-top: 40px;
            }
            
            .owner-info {
                margin: 20px 10px;
                padding: 20px;
            }
            
            .owner-avatar {
                width: 50px;
                height: 50px;
            }
            
            .owner-name {
                font-size: 1.2rem;
            }
        }
    </style>
</head>
<body>
    <div class="floating-elements">
        <div class="floating-element"></div>
        <div class="floating-element"></div>
        <div class="floating-element"></div>
        <div class="floating-element"></div>
    </div>

    <div class="container">
        <div class="cube-container">
            <div class="cube">
                <img src="https://media.discordapp.net/attachments/1419673724000407674/1427289960335151144/f4d57eaf-234f-4015-b0c2-76ab7c10cf33c.jpg?ex=68ee52dc&is=68ed015c&hm=0512a812ad1879bfb2542d4a36fb87736f7f7d7276ceac059c7e1a512a429fb9&=&format=webp" alt="BSE Team" class="cube-image">
            </div>
        </div>

        <div class="content">
            <header class="fade-in">
                <h1>BSE Team Present</h1>
                <p class="subtitle">Добро пожаловать в наше сообщество</p>
            </header>

            <div class="buttons-container">
                <button class="btn btn-discord" onclick="joinDiscord()">Присоединиться к серверу</button>
                <button class="btn btn-purple" onclick="showInfo()">О нас</button>
                <button class="btn btn-border" onclick="showProjects()">Наши проекты</button>
            </div>

            <div id="ownerInfo" class="owner-info" style="display: none;">
                <div class="owner-header">
                    <img src="https://cdn.discordapp.com/attachments/1363219380703461618/1427296719468494929/ff20a57a8a3053b148ad6c76b4a6bb57.gif?ex=68ee5927&is=68ed07a7&hm=e4c13a27e5a4e40be2d7ccc0dec883304b2ebf06eb25420b2a3e93026376b995&" alt="g1oof Avatar" class="owner-avatar">
                    <div class="owner-details">
                        <div class="owner-name">g1oof</div>
                        <div class="owner-role">Владелец сервера & Разработчик сайта</div>
                    </div>
                </div>
                <div class="owner-description">
                    <p>Основатель сообщества BSE Team и создатель этого сайта. Активный разработчик с опытом в создании интерактивных веб-проектов и комьюнити-менеджменте.</p>
                </div>
            </div>

            <footer class="fade-in">
                <p>BSE Team Present | Site developer: g1oof</p>
            </footer>
        </div>
    </div>

    <script>
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

        // Функция для показа информации
        function showInfo() {
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

        // Функция для показа проектов
        function showProjects() {
            alert('Наши проекты скоро появятся здесь! Следите за обновлениями.');
            
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

        // Анимация появления элементов при загрузке
        document.addEventListener('DOMContentLoaded', function() {
            const elements = document.querySelectorAll('.fade-in');
            elements.forEach((element, index) => {
                element.style.animationDelay = `${index * 0.2}s`;
            });
        });
    </script>
</body>
</html>
