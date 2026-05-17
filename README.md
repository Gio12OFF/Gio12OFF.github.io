
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>neon matrix text</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: radial-gradient(circle at 20% 30%, #0a0f0a, #000000);
            min-height: 100vh;
            padding: 40px 20px;
            font-family: 'Courier New', 'Fira Code', monospace;
            color: #0f0;
            position: relative;
            overflow-x: hidden;
        }

        /* матричный дождь (только фоновая анимация) */
        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(0deg, 
                rgba(0, 255, 0, 0.03) 0px, 
                rgba(0, 255, 0, 0.03) 2px,
                transparent 2px,
                transparent 6px);
            pointer-events: none;
            z-index: 0;
            animation: scan 8s linear infinite;
        }

        @keyframes scan {
            0% { background-position: 0 0; }
            100% { background-position: 0 20px; }
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        /* анимированный заголовок с glitch */
        .glitch {
            font-size: 2.5rem;
            font-weight: bold;
            text-transform: uppercase;
            position: relative;
            text-shadow: 0.05em 0 0 rgba(255,0,0,0.75), -0.05em -0.025em 0 rgba(0,255,0,0.75);
            animation: glitch-shake 0.3s infinite alternate;
            margin-bottom: 30px;
            text-align: center;
            word-break: break-word;
        }

        @keyframes glitch-shake {
            0% { transform: translate(0); }
            20% { transform: translate(-1px, 1px); }
            40% { transform: translate(-1px, -1px); }
            60% { transform: translate(1px, 1px); }
            80% { transform: translate(1px, -1px); }
            100% { transform: translate(0); }
        }

        .glitch::before,
        .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: transparent;
        }

        .glitch::before {
            color: #0f0;
            z-index: -1;
            animation: glitch-offset 0.2s infinite linear alternate-reverse;
        }

        @keyframes glitch-offset {
            0% { left: -2px; top: 1px; opacity: 0.8; }
            100% { left: 2px; top: -1px; opacity: 0.4; }
        }

        /* анимированная линия */
        .ascii-line {
            text-align: center;
            font-size: 12px;
            letter-spacing: 2px;
            margin: 20px 0;
            animation: blink 1.5s step-end infinite;
            white-space: pre;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }

        /* посты с появлением */
        .post {
            border-left: 3px solid #0f0;
            margin: 30px 0;
            padding: 15px 20px;
            background: rgba(0, 20, 0, 0.5);
            backdrop-filter: blur(2px);
            box-shadow: 0 0 8px rgba(0, 255, 0, 0.2);
            transition: all 0.3s ease;
            animation: fadeSlideUp 0.6s ease-out;
            transform-origin: top;
        }

        @keyframes fadeSlideUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .post:hover {
            border-left-color: #ff00ff;
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.5);
            background: rgba(0, 30, 0, 0.7);
        }

        .title {
            font-size: 1.4rem;
            font-weight: bold;
            letter-spacing: -1px;
            margin-bottom: 8px;
            display: inline-block;
            background: linear-gradient(90deg, #0f0, #afa);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            text-shadow: 0 0 5px #0f0;
        }

        .date {
            font-size: 0.75rem;
            color: #6f6;
            margin-bottom: 12px;
            opacity: 0.7;
            border-bottom: 1px dashed #0f0;
            display: inline-block;
            padding-bottom: 2px;
        }

        .content {
            font-size: 0.95rem;
            line-height: 1.5;
            white-space: pre-wrap;
            word-wrap: break-word;
        }

        /* мигающий курсор в конце */
        .cursor {
            display: inline-block;
            width: 10px;
            height: 18px;
            background-color: #0f0;
            vertical-align: middle;
            margin-left: 5px;
            animation: cursorBlink 1s step-end infinite;
        }

        @keyframes cursorBlink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        hr {
            border: none;
            border-top: 1px dashed #0f0;
            margin: 30px 0;
            opacity: 0.5;
        }

        a {
            color: #0f0;
            text-decoration: none;
            border-bottom: 1px dotted #0f0;
            transition: 0.2s;
        }

        a:hover {
            color: #ff00ff;
            border-bottom-color: #ff00ff;
            text-shadow: 0 0 4px #ff00ff;
        }

        footer {
            text-align: center;
            margin-top: 40px;
            font-size: 0.8rem;
            opacity: 0.6;
        }
    </style>
</head>
<body>
<div class="container">
    <div class="glitch" data-text="> Бабкин Лев Ярославович ">> VOID_TEXT_DUMP</div>
    <div class="ascii-line">[ ~ ] [ SYSTEM://ACTIVE ] [ ~ ]</div>

    <div class="post">
        <div class="title">> Адрес проживания // True </div>
        <div class="date">[ 2026 17.05 20:49 ]</div>
        <div class="content">
            Кировская обл Киров ул Маяковского д25.
        </div>
    </div>

    <div class="post">
        <div class="title">> Номер телефона: // True</div>
        <div class="date">[ 2026-13-02 21:32 ]</div>
        <div class="content">
            79513474196.
        </div>
    </div>

    <div class="post">
        <div class="title">> Номер телефона Родителя(-ей): // голоса</div>
        <div class="date">[ 2026-17-05 20:50 ]</div>
        <div class="content">
            79536779004.
        </div>
    </div>

    <hr>

    <div class="post">
        <div class="title">> Телеграмм // надежда</div>
        <div class="date">[ 22.03.2026 ]</div>
        <div class="content">
            @vjH3oJ3v . 
        </div>
    </div>

    <footer>
        [ STATIC_MATRIX_MODE ] // нет форм // нет кнопок // только текст и анимация
    </footer>
</div>
</body>
</html>
