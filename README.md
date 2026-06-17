<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>The YouTube Shorts Experiment</title>
    <style>
        :root {
            --bg-main: #0f172a;
            --bg-card: #1e293b;
            --bg-accent: #334155;
            --text-main: #ffffff;
            --text-muted: #94a3b8;
            --color-gold: #fbbf24;
            --color-green: #22c55e;
            
            /* Crypto Colors */
            --btc: #f7931a;
            --eth: #627eea;
            --sol: #14f195;
            --bnb: #f3ba2f;
            --trx: #ef0027;
            --usdt: #26a17b;
            --pol: #8247e5;
            --ton: #0088cc;
            --etc: #328332;
            --xrp: #23292f;
        }

        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: var(--bg-main);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            line-height: 1.5;
        }

        /* Header & Marketing Campaign */
        .hero-section {
            background: linear-gradient(180deg, #1e1b4b 0%, var(--bg-main) 100%);
            padding: 40px 20px;
            text-align: center;
            border-bottom: 1px solid #312e81;
        }

        .badge {
            background: #4338ca;
            color: #e0e7ff;
            padding: 6px 16px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: bold;
            letter-spacing: 1px;
            text-transform: uppercase;
            display: inline-block;
            margin-bottom: 15px;
        }

        h1 {
            font-size: 2.5rem;
            margin: 0 0 10px 0;
            background: linear-gradient(to right, #ffedd5, #fcd34d, #f97316);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 800;
        }

        .subtitle {
            max-width: 600px;
            margin: 0 auto 30px auto;
            color: var(--text-muted);
            font-size: 1.1rem;
        }

        /* Progress Bar */
        .progress-container {
            max-width: 600px;
            margin: 0 auto;
            background: var(--bg-card);
            padding: 20px;
            border-radius: 16px;
            box-shadow: 0 10px 25px -5px rgba(0,0,0,0.3);
        }

        .progress-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-weight: bold;
            font-size: 0.9rem;
        }

        .progress-wrap {
            height: 24px;
            background: var(--bg-accent);
            border-radius: 20px;
            overflow: hidden;
            border: 2px solid #475569;
        }

        .progress {
            width: 0%;
            height: 100%;
            background: linear-gradient(90deg, #22c55e, #4ade80);
            text-align: center;
            line-height: 20px;
            font-weight: bold;
            transition: width 0.5s ease;
        }

        /* Crypto Donation Grid */
        .crypto-section {
            max-width: 800px;
            margin: 30px auto;
            padding: 0 15px;
        }

        .crypto-title {
            text-align: center;
            color: var(--text-muted);
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 15px;
        }

        .crypto-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        .crypto-btn {
            background: var(--bg-card);
            border: 1px solid #334155;
            border-radius: 12px;
            padding: 12px 8px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 6px;
            font-size: 0.8rem;
            transition: all 0.2s ease;
            position: relative;
        }

        .crypto-btn:hover {
            transform: translateY(-2px);
            filter: brightness(1.2);
        }

        .crypto-btn .icon {
            font-size: 1.4rem;
        }

        /* Individual crypto borders for premium feel */
        .btn-btc { border-color: var(--btc); color: var(--btc); }
        .btn-eth { border-color: var(--eth); color: #a5b4fc; }
        .btn-sol { border-color: var(--sol); color: var(--sol); }
        .btn-bnb { border-color: var(--bnb); color: var(--bnb); }
        .btn-trx { border-color: var(--trx); color: #fca5a5; }
        .btn-usdt { border-color: var(--usdt); color: var(--usdt); }
        .btn-pol { border-color: var(--pol); color: #c084fc; }
        .btn-ton { border-color: var(--ton); color: #38bdf8; }
        .btn-etc { border-color: var(--etc); color: #4ade80; }
        .btn-xrp { border-color: #64748b; color: #cbd5e1; }

        /* Level Map / Gameplay Timeline */
        .map-container {
            max-width: 700px;
            margin: 50px auto;
            padding: 0 15px;
            position: relative;
        }

        .map-container::before {
            content: '';
            position: absolute;
            left: 39px;
            top: 20px;
            bottom: 20px;
            width: 4px;
            background: linear-gradient(180deg, #334155 0%, #1e293b 100%);
            z-index: 1;
        }

        .level-node {
            display: flex;
            align-items: center;
            gap: 20px;
            margin-bottom: 20px;
            position: relative;
            z-index: 2;
        }

        .level-circle {
            width: 52px;
            height: 52px;
            background: var(--bg-card);
            border: 3px solid #334155;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.6rem;
            box-shadow: 0 0 15px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
        }

        .level-node:hover .level-circle {
            transform: scale(1.1) rotate(5deg);
            border-color: var(--color-gold);
        }

        .level-content {
            flex: 1;
            background: var(--bg-card);
            border-radius: 16px;
            padding: 14px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border: 1px solid #273549;
        }

        .level-details {
            display: flex;
            flex-direction: column;
        }

        .level-number {
            color: var(--color-gold);
            font-size: 0.75rem;
            font-weight: 900;
            letter-spacing: 1px;
            margin-bottom: 2px;
        }

        .level-name {
            font-weight: 600;
            font-size: 1.05rem;
        }

        .level-price {
            color: var(--color-green);
            font-weight: 800;
            font-size: 1.1rem;
            background: rgba(34, 197, 94, 0.1);
            padding: 4px 12px;
            border-radius: 10px;
        }

        /* Leaderboard Section */
        .leaderboard-section {
            max-width: 600px;
            margin: 60px auto;
            background: padding-box linear-gradient(135deg, #1e293b, #0f172a);
            border: 2px solid #334155;
            border-radius: 24px;
            padding: 30px 20px;
        }

        .leaderboard-title {
            text-align: center;
            font-size: 1.8rem;
            font-weight: 800;
            margin-bottom: 30px;
            color: #f1f5f9;
        }

        .podium {
            display: flex;
            justify-content: center;
            align-items: flex-end;
            gap: 15px;
            margin-bottom: 35px;
            height: 160px;
        }

        .podium-place {
            background: var(--bg-card);
            border: 1px solid #334155;
            border-radius: 12px 12px 6px 6px;
            width: 100px;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 15px 5px;
            position: relative;
        }

        .podium-place .avatar {
            font-size: 2rem;
            margin-bottom: 5px;
        }

        .podium-place .username {
            font-size: 0.8rem;
            font-weight: bold;
            color: var(--text-muted);
            max-width: 90px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }

        .podium-place .rank-num {
            font-size: 1.5rem;
            font-weight: 900;
            margin-top: auto;
        }

        /* Podium Heights and Highlights */
        .place-1 { 
            height: 130px; 
            border-color: #fcd34d; 
            box-shadow: 0 0 20px rgba(252, 211, 77, 0.15);
        }
        .place-1 .rank-num { color: #fcd34d; }
        
        .place-2 { height: 100px; border-color: #cbd5e1; }
        .place-2 .rank-num { color: #cbd5e1; }
        
        .place-3 { height: 85px; border-color: #b45309; }
        .place-3 .rank-num { color: #b45309; }

        .backers-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .backer-row {
            display: flex;
            align-items: center;
            background: rgba(15, 23, 42, 0.6);
            padding: 12px 20px;
            border-radius: 12px;
            border: 1px solid #232f45;
        }

        .backer-rank {
            font-weight: bold;
            color: var(--text-muted);
            width: 35px;
        }

        .backer-name {
            flex: 1;
            font-weight: 600;
        }

        .backer-amount {
            color: var(--color-gold);
            font-weight: bold;
        }

        .empty-leaderboard {
            text-align: center;
            color: var(--text-muted);
            font-style: italic;
            padding: 20px 0;
        }

        /* Toast Notification */
        .toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--color-green);
            color: white;
            padding: 12px 24px;
            border-radius: 10px;
            font-weight: bold;
            box-shadow: 0 10px 15px -3px rgba(0,0,0,0.5);
            display: none;
            z-index: 1000;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateY(100px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* Responsive Design */
        @media(max-width: 768deg){
            .crypto-grid { grid-template-columns: repeat(3, 1fr); }
        }
        @media(max-width: 480deg){
            .crypto-grid { grid-template-columns: repeat(2, 1fr); }
            h1 { font-size: 1.8rem; }
            .level-content { padding: 10px 14px; }
            .level-name { font-size: 0.95rem; }
            .level-price { font-size: 0.95rem; }
        }
    </style>
</head>
<body>

    <!-- Toast Alert Box -->
    <div id="toast" class="toast">Address copied successfully! ✓</div>

    <!-- Hero Header -->
    <div class="hero-section">
        <span class="badge">Live YouTube Experiment</span>
        <h1>THE SHORTS DONATION GAME</h1>
        <p class="subtitle">Can a simple Shorts video complete all 100 global levels? Every single contribution unlocks the next tier real-time on our channel roadmap!</p>

        <!-- Dynamic Progress Module -->
        <div class="progress-container">
            <div class="progress-label">
                <span>Current Milestone Progress</span>
                <span id="progress-percent">0%</span>
            </div>
            <div class="progress-wrap">
                <div class="progress" id="main-progress"></div>
            </div>
        </div>
    </div>

    <!-- Crypto Addresses Grid Section -->
    <div class="crypto-section">
        <div class="crypto-title">Tap an asset below to instantly copy address:</div>
        <div class="crypto-grid">
            <button class="crypto-btn btn-btc" onclick="copyAddress('bc1q5gxpm2frv49drn05ejcxg7um048hhjwgkahl0k', this, 'BTC')">
                <span class="icon">₿</span><span>BTC</span>
            </button>
            <button class="crypto-btn btn-eth" onclick="copyAddress('0x2002F217A5991521fc8Aac74b522295693C18e36', this, 'ETH')">
                <span class="icon">Ξ</span><span>ETH</span>
            </button>
            <button class="crypto-btn btn-sol" onclick="copyAddress('7wFK8mBC9qNQ15VpX9PhCzABTLA5omAsVzx8Lud5MvN', this, 'SOL')">
                <span class="icon">☀️</span><span>SOL</span>
            </button>
            <button class="crypto-btn btn-bnb" onclick="copyAddress('0x2002f217a5991521fc8aac74b522295693c18e36', this, 'BNB')">
                <span class="icon">🔶</span><span>BNB Smart Chain</span>
            </button>
            <button class="crypto-btn btn-trx" onclick="copyAddress('TP9anAUgeWPbYi8p2C1ahS7XBCyYmZRfwc', this, 'TRX')">
                <span class="icon">💎</span><span>TRX (Tron)</span>
            </button>
            <button class="crypto-btn btn-usdt" onclick="copyAddress('TP9anAUgeWPbYi8p2C1ahS7XBCyYmZRfwc', this, 'USDT TRC20')">
                <span class="icon">💵</span><span>USDT (TRC20)</span>
            </button>
            <button class="crypto-btn btn-usdt" onclick="copyAddress('0x2002F217A5991521fc8Aac74b522295693C18e36', this, 'USDT ERC20')">
                <span class="icon">💵</span><span>USDT (ERC20)</span>
            </button>
            <button class="crypto-btn btn-usdt" onclick="copyAddress('7wFK8mBC9qNQ15VpX9PhCzABTLA5omAsVzx8Lud5MvN', this, 'USDT SPL')">
                <span class="icon">💵</span><span>USDT (SPL)</span>
            </button>
            <button class="crypto-btn btn-usdt" onclick="copyAddress('0x2002F217A5991521fc8Aac74b522295693C18e36', this, 'USDT Polygon')">
                <span class="icon">💵</span><span>USDT (POLYGON)</span>
            </button>
            <button class="crypto-btn btn-pol" onclick="copyAddress('0x2002F217A5991521fc8Aac74b522295693C18e36', this, 'POL')">
                <span class="icon">🍇</span><span>POL (Polygon)</span>
            </button>
            <button class="crypto-btn btn-ton" onclick="copyAddress('UQCEdaxRbzLGUgihFx-51Au7mc2DhV5FlcPNRKuiiaJlIDJW', this, 'TON')">
                <span class="icon">💎</span><span>TON</span>
            </button>
            <button class="crypto-btn btn-etc" onclick="copyAddress('0xF5292F1051686fA445b72B85BD59E4bc6FCBC4aC', this, 'ETC')">
                <span class="icon">🍀</span><span>ETC</span>
            </button>
            <button class="crypto-btn btn-xrp" onclick="copyAddress('rpAffRfsJ6CdNkGEdGdafZuZx1zcbNfJBk', this, 'XRP')">
                <span class="icon">✕</span><span>XRP</span>
            </button>
        </div>
    </div>

    <!-- 100 Levels Map Layout -->
    <div class="map-container" id="levels-map">
        <!-- Generated inside Javascript for optimal and seamless loading -->
    </div>

    <!-- Global Experiment Leaderboard -->
    <div class="leaderboard-section">
        <div class="leaderboard-title">🏆 Top Experiment Backers</div>
        
        <!-- Podium Element -->
        <div class="podium">
            <div class="podium-place place-2">
                <div class="avatar">🥈</div>
                <div class="username">Empty</div>
                <div class="rank-num">2</div>
            </div>
            <div class="podium-place place-1">
                <div class="avatar">👑</div>
                <div class="username">Empty</div>
                <div class="rank-num">1</div>
            </div>
            <div class="podium-place place-3">
                <div class="avatar">🥉</div>
                <div class="username">Empty</div>
                <div class="rank-num">3</div>
            </div>
        </div>

        <!-- Scroll list for other donors -->
        <div class="backers-list">
            <div class="empty-leaderboard">No sponsors yet. Be the first to secure a spot! 🔥</div>
        </div>
    </div>

    <script>
        // 100 Customized Levels Dataset with premium glossy emojis
        const gameLevels = [
            { id: 1, name: "Cup of coffee", price: 4, emoji: "☕" },
            { id: 2, name: "Chocolate bar", price: 5, emoji: "🍫" },
            { id: 3, name: "Hot dog", price: 6, emoji: "🌭" },
            { id: 4, name: "Cotton candy on a stick", price: 7, emoji: "🍭" },
            { id: 5, name: "Rubber duck", price: 8, emoji: "🦆" },
            { id: 6, name: "Condoms (3-pack)", price: 9, emoji: "🎈" },
            { id: 7, name: "Red Bull energy drink (can)", price: 10, emoji: "⚡" },
            { id: 8, name: "Watermelon (whole)", price: 11, emoji: "🍉" },
            { id: 9, name: "Slice of cake (at a cafe)", price: 12, emoji: "🍰" },
            { id: 10, name: "Cactus (small in a pot)", price: 13, emoji: "🌵" },
            { id: 11, name: "Bucket (plastic)", price: 14, emoji: "🪣" },
            { id: 12, name: "Sanitary pads (pack)", price: 15, emoji: "🧼" },
            { id: 13, name: "Movie ticket", price: 16, emoji: "🎟️" },
            { id: 14, name: "Popcorn (large at a theater)", price: 18, emoji: "🍿" },
            { id: 15, name: "Goldfish", price: 19, emoji: "🐟" },
            { id: 16, name: "Water gun (medium)", price: 20, emoji: "🔫" },
            { id: 17, name: "Salami sausage (whole stick)", price: 22, emoji: "🥩" },
            { id: 18, name: "Shovel (garden)", price: 25, emoji: "🪵" },
            { id: 19, name: "Pizza (large meat)", price: 26, emoji: "🍕" },
            { id: 20, name: "Travel mug", price: 28, emoji: "🥤" },
            { id: 21, name: "Hand gripper / Resistance band", price: 29, emoji: "💪" },
            { id: 22, name: "Book (hardcover bestseller)", price: 30, emoji: "📘" },
            { id: 23, name: "T-shirt (basic branded)", price: 32, emoji: "👕" },
            { id: 24, name: "Blender (kitchen)", price: 35, emoji: "🌪️" },
            { id: 25, name: "Red skirt", price: 36, emoji: "👗" },
            { id: 26, name: "Thermos (1 liter)", price: 38, emoji: "🍼" },
            { id: 27, name: "Barbie doll (original)", price: 40, emoji: "👱‍♀️" },
            { id: 28, name: "Bra", price: 42, emoji: "👙" },
            { id: 29, name: "Floor fan", price: 45, emoji: "🌀" },
            { id: 30, name: "Gaming mouse pad (large)", price: 46, emoji: "🗺️" },
            { id: 31, name: "Notebook / Planner (leather)", price: 48, emoji: "📓" },
            { id: 32, name: "Inflatable unicorn (pool float)", price: 50, emoji: "🦄" },
            { id: 33, name: "Darts set (board and darts)", price: 52, emoji: "🎯" },
            { id: 34, name: "Dinosaur slippers", price: 55, emoji: "🦖" },
            { id: 35, name: "Desk lamp", price: 58, emoji: "💡" },
            { id: 36, name: "Wireless mouse", price: 60, emoji: "🖱️" },
            { id: 37, name: "Power bank (20,000 mAh)", price: 65, emoji: "🔋" },
            { id: 38, name: "Wig (synthetic)", price: 68, emoji: "💇" },
            { id: 39, name: "Gaming controller (Xbox/PS)", price: 70, emoji: "🎮" },
            { id: 40, name: "Large piñata (empty)", price: 72, emoji: "🪅" },
            { id: 41, name: "Baseball bat (aluminum)", price: 74, emoji: "🦇" },
            { id: 42, name: "Crutches (pair, aluminum)", price: 76, emoji: "🩼" },
            { id: 43, name: "Backpack (urban casual)", price: 80, emoji: "🎒" },
            { id: 44, name: "High heels", price: 85, emoji: "👠" },
            { id: 45, name: "Good Wi-Fi 6 router", price: 88, emoji: "🌐" },
            { id: 46, name: "Men's dress shoes (leather)", price: 92, emoji: "👞" },
            { id: 47, name: "S
