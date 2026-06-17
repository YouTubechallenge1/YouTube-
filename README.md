<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>0$ to 1000$ Real-Life Level Up Challenge</title>
    <!-- Google Fonts & FontAwesome Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --accent-color: #38bdf8;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --success: #22c55e;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .game-container {
            max-width: 600px;
            width: 100%;
            background: var(--card-bg);
            border-radius: 24px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
            border: 2px solid #334155;
        }

        /* --- HEADER SECTION --- */
        .header {
            text-align: center;
            margin-bottom: 25px;
        }

        .badge {
            background: linear-gradient(45deg, #f59e0b, #ef4444);
            color: white;
            padding: 6px 16px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1px;
            display: inline-block;
            margin-bottom: 10px;
            box-shadow: 0 4px 15px rgba(239, 68, 68, 0.4);
        }

        h1 {
            font-size: 2.2rem;
            font-weight: 800;
            background: linear-gradient(to right, #38bdf8, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            line-height: 1.2;
            margin-bottom: 8px;
        }

        .tagline {
            color: var(--text-muted);
            font-size: 0.95rem;
            line-height: 1.4;
        }

        /* --- PROGRESS BAR --- */
        .progress-section {
            background: #111827;
            padding: 20px;
            border-radius: 16px;
            margin-bottom: 25px;
            border: 1px solid #334155;
        }

        .progress-meta {
            display: flex;
            justify-content: space-between;
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 1.1rem;
        }

        .progress-bar-container {
            background: #1f2937;
            height: 24px;
            border-radius: 12px;
            overflow: hidden;
            position: relative;
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.6);
        }

        .progress-bar {
            width: 0%; /* Dynamic tracking starting position */
            height: 100%;
            background: linear-gradient(90deg, #3b82f6, #10b981);
            border-radius: 12px;
            transition: width 0.5s ease;
        }

        /* --- CRYPTO GATEWAY GRID --- */
        .crypto-title {
            text-align: center;
            font-size: 0.9rem;
            color: var(--text-muted);
            margin-bottom: 12px;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
        }

        .crypto-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-bottom: 30px;
        }

        @media (min-width: 450px) {
            .crypto-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        .crypto-btn {
            border: none;
            padding: 12px 8px;
            border-radius: 12px;
            color: white;
            font-weight: 600;
            font-size: 0.8rem;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 6px;
            transition: transform 0.2s, box-shadow 0.2s;
            position: relative;
        }

        .crypto-btn:hover {
            transform: translateY(-3px);
            filter: brightness(1.15);
        }

        .crypto-btn i {
            font-size: 1.4rem;
        }

        /* Standardized Asset Colors */
        .btn-btc { background: #f59e0b; box-shadow: 0 4px 12px rgba(245,158,11,0.3); }
        .btn-eth { background: #627eea; box-shadow: 0 4px 12px rgba(98,126,234,0.3); }
        .btn-sol { background: #14f195; color: #000; box-shadow: 0 4px 12px rgba(20,241,149,0.3); }
        .btn-bnb { background: #f3ba2f; color: #000; box-shadow: 0 4px 12px rgba(243,186,47,0.3); }
        .btn-trx { background: #ef4444; box-shadow: 0 4px 12px rgba(239,68,68,0.3); }
        .btn-usdt { background: #26a17b; box-shadow: 0 4px 12px rgba(38,161,123,0.3); }
        .btn-ton { background: #0088cc; box-shadow: 0 4px 12px rgba(0,136,204,0.3); }
        .btn-xrp { background: #23292f; box-shadow: 0 4px 12px rgba(35,41,47,0.3); }

        /* --- TOAST NOTIFICATION --- */
        .toast {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: #22c55e;
            color: white;
            padding: 12px 24px;
            border-radius: 50px;
            font-weight: 600;
            box-shadow: 0 10px 25px rgba(34,197,94,0.4);
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            z-index: 1000;
            display: flex;
            align-items: center;
            gap: 8px;
            pointer-events: none;
        }

        .toast.show {
            transform: translateX(-50%) translateY(0);
        }

        /* --- MAP QUEST QUESTLINE LIST --- */
        .quest-list {
            max-height: 400px;
            overflow-y: auto;
            padding-right: 8px;
            margin-bottom: 30px;
            border: 1px solid #334155;
            border-radius: 16px;
            background: #111827;
        }

        .quest-list::-webkit-scrollbar {
            width: 6px;
        }
        .quest-list::-webkit-scrollbar-thumb {
            background: #475569;
            border-radius: 4px;
        }

        .level-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 14px 16px;
            border-bottom: 1px solid #1e293b;
            transition: background 0.2s;
        }

        .level-item:last-child { border-bottom: none; }

        .level-left {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .level-num {
            font-size: 0.75rem;
            background: #334155;
            padding: 2px 8px;
            border-radius: 6px;
            color: var(--text-muted);
            font-weight: 600;
            min-width: 55px;
            text-align: center;
        }

        /* 3D Asset Pop Styling */
        .level-icon {
            font-size: 1.6rem;
            filter: drop-shadow(0 4px 6px rgba(0,0,0,0.3));
            transform: scale(1);
            transition: transform 0.2s;
        }
        .level-item:hover .level-icon {
            transform: scale(1.2) rotate(5deg);
        }

        .level-name {
            font-weight: 600;
            font-size: 0.95rem;
        }

        .level-price {
            font-weight: 800;
            color: #38bdf8;
            font-size: 1.05rem;
        }

        /* --- THE PODIUM LEADERBOARD --- */
        .leaderboard-title {
            text-align: center;
            font-weight: 800;
            font-size: 1.3rem;
            margin-bottom: 20px;
            letter-spacing: 0.5px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
        }

        .pedestal-container {
            display: flex;
            justify-content: center;
            align-items: flex-end;
            height: 160px;
            margin-top: 10px;
            gap: 12px;
            padding-bottom: 10px;
        }

        .pedestal-rank {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100px;
            position: relative;
        }

        .donator-name {
            font-size: 0.75rem;
            font-weight: 600;
            text-align: center;
            margin-bottom: 6px;
            max-width: 90px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            color: var(--text-main);
        }

        .block {
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            font-weight: 800;
            color: rgba(255,255,255,0.9);
            border-radius: 8px 8px 4px 4px;
            position: relative;
            box-shadow: inset 0 4px 4px rgba(255,255,255,0.1), 0 8px 16px rgba(0,0,0,0.4);
        }

        .block span {
            font-size: 1.5rem;
        }

        .block-amount {
            font-size: 0.7rem !important;
            font-weight: 600;
            opacity: 0.85;
        }

        /* Podium Placement Heights and Color Theme */
        .rank-2 .block {
            height: 65px;
            background: linear-gradient(135deg, #94a3b8, #475569);
            border: 1px solid #cbd5e1;
        }
        .rank-1 .block {
            height: 95px;
            background: linear-gradient(135deg, #fbbf24, #d97706);
            border: 1px solid #fde047;
        }
        .rank-3 .block {
            height: 45px;
            background: linear-gradient(135deg, #b45309, #78350f);
            border: 1px solid #ca8a04;
        }

        .crown {
            position: absolute;
            top: -24px;
            color: #fbbf24;
            font-size: 1.1rem;
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.5));
            animation: float 2s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-4px); }
        }
    </style>
</head>
<body>

    <div class="game-container">
        
        <!-- HEADER -->
        <div class="header">
            <div class="badge"><i class="fa-solid fa-trophy"></i> Live Experiment</div>
            <h1>0$ TO 1000$ <br>LEVEL UP CHALLENGE</h1>
            <p class="tagline">Can regular viewers scale this real-world value ladder? Choose an asset below to back the challenge and advance the track!</p>
        </div>

        <!-- PROGRESS MATRIX -->
        <div class="progress-section">
            <div class="progress-meta">
                <span>PROGRESS</span>
                <span id="pct-label">0%</span>
            </div>
            <div class="progress-bar-container">
                <div class="progress-bar" id="progress-indicator"></div>
            </div>
        </div>

        <!-- CRYPTO SYSTEM LINKS -->
        <p class="crypto-title">Tap an asset to copy deposit address</p>
        <div class="crypto-grid">
            <button class="crypto-btn btn-btc" data-addr="bc1q5gxpm2frv49drn05ejcxg7um048hhjwgkahl0k">
                <i class="fa-brands fa-bitcoin"></i>BTC
            </button>
            <button class="crypto-btn btn-usdt" data-addr="TP9anAUgeWPbYi8p2C1ahS7XBCyYmZRfwc">
                <i class="fa-solid fa-dollar-sign"></i>TRC20
            </button>
            <button class="crypto-btn btn-eth" data-addr="0x2002F217A5991521fc8Aac74b522295693C18e36">
                <i class="fa-brands fa-ethereum"></i>ETH
            </button>
            <button class="crypto-btn btn-sol" data-addr="7wFK8mBC9qNQ15VpX9PhCzABTLA5omAsVzx8Lud5MvN">
                <i class="fa-solid fa-bolt"></i>SOL
            </button>
            <button class="crypto-btn btn-ton" data-addr="UQCEdaxRbzLGUgihFx-51Au7mc2DhV5FlcPNRKuiiaJlIDJW">
                <i class="fa-solid fa-paper-plane"></i>TON
            </button>
            <button class="crypto-btn btn-bnb" data-addr="0x2002f217a5991521fc8aac74b522295693c18e36">
                <i class="fa-solid fa-cubes"></i>BNB
            </button>
            <button class="crypto-btn btn-trx" data-addr="TP9anAUgeWPbYi8p2C1ahS7XBCyYmZRfwc">
                <i class="fa-solid fa-diamond"></i>TRX
            </button>
            <button class="crypto-btn btn-xrp" data-addr="rpAffRfsJ6CdNkGEdGdafZuZx1zcbNfJBk">
                <i class="fa-solid fa-circle-nodes"></i>XRP
            </button>
        </div>

        <!-- CHALLENGE ITEMS MAP -->
        <div class="quest-list" id="quest-items-box">
            <!-- Programmatically populated by JS for optimization and perfect layouts -->
        </div>

        <!-- PODIUM LEADERBOARD -->
        <div class="leaderboard-title">
            <i class="fa-solid fa-crown" style="color: #fbbf24;"></i> TOP CHALLENGERS
        </div>
        
        <div class="pedestal-container">
            <!-- 2nd Place -->
            <div class="pedestal-rank rank-2">
                <div class="donator-name">Waiting...</div>
                <div class="block">
                    <span>2</span>
                    <span class="block-amount">-</span>
                </div>
            </div>
            <!-- 1st Place -->
            <div class="pedestal-rank rank-1">
                <i class="fa-solid fa-crown crown"></i>
                <div class="donator-name">Waiting...</div>
                <div class="block">
                    <span>1</span>
                    <span class="block-amount">-</span>
                </div>
            </div>
            <!-- 3rd Place -->
            <div class="pedestal-rank rank-3">
                <div class="donator-name">Waiting...</div>
                <div class="block">
                    <span>3</span>
                    <span class="block-amount">-</span>
                </div>
            </div>
        </div>

    </div>

    <!-- UI TOAST POPUP FOR APP COPY ACTIONS -->
    <div class="toast" id="clipboard-toast">
        <i class="fa-solid fa-circle-check"></i> Address copied to clipboard!
    </div>

    <script>
        // 100 Level Item Catalog Array mapped with Rich Fluent Visual Asset Icons
        const levelsData = [
            {lvl: 1, name: "Cup of coffee", price: 4, icon: "☕"},
            {lvl: 2, name: "Chocolate bar", price: 5, icon: "🍫"},
            {lvl: 3, name: "Hot dog", price: 6, icon: "🌭"},
            {lvl: 4, name: "Cotton candy on a stick", price: 7, icon: "🍭"},
            {lvl: 5, name: "Rubber duck", price: 8, icon: "🦆"},
            {lvl: 6, name: "Condoms (3-pack)", price: 9, icon: "📦"},
            {lvl: 7, name: "Red Bull energy drink (can)", price: 10, icon: "⚡"},
            {lvl: 8, name: "Watermelon (whole)", price: 11, icon: "🍉"},
            {lvl: 9, name: "Slice of cake (at a cafe)", price: 12, icon: "🍰"},
            {lvl: 10, name: "Cactus (small in a pot)", price: 13, icon: "🌵"},
            {lvl: 11, name: "Bucket (plastic)", price: 14, icon: "🪣"},
            {lvl: 12, name: "Sanitary pads (pack)", price: 15, icon: "🩹"},
            {lvl: 13, name: "Movie ticket", price: 16, icon: "🎟️"},
            {lvl: 14, name: "Popcorn (large at a theater)", price: 18, icon: "🍿"},
            {lvl: 15, name: "Goldfish", price: 19, icon: "🐟"},
            {lvl: 16, name: "Water gun (medium)", price: 20, icon: "🔫"},
            {lvl: 17, name: "Salami sausage (whole stick)", price: 22, icon: "🥩"},
            {lvl: 18, name: "Shovel (garden)", price: 25, icon: "🛠️"},
            {lvl: 19, name: "Pizza (large meat)", price: 26, icon: "🍕"},
            {lvl: 20, name: "Travel mug", price: 28, icon: "🥤"},
            {lvl: 21, name: "Hand gripper / Resistance band", price: 29, icon: "💪"},
            {lvl: 22, name: "Book (hardcover bestseller)", price: 30, icon: "📘"},
            {lvl: 23, name: "T-shirt (basic branded)", price: 32, icon: "👕"},
            {lvl: 24, name: "Blender (kitchen)", price: 35, icon: "🌪️"},
            {lvl: 25, name: "Red skirt", price: 36, icon: "👗"},
            {lvl: 26, name: "Thermos (1 liter)", price: 38, icon: "🧪"},
            {lvl: 27, name: "Barbie doll (original)", price: 40, icon: "👱‍♀️"},
            {lvl: 28, name: "Bra", price: 42, icon: "👙"},
            {lvl: 29, name: "Floor fan", price: 45, icon: "💨"},
            {lvl: 30, name: "Gaming mouse pad (large)", price: 46, icon: "🗺️"},
            {lvl: 31, name: "Notebook / Planner (leather)", price: 48, icon: "📓"},
            {lvl: 32, name: "Inflatable unicorn (pool float)", price: 50, icon: "🦄"},
            {lvl: 33, name: "Darts set (board and darts)", price: 52, icon: "🎯"},
            {lvl: 34, name: "Dinosaur slippers", price: 55, icon: "🦖"},
            {lvl: 35, name: "Desk lamp", price: 58, icon: "💡"},
            {lvl: 36, name: "Wireless mouse", price: 60, icon: "🖱️"},
            {lvl: 37, name: "Power bank (20,000 mAh)", price: 65, icon: "🔋"},
            {lvl: 38, name: "Wig (synthetic)", price: 68, icon: "💇"},
            {lvl: 39, name: "Gaming controller (Xbox/PS)", price: 70, icon: "🎮"},
            {lvl: 40, name: "Large piñata (empty)", price: 72, icon: "🪅"},
            {lvl: 41, name: "Baseball bat (aluminum)", price: 74, icon: "🦇"},
            {lvl: 42, name: "Crutches (pair, aluminum)", price: 76, icon: "🩼"},
            {lvl: 43, name: "Backpack (urban casual)", price: 80, icon: "🎒"},
            {lvl: 44, name: "High heels", price: 85, icon: "👠"},
            {lvl: 45, name: "Good Wi-Fi 6 router", price: 88, icon: "🌐"},
            {lvl: 46, name: "Men's dress shoes (leather)", price: 92, icon: "👞"},
            {lvl: 47, name: "Soccer ball (official/original)", price: 95, icon: "⚽"},
            {lvl: 48, name: "Fire extinguisher (car/home)", price: 100, icon: "🧯"},
            {lvl: 49, name: "Sneakers (classic branded)", price: 105, icon: "👟"},
            {lvl: 50, name: "Protein powder (2 kg tub)", price: 110, icon: "🥤"},
            {lvl: 51, name: "RC helicopter (remote control)", price: 115, icon: "🚁"},
            {lvl: 52, name: "Sex toy / Vibrator (high quality)", price: 120, icon: "🔮"},
            {lvl: 53, name: "Bluetooth speaker (JBL Flip level)", price: 125, icon: "🔊"},
            {lvl: 54, name: "Boxing gloves (leather)", price: 130, icon: "🥊"},
            {lvl: 55, name: "Bouquet of flowers (large rose bouquet)", price: 135, icon: "💐"},
            {lvl: 56, name: "Good inline skates / Rollerblades", price: 140, icon: "🛼"},
            {lvl: 57, name: "Banana costume (mascot suit)", price: 145, icon: "🍌"},
            {lvl: 58, name: "Webcam (streaming, 1080p)", price: 150, icon: "📷"},
            {lvl: 59, name: "Kettlebell (24 kg)", price: 155, icon: "🏋️"},
            {lvl: 60, name: "Good ice skates", price: 160, icon: "⛸️"},
            {lvl: 61, name: "YouTube Premium (1-year subscription)", price: 165, icon: "📺"},
            {lvl: 62, name: "Mechanical keyboard", price: 170, icon: "⌨️"},
            {lvl: 63, name: "Wireless over-ear headphones", price: 180, icon: "🎧"},
            {lvl: 64, name: "USB microphone (streaming)", price: 190, icon: "🎙️"},
            {lvl: 65, name: "LEGO set (medium-large)", price: 200, icon: "🧱"},
            {lvl: 66, name: "Fish tank / Aquarium (50-60L with filter)", price: 220, icon: "🐠"},
            {lvl: 67, name: "E-reader (Kindle)", price: 240, icon: "📖"},
            {lvl: 
