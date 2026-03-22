<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gio's Documents</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #050505;
            color: #0f0;
            font-family: 'Courier New', 'Monaco', 'Fira Code', monospace;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        /* Анимированный шумный фон (эффект старого терминала) */
        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(0, 255, 0, 0.03) 0px,
                rgba(0, 255, 0, 0.03) 2px,
                transparent 2px,
                transparent 6px
            );
            pointer-events: none;
            z-index: 1;
        }

        .container {
            text-align: center;
            padding: 2rem;
            max-width: 800px;
            width: 90%;
            z-index: 2;
            border: 1px solid #0f0;
            border-radius: 8px;
            background-color: rgba(0, 0, 0, 0.85);
            box-shadow: 0 0 30px rgba(0, 255, 0, 0.2);
            backdrop-filter: blur(2px);
        }

        /* SVG маска Anonymous */
        .anonymous-symbol {
            width: 180px;
            height: auto;
            margin: 0 auto 1.5rem;
            filter: drop-shadow(0 0 8px #0f0);
            transition: transform 0.3s ease;
        }

        .anonymous-symbol:hover {
            transform: scale(1.02);
        }

        .anonymous-symbol svg {
            width: 100%;
            height: auto;
        }

        h1 {
            font-size: 2.8rem;
            letter-spacing: 4px;
            margin-bottom: 2rem;
            text-transform: uppercase;
            font-weight: normal;
            border-right: 3px solid #0f0;
            display: inline-block;
            white-space: nowrap;
            overflow: hidden;
            animation: blinkCursor 0.75s step-end infinite;
            padding-right: 8px;
        }

        @keyframes blinkCursor {
            0%, 100% { border-color: #0f0; }
            50% { border-color: transparent; }
        }

        .status {
            margin-bottom: 2rem;
            font-size: 0.9rem;
            color: #8bc34a;
            background: rgba(0, 20, 0, 0.6);
            display: inline-block;
            padding: 0.3rem 1rem;
            border-radius: 20px;
            border-left: 2px solid #0f0;
            border-right: 2px solid #0f0;
        }

        .login-panel {
            background: #0a0f0a;
            border: 1px solid #2a5a2a;
            border-radius: 12px;
            padding: 2rem;
            margin-top: 1rem;
            text-align: left;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.5);
        }

        .login-panel h2 {
            font-size: 1.4rem;
            margin-bottom: 1.5rem;
            text-align: center;
            color: #0f0;
            font-weight: normal;
            letter-spacing: 2px;
        }

        .input-group {
            margin-bottom: 1.2rem;
        }

        .input-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
            color: #8bc34a;
        }

        .input-group input {
            width: 100%;
            padding: 0.8rem;
            background: #000;
            border: 1px solid #2a5a2a;
            color: #0f0;
            font-family: monospace;
            font-size: 1rem;
            border-radius: 4px;
            outline: none;
            transition: all 0.2s;
        }

        .input-group input:focus {
            border-color: #0f0;
            box-shadow: 0 0 8px rgba(0, 255, 0, 0.3);
        }

        .btn {
            width: 100%;
            padding: 0.8rem;
            background: #0f0;
            color: #000;
            border: none;
            font-family: monospace;
            font-size: 1.1rem;
            font-weight: bold;
            letter-spacing: 1px;
            cursor: pointer;
            margin-top: 0.5rem;
            border-radius: 4px;
            transition: all 0.2s;
        }

        .btn:hover {
            background: #2ecc2e;
            box-shadow: 0 0 12px #0f0;
        }

        .info-message {
            margin-top: 1.2rem;
            font-size: 0.8rem;
            text-align: center;
            color: #6a6;
            border-top: 1px solid #1a3a1a;
            padding-top: 1rem;
        }

        .footer {
            margin-top: 2rem;
            font-size: 0.7rem;
            color: #2a5a2a;
        }

        /* Адаптивность */
        @media (max-width: 600px) {
            .container {
                width: 95%;
                padding: 1.5rem;
            }
            h1 {
                font-size: 1.8rem;
                white-space: normal;
                border-right: none;
                animation: none;
            }
            .anonymous-symbol {
                width: 120px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Символ Anonymous (SVG маска) -->
        <div class="anonymous-symbol">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M50 10 L70 25 L70 45 L65 55 L50 65 L35 55 L30 45 L30 25 L50 10Z" fill="none" stroke="#0f0" stroke-width="2.5"/>
                <circle cx="38" cy="38" r="3" fill="#0f0"/>
                <circle cx="62" cy="38" r="3" fill="#0f0"/>
                <path d="M44 48 L56 48" stroke="#0f0" stroke-width="2" stroke-linecap="round"/>
                <path d="M50 52 L50 62" stroke="#0f0" stroke-width="2"/>
                <path d="M30 70 L70 70" stroke="#0f0" stroke-width="2" stroke-dasharray="3 3"/>
                <text x="50" y="88" font-size="8" text-anchor="middle" fill="#0f0" font-family="monospace">ANONYMOUS</text>
            </svg>
        </div>

        <h1>Gio's Documents</h1>
        <div class="status">◆ SECURE TERMINAL ◆ AUTHORIZED ACCESS ONLY ◆</div>

        <!-- Панель входа (только для создателя) -->
        <div class="login-panel">
            <h2>> AUTHENTICATION REQUIRED_</h2>
            <form id="loginForm">
                <div class="input-group">
                    <label>USERNAME</label>
                    <input type="text" id="username" placeholder="creator" autocomplete="off">
                </div>
                <div class="input-group">
                    <label>ACCESS KEY</label>
                    <input type="password" id="password" placeholder="••••••••">
                </div>
                <button type="submit" class="btn">[ ENTER ]</button>
                <div class="info-message">
                    ⚡ Only creator has administrative privileges.<br>
                    All documents are encrypted and secured.
                </div>
            </form>
        </div>
        <div class="footer">
            Gio's Documents v1.0 | Black/Green Protocol | Anonymous Archive
        </div>
    </div>

    <script>
        // Простая демонстрация авторизации (для примера)
        // В реальном проекте данные должны проверяться на сервере
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            // Заглушка: логин и пароль для демонстрации
            // В реальной реализации это должно быть серверное API
            if (username === 'Gio' && password === 'Anonymous2024') {
                // Перенаправление на панель управления (админку)
                window.location.href = '/admin/dashboard.html';
                // В демо-версии показываем alert, т.к. страницы админки ещё нет
                alert('Авторизация успешна! Переход в панель управления.\n(В реальном проекте здесь будет страница управления документами)');
            } else {
                alert('ДОСТУП ЗАПРЕЩЁН\nНеверные учётные данные.');
                document.getElementById('username').value = '';
                document.getElementById('password').value = '';
                document.getElementById('username').focus();
            }
        });
    </script>
</body>
</html>
