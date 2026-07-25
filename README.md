<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StormGames - דף הבית</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1a1a2e !important; 
            color: #ffffff;
            text-align: center;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        h1 {
            font-size: 3rem;
            color: #00fff0;
            margin-bottom: 5px;
            text-shadow: 0 0 10px rgba(0, 255, 240, 0.3);
        }

        p.subtitle {
            color: #888;
            font-size: 1.2rem;
            margin-top: 0;
        }

        .admin-top-bar {
            background-color: #0f0f1e;
            padding: 10px;
            border-bottom: 2px solid #333;
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .admin-trigger-btn {
            background-color: #00fff0;
            color: #000;
            border: none;
            padding: 8px 16px;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
        }

        #logout-btn {
            display: none;
            background-color: #ff3333;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        .search-container {
            margin-bottom: 40px;
        }

        .search-bar {
            width: 60%;
            max-width: 500px;
            padding: 12px 20px;
            font-size: 1rem;
            border: 2px solid #00fff0;
            border-radius: 25px;
            background-color: #0f0f1e;
            color: #fff;
            outline: none;
            transition: 0.3s;
        }
        .search-bar:focus {
            box-shadow: 0 0 15px #00fff0;
        }

        #game-zone {
            display: none; 
            background-color: #0f0f1e; 
            border: 3px solid #00fff0;
            border-radius: 15px; 
            max-width: 500px; 
            margin: 0 auto 40px auto; 
            padding: 20px;
            box-shadow: 0 0 30px rgba(0, 255, 240, 0.3);
        }

        #game-canvas {
            background-color: #050510; 
            display: block; 
            margin: 0 auto;
            border-radius: 10px; 
            cursor: crosshair;
        }

        .game-btn {
            background-color: #00fff0; 
            color: #000; 
            border: none; 
            padding: 10px 20px;
            font-size: 1rem; 
            font-weight: bold; 
            border-radius: 5px; 
            cursor: pointer; 
            margin-top: 15px;
            margin-left: 5px;
            margin-right: 5px;
        }
        .game-btn:hover { background-color: #ffffff; }

        .section-title {
            font-size: 1.8rem;
            border-bottom: 2px solid #333;
            padding-bottom: 10px;
            margin-bottom: 30px;
            text-align: right;
            color: #00fff0;
        }

        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
        }

        .game-card {
            background-color: #0f0f1e;
            border: 1px solid #333;
            border-radius: 10px;
            padding: 20px;
            transition: 0.3s;
            cursor: pointer;
            text-align: right;
        }
        .game-card:hover {
            transform: translateY(-5px);
            border-color: #00fff0;
            box-shadow: 0 5px 15px rgba(0, 255, 240, 0.2);
        }

        .game-thumb {
            width: 100%;
            height: 150px;
            background-color: #2a2a40;
            border-radius: 8px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #888;
            margin-bottom: 15px;
            font-weight: bold;
        }

        .active-thumb {
            background: linear-gradient(45deg, #00fff0, #0055ff);
            color: #fff;
        }

        #body-element.purple-active {
            background-color: #12072B !important; 
        }
        
        .emotion-card {
            background-color: #200F49 !important;
            border: 1px solid #4A1E87 !important;
        }
        .emotion-card:hover {
            border-color: #ff007f !important;
            box-shadow: 0 5px 15px rgba(255, 0, 127, 0.4) !important;
        }

        .emotion-thumb {
            background: linear-gradient(45deg, #ff007f, #7f00ff) !important;
            color: #fff !important;
        }

        .sponsor-section {
            margin-top: 80px;
            background: linear-gradient(135deg, #150030, #2b0054); 
            padding: 30px 20px;
            border-radius: 20px;
            border: 3px solid #7f00ff;
            box-shadow: 0 0 20px rgba(127, 0, 255, 0.3);
            cursor: pointer;
            transition: all 0.4s ease;
        }
        .sponsor-section:hover {
            transform: scale(1.02);
            border-color: #ff007f;
            box-shadow: 0 0 35px rgba(255, 0, 127, 0.6);
        }

        .neon-text {
            color: #ff007f;
            text-shadow: 0 0 10px rgba(255, 0, 127, 0.8);
            margin: 15px 0 5px 0;
            font-size: 1.6rem;
            font-weight: bold;
        }

        [contenteditable="true"]:focus {
            outline: 2px dashed #00fff0;
            background-color: rgba(0, 255, 240, 0.1);
            padding: 2px;
            border-radius: 4px;
        }
    </style>
</head>
<body id="body-element">

    <div class="admin-top-bar">
        <button class="admin-trigger-btn" id="login-btn" onclick="loginAdmin()">אתה אדמין? כנס עכשיו!</button>
        <button id="logout-btn" onclick="logoutAdmin()">התנתק מהאדמין</button>
    </div>

    <div id="main-page" style="display: block;">
        <div class="container">
            <header>
                <h1 id="main-title">StormGames</h1>
                <p id="main-subtitle" class="subtitle">ברוכים הבאים לעולם המשחקים שלנו</p>
            </header>

            <div class="search-container">
                <input type="text" class="search-bar" placeholder="חפש משחק ב-StormGames...">
            </div>

            <div id="game-zone">
                <h2 style="color: #00fff0; margin-top: 0;">תופס הברקים ⚡</h2>
                <p>הזיזו את העכבר ימינה ושמאלה כדי לתפוס ברקים צהובים!</p>
                <div style="font-size: 1.2rem; margin-bottom: 10px; font-weight: bold;">נקודות: <span id="score" style="color: #00fff0;">0</span></div>
                <canvas id="game-canvas" width="450" height="300"></canvas>
                <button class="game-btn" onclick="startGame()">התחל מחדש</button>
                <button class="game-btn" style="background-color: #ff3333; color: white;" onclick="closeGame()">סגור משחק</button>
            </div>

            <section style="margin-bottom: 60px;">
                <h2 class="section-title">המשחקים שלנו</h2>
                <div class="games-grid">
                    
                    <div class="game-card">
                        <div onclick="openGame()">
                            <div class="game-thumb active-thumb">⚡ לשחק עכשיו</div>
                        </div>
                        <h3 id="g1-title">תופס הברקים (משחק 1)</h3>
                        <p id="g1-desc">משחק ארקייד מהיר ומאתגר. לחצו כדי לשחק מיד!</p>
                    </div>

                    <div class="game-card">
                        <div class="game-thumb">בפיתוח...</div>
                        <h3 id="g2-title">משחק 2</h3>
                        <p id="g2-desc">תיאור קצר ומגניב של המשחק השני של StormGames.</p>
                    </div>

                    <div class="game-card">
                        <div class="game-thumb">בפיתוח...</div>
                        <h3 id="g3-title">משחק 3</h3>
                        <p id="g3-desc">תיאור קצר ומגניב של המשחק השלישי של StormGames.</p>
                    </div>

                </div>
            </section>

            <div class="sponsor-section" onclick="navigateToEmotions()">
                <div class="neon-text">שיתוף מיוחד: עולם הרגשות לילדים! 💜</div>
                <p style="color: #b39ddb; margin: 5px 0 0 0; font-size: 1.1rem; font-weight: 500;">לחצו כאן כדי להיכנס למתחם משחקי הרגשות הסגלגל והסודי שלנו 🔮</p>
            </div>
        </div>
    </div>

    <div id="emotion-page" style="display: none;">
        <div class="container">
            <header>
                <h1 style="color: #ff007f; text-shadow: 0 0 10px rgba(255, 0, 127, 0.3);">מתחם הרגשות 💜</h1>
                <p class="subtitle" style="color: #b39ddb;">משחקים שמחברים בין הלב למסך</p>
                <button class="game-btn" style="background-color: #ff007f; color: white;" onclick="navigateToMain()">← חזרה לאתר הראשי</button>
            </header>

            <section style="margin-top: 50px;">
                <h2 class="section-title" style="color: #ff007f; border-color: #4A1E87;">משחקי הרגשות</h2>
                <div class="games-grid">
                    
                    <div class="emotion-card game-card">
                        <div class="game-thumb emotion-thumb">❤️ פאזל הרגשות</div>
                        <h3 id="e1-title">מזהים ומנצחים</h3>
                        <p id="e1-desc" style="color: #d1c4e9;">משחק אינטראקטיבי המלמד ילדים לזהות רגשות דרך הבעות פנים וסיטואציות.</p>
                    </div>

                    <div class="emotion-card game-card">
                        <div class="game-thumb emotion-thumb">🧠 סערת המחשבות</div>
                        <h3 id="e2-title">להרגיע את הסופה</h3>
                        <p id="e2-desc" style="color: #d1c4e9;">משחק קצב מרגיע שעוזר להתמודד עם כעס ולחץ בצורה חיובית.</p>
                    </div>

                    <div class="emotion-card game-card">
                        <div class="game-thumb emotion-thumb">🌟 מבוך הביטחון</div>
                        <h3 id="e3-title">מוצאים את הכוח</h3>
                        <p id="e3-desc" style="color: #d1c4e9;">הרפתקה קטנה שבה אוספים נקודות של חוזק וביטחון עצמי.</p>
                    </div>

                </div>
            </section>
        </div>
    </div>

    <script>
        function navigateToEmotions() {
            document.getElementById('main-page').style.display = 'none';
            document.getElementById('emotion-page').style.display = 'block';
            document.getElementById('body-element').classList.add('purple-active'); 
            window.scrollTo(0, 0);
        }

        function navigateToMain() {
            document.getElementById('emotion-page').style.display = 'none';
            document.getElementById('main-page').style.display = 'block';
            document.getElementById('body-element').classList.remove('purple-active'); 
            window.scrollTo(0, 0);
        }

        function loginAdmin() {
            let username = prompt("הכנס שם משתמש אדמין:");
            if (username === null) return;

            let password = prompt("הכנס סיסמה סודית:");
            if (password === null) return;

            if (username === "ירין" && password === "123654") {
                alert("שלום ירין! מצב אדמין הופעל. עכשיו אתה יכול פשוט ללחוץ על כל טקסט באתר ולשנות אותו ישירות!");
                
                let editableIds = ['main-title', 'main-subtitle', 'g1-title', 'g1-desc', 'g2-title', 'g2-desc', 'g3-title', 'g3-desc', 'e1-title', 'e1-desc', 'e2-title', 'e2-desc', 'e3-title', 'e3-desc'];
                
                editableIds.forEach(id => {
                    let el = document.getElementById(id);
                    if(el) el.contentEditable = "true";
                });
                
                document.getElementById('logout-btn').style.display = 'inline-block';
                document.getElementById('login-btn').style.display = 'none';
            } else {
                alert("פרטים שגויים!");
            }
        }

        function logoutAdmin() {
            alert("התנתקת ממצב אדמין. השינויים נשמרו בדף הנוכחי.");
            
            let editableIds = ['main-title', 'main-subtitle', 'g1-title', 'g1-desc', 'g2-title', 'g2-desc', 'g3-title', 'g3-desc', 'e1-title', 'e1-desc', 'e2-title', 'e2-desc', 'e3-title', 'e3-desc'];
            
            editableIds.forEach(id => {
                let el = document.getElementById(id);
                if(el) el.contentEditable = "false";
            });
            
            document.getElementById('logout-btn').style.display = 'none';
            document.getElementById('login-btn').style.display = 'inline-block';
        }

        const canvas = document.getElementById('game-canvas');
        const ctx = canvas.getContext('2d');
        let score = 0;
        let gameInterval;
        let items = [];
        let player = { x: 200, y: 270, width: 60, height: 12 };

        canvas.addEventListener('mousemove', (e) => {
            const rect = canvas.getBoundingClientRect();
            player.x = e.clientX - rect.left - player.width / 2;
            if (player.x < 0) player.x = 0;
            if (player.x > canvas.width - player.width) player.x = canvas.width - player.width;
        });

        function openGame() {
            document.getElementById('game-zone').style.display = 'block';
            document.getElementById('game-zone').scrollIntoView({ behavior: 'smooth' });
            startGame();
        }

        function closeGame() {
            document.getElementById('game-zone').style.display = 'none';
            clearInterval(gameInterval);
        }

        function startGame() {
            clearInterval(gameInterval);
            score = 0;
            items = [];
            document.getElementById('score').innerText = score;
            gameInterval = setInterval(updateGame, 20);
        }

        function updateGame() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = '#00fff0';
            ctx.fillRect(player.x, player.y, player.width, player.height);

            if (Math.random() < 0.03) {
                items.push({ x: Math.random() * (canvas.width - 20), y: 0, speed: 4 });
            }

            for (let i = items.length - 1; i >= 0; i--) {
                let item = items[i];
                item.y += item.speed;
                ctx.fillStyle = '#ffff00';
                ctx.font = '18px Arial';
                ctx.fillText('⚡', item.x, item.y);

                if (item.y >= player.y && item.y <= player.y + player.height &&
                    item.x >= player.x - 10 && item.x <= player.x + player.width) {
                    score += 10;
                    document.getElementById('score').innerText = score;
                    items.splice(i, 1);
                    continue;
                }
                if (item.y > canvas.height) items.splice(i, 1);
            }
        }
    </script>
</body>
</html>
