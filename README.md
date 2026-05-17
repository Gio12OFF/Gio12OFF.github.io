
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DoxBin style</title>
    <style>
        body {
            background-color: black;
            color: #00ff00;
            font-family: 'Courier New', monospace;
            padding: 20px;
            margin: 0;
        }
        pre {
            white-space: pre-wrap;
            word-wrap: break-word;
            font-size: 14px;
            line-height: 1.5;
        }
        a {
            color: #00ff00;
            text-decoration: none;
            border-bottom: 1px dotted #00ff00;
        }
        a:hover {
            color: #ffffff;
            background-color: #00ff00;
        }
        hr {
            border: none;
            border-top: 1px dashed #00ff00;
        }
        .post {
            margin-bottom: 40px;
            border-left: 2px solid #00ff00;
            padding-left: 15px;
        }
        .title {
            font-weight: bold;
            font-size: 18px;
            margin-bottom: 5px;
        }
        .date {
            color: #888888;
            font-size: 12px;
            margin-bottom: 15px;
        }
        textarea, input {
            background-color: #111111;
            color: #00ff00;
            border: 1px solid #00ff00;
            font-family: 'Courier New', monospace;
            padding: 8px;
            width: 100%;
            margin-bottom: 10px;
        }
        button {
            background-color: #00ff00;
            color: black;
            border: none;
            padding: 8px 16px;
            font-family: 'Courier New', monospace;
            font-weight: bold;
            cursor: pointer;
        }
        button:hover {
            background-color: #ffffff;
            color: black;
        }
    </style>
</head>
<body>
    <pre>
========================================
   D O X B I N   S T Y L E   P A G E
   только текст. никаких картинок.
========================================
    </pre>
    <hr>

    <div id="posts"></div>

    <hr>
    <div>
        <input type="text" id="titleInput" placeholder="Заголовок..."><br>
        <textarea id="contentInput" rows="6" placeholder="Текст поста..."></textarea><br>
        <button onclick="addPost()">Опубликовать</button>
    </div>

    <script>
        let posts = [];

        function renderPosts() {
            let container = document.getElementById('posts');
            container.innerHTML = '';
            for (let i = posts.length-1; i >= 0; i--) {
                let p = posts[i];
                let div = document.createElement('div');
                div.className = 'post';
                div.innerHTML = `
                    <div class="title">> ${escapeHtml(p.title)}</div>
                    <div class="date">[ ${p.date} ]</div>
                    <pre>${escapeHtml(p.content)}</pre>
                `;
                container.appendChild(div);
            }
        }

        function addPost() {
            let title = document.getElementById('titleInput').value.trim();
            let content = document.getElementById('contentInput').value.trim();
            if (!title || !content) return;
            let date = new Date().toLocaleString();
            posts.push({ title, content, date });
            renderPosts();
            document.getElementById('titleInput').value = '';
            document.getElementById('contentInput').value = '';
        }

        function escapeHtml(str) {
            return str.replace(/[&<>]/g, function(m) {
                if (m === '&') return '&amp;';
                if (m === '<') return '&lt;';
                if (m === '>') return '&gt;';
                return m;
            });
        }

        // пример поста для старта
        posts.push({
            title: 'Пример поста',
            content: 'Только текст. Зелёный на чёрном.\nСтроки, ссылки, логи.\nКак старый добрый doxbin.',
            date: new Date().toLocaleString()
        });
        renderPosts();
    </script>
</body>
</html>
