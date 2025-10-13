
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Синий сайт с анимациями</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a2a6c, #2d4ba9);
            color: white;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }

        header {
            padding: 40px 0;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 40px;
        }

        .buttons-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }

        /* Базовые стили для кнопок */
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
        }

        /* Анимированная кнопка с пульсацией */
        .btn-pulse {
            background: linear-gradient(45deg, #2563eb, #3b82f6);
            box-shadow: 0 4px 15px rgba(37, 99, 235, 0.4);
        }

        .btn-pulse:hover {
            animation: pulse 1s infinite;
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(37, 99, 235, 0.6);
        }

        /* Кнопка с заполнением */
        .btn-fill {
            background: transparent;
            border: 2px solid #60a5fa;
            position: relative;
            z-index: 1;
        }

        .btn-fill::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: #60a5fa;
            transition: left 0.4s ease;
            z-index: -1;
        }

        .btn-fill:hover::before {
            left: 0;
        }

        /* Кнопка с поднятием */
        .btn-lift {
            background: linear-gradient(45deg, #1e40af, #3730a3);
            box-shadow: 0 6px 0 #1e3a8a, 0 8px 10px rgba(0,0,0,0.3);
            transition: all 0.1s ease;
        }

        .btn-lift:active {
            transform: translateY(6px);
            box-shadow: 0 0 0 #1e3a8a, 0 0 15px rgba(0,0,0,0.2);
        }

        /* Кнопка с градиентной обводкой */
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
            background: linear-gradient(45deg, #3b82f6, #60a5fa, #93c5fd, #60a5fa, #3b82f6);
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

        /* Анимированный блок */
        .animated-box {
            width: 200px;
            height: 200px;
            background: linear-gradient(45deg, #3b82f6, #60a5fa);
            margin: 40px auto;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            animation: float 3s ease-in-out infinite;
        }

        /* Ключевые кадры для анимаций */
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
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
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

        /* Анимация появления элементов */
        .fade-in {
            animation: fadeInUp 0.6s ease-out;
        }

        footer {
            margin-top: 60px;
            padding: 20px;
            opacity: 0.7;
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="fade-in">
            <h1>Добро пожаловать в синий мир</h1>
            <p class="subtitle">Исследуйте магию анимаций и интерактивности</p>
        </header>

        <section class="buttons-grid">
            <button class="btn btn-pulse" onclick="animateButton(this)">Пульсирующая кнопка</button>
            <button class="btn btn-fill" onclick="animateButton(this)">Заполняющаяся кнопка</button>
            <button class="btn btn-lift" onclick="animateButton(this)">Поднимающаяся кнопка</button>
            <button class="btn btn-border" onclick="animateButton(this)">Градиентная кнопка</button>
        </section>

        <div class="animated-box" id="animatedBox"></div>

        <footer class="fade-in">
            <p>Сайт создан с использованием HTML, CSS и JavaScript</p>
        </footer>
    </div>

    <script>
        // Функция для анимации кнопок при клике
        function animateButton(button) {
            // Добавляем класс для анимации
            button.style.transform = 'scale(0.95)';
            
            // Убираем трансформацию через 150ms
            setTimeout(() => {
                button.style.transform = '';
            }, 150);
            
            // Создаем эффект пузырька
            createRipple(button);
            
            // Меняем цвет анимированного блока случайным образом
            changeBoxColor();
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

        // Функция для изменения цвета анимированного блока
        function changeBoxColor() {
            const box = document.getElementById('animatedBox');
            const blueShades = [
                'linear-gradient(45deg, #3b82f6, #60a5fa)',
                'linear-gradient(45deg, #2563eb, #3b82f6)',
                'linear-gradient(45deg, #1d4ed8, #2563eb)',
                'linear-gradient(45deg, #1e40af, #1d4ed8)',
                'linear-gradient(45deg, #3730a3, #1e40af)'
            ];
            
            // Выбираем случайный градиент
            const randomGradient = blueShades[Math.floor(Math.random() * blueShades.length)];
            box.style.background = randomGradient;
            
            // Добавляем небольшую анимацию изменения
            box.style.transform = 'scale(1.1)';
            setTimeout(() => {
                box.style.transform = '';
            }, 300);
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
