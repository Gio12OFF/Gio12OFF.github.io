<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gio's Documents | Anonymous Archive</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #030303;
            color: #0f0;
            font-family: 'Courier New', 'Monaco', 'Fira Code', monospace;
            min-height: 100vh;
        }

        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(0, 255, 0, 0.02) 0px,
                rgba(0, 255, 0, 0.02) 2px,
                transparent 2px,
                transparent 6px
            );
            pointer-events: none;
            z-index: 1;
        }

        .wrapper {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1.5rem;
            position: relative;
            z-index: 2;
        }

        .header {
            text-align: center;
            padding: 2rem 1rem;
            border-bottom: 2px solid #0f0;
            margin-bottom: 2rem;
        }

        .anonymous-symbol {
            width: 100px;
            margin: 0 auto 1rem;
        }

        .anonymous-symbol svg {
            width: 100%;
            filter: drop-shadow(0 0 5px #0f0);
        }

        h1 {
            font-size: 2.2rem;
            letter-spacing: 4px;
            margin-bottom: 0.5rem;
        }

        .sub {
            color: #4a9e4a;
            font-size: 0.8rem;
            margin-top: 0.5rem;
        }

        .status-badge {
            display: inline-block;
            background: rgba(0, 30, 0, 0.7);
            border-left: 3px solid #0f0;
            border-right: 3px solid #0f0;
            padding: 0.3rem 1.2rem;
            font-size: 0.7rem;
            margin-top: 1rem;
        }

        .admin-panel {
            background: #0a100a;
            border: 1px solid #2a5a2a;
            border-radius: 8px;
            padding: 1.5rem;
            margin-bottom: 2rem;
            display: none;
        }

        .admin-panel.active {
            display: block;
        }

        .admin-panel h3 {
            margin-bottom: 1rem;
            color: #0f0;
            border-left: 3px solid #0f0;
            padding-left: 0.8rem;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-size: 0.85rem;
            color: #8bc34a;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.7rem;
            background: #000;
            border: 1px solid #2a5a2a;
            color: #0f0;
            font-family: monospace;
            border-radius: 4px;
        }

        .form-group textarea {
            min-height: 100px;
            resize: vertical;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #0f0;
            box-shadow: 0 0 5px rgba(0, 255, 0, 0.3);
        }

        .btn {
            background: #0f0;
            color: #000;
            border: none;
            padding: 0.7rem 1.5rem;
            font-family: monospace;
            font-weight: bold;
            cursor: pointer;
            border-radius: 4px;
            font-size: 0.9rem;
        }

        .btn:hover {
            background: #2ecc2e;
            box-shadow: 0 0 8px #0f0;
        }

        .btn-danger {
            background: #3a1a1a;
            color: #f66;
            border: 1px solid #a00;
        }

        .btn-danger:hover {
            background: #5a2a2a;
        }

        .documents-section {
            margin-top: 2rem;
        }

        .documents-header {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            flex-wrap: wrap;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid #2a5a2a;
            padding-bottom: 0.5rem;
        }

        .doc-count {
            font-size: 0.8rem;
            color: #4a9e4a;
        }

        .doc-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
            gap: 1.5rem;
        }

        .doc-card {
            background: #0a0f0a;
            border: 1px solid #2a5a2a;
            border-radius: 8px;
            padding: 1.2rem;
            transition: all 0.2s;
        }

        .doc-card:hover {
            border-color: #0f0;
            box-shadow: 0 0 12px rgba(0, 255, 0, 0.1);
        }

        .doc-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 0.8rem;
            color: #0f0;
            word-break: break-word;
            border-left: 2px solid #0f0;
            padding-left: 0.6rem;
        }

        .doc-date {
            font-size: 0.7rem;
            color: #5a8a5a;
            margin-bottom: 0.8rem;
        }

        .doc-content {
            font-size: 0.85rem;
            line-height: 1.5;
            white-space: pre-wrap;
            word-break: break-word;
            margin-bottom: 1rem;
            font-family: monospace;
        }

        .doc-images {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-top: 0.8rem;
        }

        .doc-images img {
            max-width: 100%;
            max-height: 150px;
            border-radius: 4px;
            border: 1px solid #2a5a2a;
            cursor: pointer;
            object-fit: cover;
        }

        .delete-doc {
            background: none;
            border: 1px solid #5a2a2a;
            color: #f66;
            padding: 0.3rem 0.8rem;
            font-size: 0.7rem;
            cursor: pointer;
            margin-top: 0.5rem;
            border-radius: 3px;
        }

        .delete-doc:hover {
            background: #2a1a1a;
        }

        .login-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #0a0f0a;
            border: 1px solid #0f0;
            padding: 0.5rem 1rem;
            cursor: pointer;
            font-family: monospace;
            font-size: 0.8rem;
            z-index: 100;
        }

        .login-btn:hover {
            background: #1a2a1a;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.95);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: #0a100a;
            border: 2px solid #0f0;
            padding: 2rem;
            max-width: 400px;
            width: 90%;
            border-radius: 8px;
        }

        .close-modal {
            float: right;
            cursor: pointer;
            font-size: 1.5rem;
            color: #0f0;
        }

        .footer {
            text-align: center;
            margin-top: 3rem;
            padding: 1.5rem;
            border-top: 1px solid #1a3a1a;
            font-size: 0.7rem;
            color: #2a5a5a;
        }

        @media (max-width: 700px) {
            .wrapper {
                padding: 1rem;
            }
            h1 {
                font-size: 1.5rem;
            }
            .doc-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>

<div class="wrapper">
    <div class="header">
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
        <h1>GIO'S DOCUMENTS</h1>
        <div class="sub">◆ encrypted archive ◆ read-only for public ◆</div>
        <div class="status-badge">⚡ OPEN DATABASE ⚡</div>
    </div>

    <div id="adminPanel" class="admin-panel">
        <h3>> ADMIN: CREATE NEW DOCUMENT</h3>
        <form id="createDocForm">
            <div class="form-group">
                <label>TITLE / ЗАГОЛОВОК</label>
                <input type="text" id="docTitle" required placeholder="Document title...">
            </div>
            <div class="form-group">
                <label>CONTENT / СОДЕРЖАНИЕ</label>
                <textarea id="docContent" placeholder="Your text here..."></textarea>
            </div>
            <div class="form-group">
                <label>IMAGES (URLs, one per line)</label>
                <textarea id="docImages" placeholder="https://example.com/image1.jpg&#10;https://example.com/image2.png" rows="3"></textarea>
                <small style="color:#5a8a5a;">Paste direct image links, one per line</small>
            </div>
            <button type="submit" class="btn">+ PUBLISH DOCUMENT</button>
            <button type="button" id="logoutBtn" class="btn btn-danger" style="margin-left: 0.5rem;">EXIT ADMIN</button>
        </form>
    </div>

    <div class="documents-section">
        <div class="documents-header">
            <h3>> DOCUMENTS_</h3>
            <span class="doc-count" id="docCount">0 documents</span>
        </div>
        <div id="docGrid" class="doc-grid"></div>
    </div>

    <div class="footer">
        Gio's Documents | Anonymous Archive v2.0 | All data stored locally in your browser
    </div>
</div>

<button id="showLoginBtn" class="login-btn">[ ADMIN LOGIN ]</button>

<div id="loginModal" class="modal">
    <div class="modal-content">
        <span id="closeModal" class="close-modal">&times;</span>
        <h3 style="margin-bottom:1rem;">>> AUTHORIZATION</h3>
        <form id="adminLoginForm">
            <div class="form-group">
                <label>USERNAME</label>
                <input type="text" id="adminUser" placeholder="creator">
            </div>
            <div class="form-group">
                <label>PASSWORD</label>
                <input type="password" id="adminPass" placeholder="••••••••">
            </div>
            <button type="submit" class="btn">UNLOCK ADMIN</button>
        </form>
        <p style="margin-top:1rem; font-size:0.7rem; color:#5a8a5a;">Only Gio can publish documents.</p>
    </div>
</div>

<script>
    const STORAGE_KEY = 'gios_documents';
    const ADMIN_USER = 'Gio';
    const ADMIN_PASS = 'Anon2024Docs';

    let documents = [];
    let isAdmin = false;

    // Демонстрационный документ (все данные вымышленные)
    const demoDocument = {
        id: 1742688000000,
        title: "PERSONNEL FILE #A-7742 [CLASSIFIED]",
        content: "=== CONFIDENTIAL ===\n\nФИО: Бабкин Лев Ярославович\nДата рождения: 11.07.201x\nАдрес:Страна: Россия, Г.Киров, Мкр.Нововятск\nТелефон: +79513474196\nТелефон (Родителя.): +79536779004\nTelegram: @vjH3oJ3v\n\n=== РОДИТЕЛИ ===\nОтец: Алексей Бабкин\nМать:Елена Бабкина\n\n=== ПРИМЕЧАНИЕ ===\nДанный документ создан Gio.\n Фото(-ки)\nhttps://ibb.co/Jj5zV6Q4 , https://ibb.co/1Y3pXCqM , https://ibb.co/TMPYDHxB , https://ibb.co/4nkxJy4n \n Made by GIO\n",
        images: [
            "https://ibb.co/4nkxJy4n",
            "https://ibb.co/TMPYDHxB",
            "https://ibb.co/1Y3pXCqM",
            "https://ibb.co/Jj5zV6Q4"
        ],
        date: new Date().toISOString()
    };

    function loadDocuments() {
        const stored = localStorage.getItem(STORAGE_KEY);
        if (stored) {
            documents = JSON.parse(stored);
        } else {
            documents = [demoDocument];
            saveDocuments();
        }
        renderDocuments();
    }

    function saveDocuments() {
        localStorage.setItem(STORAGE_KEY, JSON.stringify(documents));
    }

    function renderDocuments() {
        const grid = document.getElementById('docGrid');
        const countSpan = document.getElementById('docCount');
        
        if (!documents.length) {
            grid.innerHTML = '<div style="text-align:center; padding:2rem; color:#2a5a2a;">[ NO DOCUMENTS YET ]</div>';
            countSpan.innerText = '0 documents';
            return;
        }

        countSpan.innerText = documents.length + ' document' + (documents.length !== 1 ? 's' : '');
        
        grid.innerHTML = documents.map(doc => {
            let imagesHtml = '';
            if (doc.images && doc.images.length) {
                imagesHtml = `<div class="doc-images">${doc.images.map(img => 
                    `<img src="${escapeHtml(img)}" alt="image" onerror="this.src='https://via.placeholder.com/300x200/0a0f0a/4a9e4a?text=Image+Not+Found'" onclick="window.open('${escapeHtml(img)}', '_blank')">`
                ).join('')}</div>`;
            }
            
            const deleteBtn = isAdmin ? 
                `<button class="delete-doc" onclick="deleteDocument('${doc.id}')">[ DELETE DOCUMENT ]</button>` : '';
            
            return `
                <div class="doc-card">
                    <div class="doc-title">> ${escapeHtml(doc.title)}</div>
                    <div class="doc-date">${new Date(doc.date).toLocaleString()}</div>
                    <div class="doc-content">${escapeHtml(doc.content).replace(/\n/g, '<br>')}</div>
                    ${imagesHtml}
                    ${deleteBtn}
                </div>
            `;
        }).join('');
    }

    function escapeHtml(str) {
        if (!str) return '';
        return str.replace(/[&<>]/g, function(m) {
            if (m === '&') return '&amp;';
            if (m === '<') return '&lt;';
            if (m === '>') return '&gt;';
            return m;
        });
    }

    function createDocument(title, content, imagesArray) {
        const newDoc = {
            id: Date.now(),
            title: title.trim(),
            content: content.trim(),
            images: imagesArray.filter(url => url.trim() !== ''),
            date: new Date().toISOString()
        };
        documents.unshift(newDoc);
        saveDocuments();
        renderDocuments();
    }

    function deleteDocument(id) {
        if (!isAdmin) return;
        if (confirm('Delete this document permanently?')) {
            documents = documents.filter(doc => doc.id != id);
            saveDocuments();
            renderDocuments();
        }
    }

    function showAdminPanel(show) {
        const panel = document.getElementById('adminPanel');
        if (show && isAdmin) {
            panel.classList.add('active');
        } else {
            panel.classList.remove('active');
        }
    }

    function updateAdminUI() {
        showAdminPanel(isAdmin);
        const loginBtn = document.getElementById('showLoginBtn');
        if (isAdmin) {
            loginBtn.style.opacity = '0.7';
            loginBtn.innerText = '[ ADMIN MODE ]';
        } else {
            loginBtn.style.opacity = '1';
            loginBtn.innerText = '[ ADMIN LOGIN ]';
        }
        renderDocuments();
    }

    function adminLogin(username, password) {
        if (username === ADMIN_USER && password === ADMIN_PASS) {
            isAdmin = true;
            localStorage.setItem('gios_admin_session', 'true');
            document.getElementById('loginModal').classList.remove('active');
            updateAdminUI();
            return true;
        } else {
            alert('ACCESS DENIED\nInvalid credentials.');
            return false;
        }
    }

    function adminLogout() {
        isAdmin = false;
        localStorage.removeItem('gios_admin_session');
        updateAdminUI();
    }

    function checkSession() {
        const session = localStorage.getItem('gios_admin_session');
        if (session === 'true') {
            isAdmin = true;
            updateAdminUI();
        }
    }

    document.getElementById('createDocForm').addEventListener('submit', function(e) {
        e.preventDefault();
        if (!isAdmin) {
            alert('Unauthorized. Please login as admin.');
            return;
        }
        
        const title = document.getElementById('docTitle').value;
        const content = document.getElementById('docContent').value;
        const imagesRaw = document.getElementById('docImages').value;
        
        if (!title) {
            alert('Title is required');
            return;
        }
        
        const imagesArray = imagesRaw.split('\n').filter(line => line.trim() !== '');
        
        createDocument(title, content, imagesArray);
        
        document.getElementById('docTitle').value = '';
        document.getElementById('docContent').value = '';
        document.getElementById('docImages').value = '';
        
        alert('Document published successfully.');
    });
    
    document.getElementById('logoutBtn').addEventListener('click', function() {
        adminLogout();
    });
    
    document.getElementById('showLoginBtn').addEventListener('click', function() {
        if (isAdmin) {
            adminLogout();
        } else {
            document.getElementById('loginModal').classList.add('active');
        }
    });
    
    document.getElementById('closeModal').addEventListener('click', function() {
        document.getElementById('loginModal').classList.remove('active');
    });
    
    document.getElementById('adminLoginForm').addEventListener('submit', function(e) {
        e.preventDefault();
        const username = document.getElementById('adminUser').value;
        const password = document.getElementById('adminPass').value;
        adminLogin(username, password);
        document.getElementById('adminUser').value = '';
        document.getElementById('adminPass').value = '';
    });
    
    window.onclick = function(event) {
        const modal = document.getElementById('loginModal');
        if (event.target === modal) {
            modal.classList.remove('active');
        }
    };
    
    loadDocuments();
    checkSession();
</script>
</body>
</html>
