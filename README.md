<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>0$ to 1000$ Real-Life Level Up Challenge</title>
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
            width: 0%; /* Поменяй тут на нужный процент, например 5%, если игра началась */
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
            transition: all 0.2s ease;
            position: relative;
        }

        .crypto-btn:hover {
            transform: translateY(-3px);
            filter: brightness(1.15);
        }

        .crypto-btn i {
            font-size: 1.4rem;
        }

        /* Анимация клика (Копирования) */
        .crypto-btn.copied {
            background: #22c55e !important;
            box-shadow: 0 0 15px #22c55e !important;
            transform: scale(0.95);
        }

        /* Цвета кнопок */
        .btn-btc { background: #f59e0b; box-shadow: 0 4px 12px rgba(245,158,11,0.3); }
        .btn-usdt { background: #26a17b; box-shadow: 0 4px 12px rgba(38,161,123,0.3); }
        .btn-eth { background: #627eea; box-shadow: 0 4px 12px rgba(98,126,234,0.3); }
        .btn-sol { background: #14f195; color: #000; box-shadow: 0 4px 12px rgba(20,241,149,0.3); }
        .btn-ton { background: #0088cc; box-shadow: 0 4px 12px rgba(0,136,204,0.3); }
        .btn-bnb { background: #f3ba2f; color: #000; box-shadow: 0 4px 12px rgba(243,186,47,0.3); }
        .btn-trx { background: #ef4444; box-shadow: 0 4px 12px rgba(239,68,68,0.3); }
        .btn-xrp { background: #23292f; box-shadow: 0 4px 12px rgba(35,41,47,0.3); }

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

        /* Скрытый инпут для железобетонного копирования */
        #hidden-copy-input {
            position: absolute;
            left: -9999px;
            top: -9999px;
        }
    </style>
</head>
<body>

    <textarea id="hidden-copy-input"></textarea>

    <div class="game-container">
        
        <div class="header">
            <div class="badge"><i class="fa-solid fa-trophy"></i> Live Experiment</div>
            <h1>0$ TO 1000$ <br>LEVEL UP CHALLENGE</h1>
            <p class="tagline">Can regular viewers scale this real-world value ladder? Choose an asset below to back the challenge and advance the track!</p>
        </div>

        <div class="progress-section">
            <div class="progress-meta">
                <span>PROGRESS</span>
                <span id="pct-label">0%</span>
            </div>
            <div class="progress-bar-container">
                <div class="progress-bar" id="progress-indicator"></div>
            </div>
        </div>

        <p class="crypto-title">Tap an asset to copy deposit address</p>
        <div class="crypto-grid">
            <button class="crypto-btn btn-btc" data-addr="bc1q5gxpm2frv49drn05ejcxg7um048hhjwgkahl0k">
                <i class="fa-brands fa-bitcoin"></i><span>BTC</span>
            </button>
            <button class="crypto-btn btn-usdt" data-addr="TP9anAUgeWPbYi8p2C1ahS7XBCyYmZRfwc">
                <i class="fa-solid fa-dollar-sign"></i><span>TRC20</span>
            </button>
            <button class="crypto-btn btn-eth" data-addr="0x2002F217A5991521fc8Aac74b522295693C18e36">
                <i class="fa-brands fa-ethereum"></i><span>ETH</span>
            </button>
            <button class="crypto-btn btn-sol" data-addr="7wFK8mBC9qNQ15VpX9PhCzABTLA5omAsVzx8Lud5MvN">
                <i class="fa-solid fa-bolt"></i><span>SOL</span>
            </button>
            <button class="crypto-btn btn-ton" data-addr="UQCEdaxRbzLGUgihFx-51Au7mc2DhV5FlcPNRKuiiaJlIDJW">
                <i class="fa-solid fa-paper-plane"></i><span>TON</span>
            </button>
            <button class="crypto-btn btn-bnb" data-addr="0x2002f217a5991521fc8aac74b522295693c18e36">
                <i class="fa-solid fa-cubes"></i><span>BNB</span>
            </button>
            <button class="crypto-btn btn-trx" data-addr="TP9anAUgeWPbYi8p2C1ahS7XBCyYmZRfwc">
                <i class="fa-solid fa-diamond"></i><span>TRX</span>
            </button>
            <button class="crypto-btn btn-xrp" data-addr="rpAffRfsJ6CdNkGEdGdafZuZx1zcbNfJBk">
                <i class="fa-solid fa-circle-nodes"></i><span>XRP</span>
            </button>
        </div>

        <div class="quest-list">
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 1</span><span class="level-icon">☕</span><span class="level-name">Cup of coffee</span></div><div class="level-price">$4</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 2</span><span class="level-icon">🍫</span><span class="level-name">Chocolate bar</span></div><div class="level-price">$5</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 3</span><span class="level-icon">🌭</span><span class="level-name">Hot dog</span></div><div class="level-price">$6</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 4</span><span class="level-icon">🍭</span><span class="level-name">Cotton candy on a stick</span></div><div class="level-price">$7</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 5</span><span class="level-icon">🦆</span><span class="level-name">Rubber duck</span></div><div class="level-price">$8</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 6</span><span class="level-icon">📦</span><span class="level-name">Condoms (3-pack)</span></div><div class="level-price">$9</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 7</span><span class="level-icon">⚡</span><span class="level-name">Red Bull energy drink (can)</span></div><div class="level-price">$10</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 8</span><span class="level-icon">🍉</span><span class="level-name">Watermelon (whole)</span></div><div class="level-price">$11</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 9</span><span class="level-icon">🍰</span><span class="level-name">Slice of cake (at a cafe)</span></div><div class="level-price">$12</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 10</span><span class="level-icon">🌵</span><span class="level-name">Cactus (small in a pot)</span></div><div class="level-price">$13</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 11</span><span class="level-icon">🪣</span><span class="level-name">Bucket (plastic)</span></div><div class="level-price">$14</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 12</span><span class="level-icon">🩹</span><span class="level-name">Sanitary pads (pack)</span></div><div class="level-price">$15</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 13</span><span class="level-icon">🎟️</span><span class="level-name">Movie ticket</span></div><div class="level-price">$16</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 14</span><span class="level-icon">🍿</span><span class="level-name">Popcorn (large at a theater)</span></div><div class="level-price">$18</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 15</span><span class="level-icon">🐟</span><span class="level-name">Goldfish</span></div><div class="level-price">$19</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 16</span><span class="level-icon">🔫</span><span class="level-name">Water gun (medium)</span></div><div class="level-price">$20</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 17</span><span class="level-icon">🥩</span><span class="level-name">Salami sausage (whole stick)</span></div><div class="level-price">$22</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 18</span><span class="level-icon">🛠️</span><span class="level-name">Shovel (garden)</span></div><div class="level-price">$25</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 19</span><span class="level-icon">🍕</span><span class="level-name">Pizza (large meat)</span></div><div class="level-price">$26</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 20</span><span class="level-icon">🥤</span><span class="level-name">Travel mug</span></div><div class="level-price">$28</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 21</span><span class="level-icon">💪</span><span class="level-name">Hand gripper / Resistance band</span></div><div class="level-price">$29</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 22</span><span class="level-icon">📘</span><span class="level-name">Book (hardcover bestseller)</span></div><div class="level-price">$30</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 23</span><span class="level-icon">👕</span><span class="level-name">T-shirt (basic branded)</span></div><div class="level-price">$32</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 24</span><span class="level-icon">🌪️</span><span class="level-name">Blender (kitchen)</span></div><div class="level-price">$35</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 25</span><span class="level-icon">👗</span><span class="level-name">Red skirt</span></div><div class="level-price">$36</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 26</span><span class="level-icon">🧪</span><span class="level-name">Thermos (1 liter)</span></div><div class="level-price">$38</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 27</span><span class="level-icon">👱‍♀️</span><span class="level-name">Barbie doll (original)</span></div><div class="level-price">$40</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 28</span><span class="level-icon">👙</span><span class="level-name">Bra</span></div><div class="level-price">$42</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 29</span><span class="level-icon">💨</span><span class="level-name">Floor fan</span></div><div class="level-price">$45</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 30</span><span class="level-icon">🗺️</span><span class="level-name">Gaming mouse pad (large)</span></div><div class="level-price">$46</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 31</span><span class="level-icon">📓</span><span class="level-name">Notebook / Planner (leather)</span></div><div class="level-price">$48</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 32</span><span class="level-icon">🦄</span><span class="level-name">Inflatable unicorn (pool float)</span></div><div class="level-price">$50</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 33</span><span class="level-icon">🎯</span><span class="level-name">Darts set (board and darts)</span></div><div class="level-price">$52</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 34</span><span class="level-icon">🦖</span><span class="level-name">Dinosaur slippers</span></div><div class="level-price">$55</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 35</span><span class="level-icon">💡</span><span class="level-name">Desk lamp</span></div><div class="level-price">$58</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 36</span><span class="level-icon">🖱️</span><span class="level-name">Wireless mouse</span></div><div class="level-price">$60</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 37</span><span class="level-icon">🔋</span><span class="level-name">Power bank (20,000 mAh)</span></div><div class="level-price">$65</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 38</span><span class="level-icon">💇</span><span class="level-name">Wig (synthetic)</span></div><div class="level-price">$68</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 39</span><span class="level-icon">🎮</span><span class="level-name">Gaming controller (Xbox/PS)</span></div><div class="level-price">$70</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 40</span><span class="level-icon">🪅</span><span class="level-name">Large piñata (empty)</span></div><div class="level-price">$72</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 41</span><span class="level-icon">🦇</span><span class="level-name">Baseball bat (aluminum)</span></div><div class="level-price">$74</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 42</span><span class="level-icon">🩼</span><span class="level-name">Crutches (pair, aluminum)</span></div><div class="level-price">$76</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 43</span><span class="level-icon">🎒</span><span class="level-name">Backpack (urban casual)</span></div><div class="level-price">$80</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 44</span><span class="level-icon">👠</span><span class="level-name">High heels</span></div><div class="level-price">$85</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 45</span><span class="level-icon">🌐</span><span class="level-name">Good Wi-Fi 6 router</span></div><div class="level-price">$88</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 46</span><span class="level-icon">👞</span><span class="level-name">Men's dress shoes (leather)</span></div><div class="level-price">$92</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 47</span><span class="level-icon">⚽</span><span class="level-name">Soccer ball (official/original)</span></div><div class="level-price">$95</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 48</span><span class="level-icon">🧯</span><span class="level-name">Fire extinguisher (car/home)</span></div><div class="level-price">$100</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 49</span><span class="level-icon">👟</span><span class="level-name">Sneakers (classic branded)</span></div><div class="level-price">$105</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 50</span><span class="level-icon">🥤</span><span class="level-name">Protein powder (2 kg tub)</span></div><div class="level-price">$110</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 51</span><span class="level-icon">🚁</span><span class="level-name">RC helicopter (remote control)</span></div><div class="level-price">$115</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 52</span><span class="level-icon">🔮</span><span class="level-name">Sex toy / Vibrator (high quality)</span></div><div class="level-price">$120</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 53</span><span class="level-icon">🔊</span><span class="level-name">Bluetooth speaker (JBL Flip level)</span></div><div class="level-price">$125</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 54</span><span class="level-icon">🥊</span><span class="level-name">Boxing gloves (leather)</span></div><div class="level-price">$130</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 55</span><span class="level-icon">💐</span><span class="level-name">Bouquet of flowers (large rose bouquet)</span></div><div class="level-price">$135</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 56</span><span class="level-icon">🛼</span><span class="level-name">Good inline skates / Rollerblades</span></div><div class="level-price">$140</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 57</span><span class="level-icon">🍌</span><span class="level-name">Banana costume (mascot suit)</span></div><div class="level-price">$145</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 58</span><span class="level-icon">📷</span><span class="level-name">Webcam (streaming, 1080p)</span></div><div class="level-price">$150</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 59</span><span class="level-icon">🏋️</span><span class="level-name">Kettlebell (24 kg)</span></div><div class="level-price">$155</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 60</span><span class="level-icon">🇲🇩</span><span class="level-name">Good ice skates</span></div><div class="level-price">$160</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 61</span><span class="level-icon">📺</span><span class="level-name">YouTube Premium (1-year subscription)</span></div><div class="level-price">$165</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 62</span><span class="level-icon">⌨️</span><span class="level-name">Mechanical keyboard</span></div><div class="level-price">$170</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 63</span><span class="level-icon">🎧</span><span class="level-name">Wireless over-ear headphones</span></div><div class="level-price">$180</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 64</span><span class="level-icon">🎙️</span><span class="level-name">USB microphone (streaming)</span></div><div class="level-price">$190</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 65</span><span class="level-icon">🧱</span><span class="level-name">LEGO set (medium-large)</span></div><div class="level-price">$200</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 66</span><span class="level-icon">🐠</span><span class="level-name">Fish tank / Aquarium (50-60L with filter)</span></div><div class="level-price">$220</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 67</span><span class="level-icon">📖</span><span class="level-name">E-reader (Kindle)</span></div><div class="level-price">$240</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 68</span><span class="level-icon">🖥️</span><span class="level-name">24-inch gaming monitor (IPS)</span></div><div class="level-price">$250</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 69</span><span class="level-icon">🐊</span><span class="level-name">Small crocodile (caiman)</span></div><div class="level-price">$265</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 70</span><span class="level-icon">📺</span><span class="level-name">32-inch Smart TV (budget)</span></div><div class="level-price">$280</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 71</span><span class="level-icon">💺</span><span class="level-name">Gaming chair</span></div><div class="level-price">$300</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 72</span><span class="level-icon">🏋️‍♂️</span><span class="level-name">Dumbbell set (30-40 kg total)</span></div><div class="level-price">$320</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 73</span><span class="level-icon">❄️</span><span class="level-name">Air conditioner (portable/window)</span></div><div class="level-price">$340</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 74</span><span class="level-icon">🎈</span><span class="level-name">Inflatable sex doll</span></div><div class="level-price">$350</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 75</span><span class="level-icon">🚗</span><span class="level-name">Kids ride-on electric car</span></div><div class="level-price">$360</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 76</span><span class="level-icon">🚜</span><span class="level-name">Lawn mower (cordless/gas)</span></div><div class="level-price">$375</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 77</span><span class="level-icon">🧹</span><span class="level-name">Robot vacuum cleaner (basic)</span></div><div class="level-price">$390</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 78</span><span class="level-icon">🐈</span><span class="level-name">Pedigree cat</span></div><div class="level-price">$400</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 79</span><span class="level-icon">📱</span><span class="level-name">Entry-level smartphone (Android)</span></div><div class="level-price">$415</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 80</span><span class="level-icon">🎮</span><span class="level-name">Xbox Series S</span></div><div class="level-price">$435</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 81</span><span class="level-icon">🧺</span><span class="level-name">Washing machine</span></div><div class="level-price">$455</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 82</span><span class="level-icon">🤖</span><span class="level-name">Full-size Iron Man helmet (replica)</span></div><div class="level-price">$480</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 83</span><span class="level-icon">🐕</span><span class="level-name">Pedigree dog</span></div><div class="level-price">$500</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 84</span><span class="level-icon">🕹️</span><span class="level-name">PlayStation 5 Digital</span></div><div class="level-price">$515</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 85</span><span class="level-icon">🛸</span><span class="level-name">Beginner drone (DJI Mini level)</span></div><div class="level-price">$535</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 86</span><span class="level-icon">🍏</span><span class="level-name">iPad (base model)</span></div><div class="level-price">$550</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 87</span><span class="level-icon">🧊</span><span class="level-name">Compact refrigerator (mini-bar)</span></div><div class="level-price">$580</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 88</span><span class="level-icon">📡</span><span class="level-name">Portable Starlink Mini antenna</span></div><div class="level-price">$600</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 89</span><span class="level-icon">🏎️</span><span class="level-name">Gaming steering wheel and pedals</span></div><div class="level-price">$620</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 90</span><span class="level-icon">⌚</span><span class="level-name">Smartwatch (Apple Watch / Galaxy)</span></div><div class="level-price">$640</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 91</span><span class="level-icon">☕</span><span class="level-name">Automatic espresso machine</span></div><div class="level-price">$660</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 92</span><span class="level-icon">🽿</span><span class="level-name">VR headset (standalone Meta Quest)</span></div><div class="level-price">$680</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 93</span><span class="level-icon">🦜</span><span class="level-name">Parrot (large, e.g., Cockatiel)</span></div><div class="level-price">$710</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 94</span><span class="level-icon">🚲</span><span class="level-name">Electric unicycle (EUC)</span></div><div class="level-price">$750</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 95</span><span class="level-icon">🛴</span><span class="level-name">Electric scooter (urban)</span></div><div class="level-price">$780</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 96</span><span class="level-icon">🖥️</span><span class="level-name">Mac Mini (base configuration)</span></div><div class="level-price">$810</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 97</span><span class="level-icon">🚲</span><span class="level-name">Bicycle (urban/mountain casual)</span></div><div class="level-price">$850</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 98</span><span class="level-icon">🛞</span><span class="level-name">Michelin tires (set of 4)</span></div><div class="level-price">$900</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 99</span><span class="level-icon">🖨️</span><span class="level-name">3D printer (home use)</span></div><div class="level-price">$950</div></div>
            <div class="level-item"><div class="level-left"><span class="level-num">LVL 100</span><span class="level-icon">🖥️</span><span class="level-name">Entry-level gaming PC (RTX 4060)</span></div><div class="level-price">$1000</div></div>
        </div>

        <div class="leaderboard-title">
            <i class="fa-solid fa-crown" style="color: #fbbf24;"></i> TOP CHALLENGERS
        </div>
        
        <div class="pedestal-container">
            <div class="pedestal-rank rank-2">
                <div class="donator-name">Waiting...</div>
                <div class="block">
                    <span>2</span>
                    <span class="block-amount">-</span>
                </div>
            </div>
            <div class="pedestal-rank rank-1">
                <i class="fa-solid fa-crown crown"></i>
                <div class="donator-name">Waiting...</div>
                <div class="block">
                    <span>1</span>
                    <span class="block-amount">-</span>
                </div>
            </div>
            <div class="pedestal-rank rank-3">
                <div class="donator-name">Waiting...</div>
                <div class="block">
                    <span>3</span>
                    <span class="block-amount">-</span>
                </div>
            </div>
        </div>

    </div>

    <script>
        // Задаем прогресс вручную (в долларах от 0 до 1000)
        let currentProgressValue = 0; 

        function updateProgress(value) {
            const maxVal = 1000;
            let percent = (value / maxVal) * 100;
            if(percent > 100) percent = 100;
            
            document.getElementById('progress-indicator').style.width = percent + '%';
            document.getElementById('pct-label').innerText = Math.round(percent) + '%';
        }
        updateProgress(currentProgressValue);

        // ЖЕЛЕЗОБЕТОННЫЙ ДВИЖОК КОПИРОВАНИЯ С СУПЕР-АНИМАЦИЕЙ КНОПОК
        document.querySelectorAll('.crypto-btn').forEach(button => {
            button.addEventListener('click', () => {
                const address = button.getAttribute('data-addr');
                const spanText = button.querySelector('span');
                const originalText = spanText.innerText;
                const hiddenInput = document.getElementById('hidden-copy-input');
                
                // Универсальное копирование через невидимое поле ввода
                hiddenInput.value = address;
                hiddenInput.select();
                hiddenInput.setSelectionRange(0, 99999); // Для мобильных телефонов
                
                try {
                    document.execCommand('copy');
                    
                    // Запуск Анимации на самой кнопке
                    button.classList.add('copied');
                    spanText.innerText = "COPIED!";
                    
                    // Возвращаем все назад через 1.5 секунды
                    setTimeout(() => {
                        button.classList.remove('copied');
                        spanText.innerText = originalText;
                    }, 1500);

                } catch (err) {
                    console.error('Fallback copy method failed', err);
                }
            });
        });
    </script>
</body>
</html>
