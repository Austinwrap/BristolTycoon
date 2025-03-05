
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Bristol Business Tycoon</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Bubblegum+Sans&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Bubblegum Sans', cursive;
            background: linear-gradient(135deg, #1e1e1e, #ff4757, #4ecdc4);
            color: #222; /* Darker text color */
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Particle & Confetti Background */
        #particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        /* Entry Page */
        #entry-page {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://images.unsplash.com/photo-1593642634367-d91a5f9e1c38?auto=format&fit=crop&w=1350&q=80') no-repeat center/cover;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            transition: transform 1s ease;
        }

        #entry-page h1 {
            font-size: 6em;
            color: #ffd700;
            text-shadow: 0 0 20px #ff4757, 0 0 40px #4ecdc4;
            animation: neon-flicker 1.5s infinite;
        }

        #enter-btn {
            font-size: 2.5em;
            padding: 30px 60px;
            background: radial-gradient(circle, #ff9f1c, #ff4757);
            color: #fff;
            border: 6px solid #ffd700;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 0 20px #ff4757;
            transition: all 0.4s ease;
        }

        #enter-btn:hover {
            transform: scale(1.3) rotate(5deg);
            box-shadow: 0 0 30px #ff4757, 0 0 50px #4ecdc4;
            background: radial-gradient(circle, #ff4757, #ff9f1c);
        }

        /* Main Game */
        .container {
            max-width: 100%;
            padding: 20px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        h1 {
            font-size: 4em;
            color: #ffd700;
            text-shadow: 0 0 15px #ff4757, 0 0 30px #4ecdc4;
            text-align: center;
            margin-bottom: 25px;
            animation: neon-pulse 2s infinite;
        }

        .business-status {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 30px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 0 25px rgba(255, 71, 87, 0.7);
            border: 4px solid #ffd700;
            animation: bounce-glow 2s infinite ease-in-out;
        }

        .business-status p {
            font-size: 1.5em;
            margin: 15px 0;
            text-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
        }

        .money-display {
            font-size: 3em;
            color: #ffd700;
            background: rgba(0, 0, 0, 0.6);
            padding: 20px;
            border-radius: 25px;
            margin-top: 20px;
            text-align: center;
            box-shadow: 0 0 20px #ff9f1c;
        }

        .tycoon-rank {
            font-size: 2.5em;
            color: #ff4757;
            text-shadow: 0 0 10px #ff4757, 0 0 20px #ffd700;
            animation: rank-glow 1.5s infinite;
        }

        /* Bubble Buttons */
        .buttons-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
            gap: 20px;
            margin-bottom: 25px;
        }

        button, select {
            font-size: 1.3em;
            padding: 25px;
            background: radial-gradient(circle, #ff9f1c, #ff4757);
            color: #fff;
            border: 5px solid #ffd700;
            border-radius: 50%;
            cursor: pointer;
            box-shadow: 0 0 15px #ff4757, 0 0 25px #4ecdc4;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            text-align: center;
            animation: bubble-pop 2s infinite ease-in-out;
        }

        button:hover, select:hover {
            transform: scale(1.25) rotate(10deg);
            box-shadow: 0 0 30px #ff4757, 0 0 50px #4ecdc4;
            background: radial-gradient(circle, #ff4757, #ff9f1c);
        }

        button:active {
            transform: scale(0.9);
            box-shadow: 0 0 10px #ff4757;
        }

        select {
            background: radial-gradient(circle, #4ecdc4, #45b7d1);
            width: 100%;
            max-width: 340px;
            margin: 0 auto;
            display: block;
        }

        /* Directions Pop-out */
        .directions-btn {
            position: fixed;
            bottom: 25px;
            right: 25px;
            font-size: 2em;
            padding: 20px;
            background: #45b7d1;
            border-radius: 50%;
            box-shadow: 0 0 15px #4ecdc4;
            z-index: 10;
        }

        .rules {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            background: rgba(255, 255, 255, 0.95);
            color: #222;
            border-radius: 40px;
            padding: 30px;
            max-width: 95%;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 0 40px rgba(255, 71, 87, 0.8);
            transition: transform 0.5s ease;
            z-index: 20;
            display: none;
        }

        .rules.active {
            transform: translate(-50%, -50%) scale(1);
            display: block;
        }

        .rules h2 {
            color: #ff4757;
            margin-bottom: 20px;
            font-size: 2.5em;
            text-shadow: 0 0 10px #ff4757;
        }

        .rules ul {
            list-style-type: none;
            padding-left: 30px;
        }

        .rules li {
            margin: 15px 0;
            font-size: 1.5em;
            position: relative;
        }

        .rules li:before {
            content: "🎊";
            position: absolute;
            left: -30px;
        }

        /* Bristol Elements */
        .bristol-decor {
            position: absolute;
            pointer-events: none;
            opacity: 0.4;
            animation: spin-float 5s infinite ease-in-out;
        }

        #clock-tower { top: 30px; left: 30px; font-size: 5em; }
        #mum-festival { bottom: 30px; right: 30px; font-size: 4.5em; }
        #espn { top: 60%; left: 20px; font-size: 4em; }
        #lake { bottom: 60px; left: 40px; font-size: 4em; }
        #mum-parade { top: 20%; right: 20px; font-size: 3.5em; }

        .reflection-note {
            background: rgba(255, 215, 0, 0.4);
            border-radius: 30px;
            padding: 30px;
            margin-top: 25px;
            text-align: center;
            box-shadow: 0 0 30px #ffd700;
            animation: explode-in 0.7s ease;
        }

        /* Animations */
        @keyframes neon-flicker {
            0%, 100% { text-shadow: 0 0 20px #ff4757, 0 0 40px #4ecdc4; }
            50% { text-shadow: 0 0 10px #ff4757, 0 0 20px #4ecdc4; }
        }

        @keyframes neon-pulse {
            0%, 100% { text-shadow: 0 0 15px #ff4757, 0 0 30px #4ecdc4; }
            50% { text-shadow: 0 0 25px #ff4757, 0 0 50px #4ecdc4; }
        }

        @keyframes rank-glow {
            0%, 100% { text-shadow: 0 0 10px #ff4757, 0 0 20px #ffd700; }
            50% { text-shadow: 0 0 20px #ff4757, 0 0 40px #ffd700; }
        }

        @keyframes bounce-glow {
            0%, 100% { transform: translateY(0); box-shadow: 0 0 25px rgba(255, 71, 87, 0.7); }
            50% { transform: translateY(-20px); box-shadow: 0 0 40px rgba(255, 71, 87, 1); }
        }

        @keyframes bubble-pop {
            0%, 100% { transform: translateY(0) rotate(0); }
            25% { transform: translateY(-10px) rotate(5deg); }
            75% { transform: translateY(10px) rotate(-5deg); }
        }

        @keyframes spin-float {
            0%, 100% { transform: translateY(0) rotate(0); }
            50% { transform: translateY(-25px) rotate(180deg); }
        }

        @keyframes explode-in {
            0% { transform: scale(0) rotate(0); opacity: 0; }
            100% { transform: scale(1) rotate(360deg); opacity: 1; }
        }

        /* iPhone Optimization */
        @media (max-width: 430px) {
            h1 { font-size: 2.8em; }
            .business-status p { font-size: 1.2em; }
            .money-display { font-size: 2em; }
            .tycoon-rank { font-size: 1.8em; }
            button, select { 
                padding: 18px; 
                font-size: 1.1em; 
                min-width: 110px; 
            }
            .buttons-container { gap: 12px; }
            #entry-page h1 { font-size: 4em; }
            #enter-btn { font-size: 1.8em; padding: 25px 50px; }
            .rules { padding: 20px; }
            .rules h2 { font-size: 2em; }
            .rules li { font-size: 1.2em; }
            .bristol-decor { font-size: 2.5em !important; }
        }
    </style>
</head>
<body>
    <!-- Particle & Confetti Background -->
    <canvas id="particles"></canvas>

    <!-- Entry Page -->
    <div id="entry-page">
        <h1>Bristol Tycoon Bash!</h1>
        <button id="enter-btn">🎉 Let’s Roll!</button>
    </div>

    <!-- Main Game -->
    <div class="container">
        <h1>Bristol Business Tycoon</h1>
        <div class="business-status">
            <p>💸 Income/Sec: $<span id="incomePerSecond">0</span></p>
            <p>🥫 Cans: <span id="cans">0</span></p>
            <p>🚚 Mum Trucks: <span id="smallBusinesses">0</span> ($<span id="smallBusinessesIncome">0</span>/s)</p>
            <p>🏪 Clock Shops: <span id="midVentures">0</span> ($<span id="midVenturesIncome">0</span>/s)</p>
            <p>🕰️ Towers: <span id="highVentures">0</span> ($<span id="highVenturesIncome">0</span>/s)</p>
            <p>🍔 Eats: <span id="restaurants">0</span> ($<span id="restaurantsIncome">0</span>/s)</p>
            <p>⛽ Fuel: <span id="gasStations">0</span> ($<span id="gasStationsIncome">0</span>/s)</p>
            <p>🛒 Choppers: <span id="groceryStores">0</span> ($<span id="groceryStoresIncome">0</span>/s)</p>
            <p class="money-display">💰 $<span id="money">0</span></p>
            <p>Rank: <span id="tycoonRank" class="tycoon-rank">Bristol Bum</span></p>
        </div>

        <div class="buttons-container">
            <button onclick="collectCans()">🥫 Snag Cans</button>
            <button onclick="sellCans()">💵 Cash Out</button>
            <button onclick="investInSmallBusiness()">🚚 Mum Truck ($200)</button>
            <button onclick="buyRestaurant()">🍔 Compounce Eats ($5000)</button>
            <button onclick="buyGasStation()">⛽ Bristol Fuel ($10000)</button>
            <button onclick="buyGroceryStore()">🛒 Price Chopper ($20000)</button>
            <button onclick="buyLocalShop()">🏪 Clock Shop ($25000)</button>
            <button onclick="buyLandmark()">🕰️ Clock Tower ($50000)</button>
        </div>

        <select id="upgrade-options" onchange="buyUpgrade()">
            <option value="">-- Boost It! --</option>
            <option value="cart">🥫 Neon Cart ($50)</option>
            <option value="flyerDistributor">📣 Mum Flyer ($200)</option>
            <option value="hireManager">👨‍💼 Boss Man ($500)</option>
            <option value="investInFoodTruck">🚚 Cafe Truck ($1500)</option>
            <option value="buyCoffeeShop">☕ Bristol Brew ($5000)</option>
            <option value="openConstruction">🏗️ Broad St Build ($10000)</option>
            <option value="buyRealEstate">🏢 Downtown Lot ($20000)</option>
            <option value="buySportsBar">🍻 ESPN Pub ($30000)</option>
            <option value="expandFranchise">🏪 GameTime ($50000)</option>
            <option value="buyLuxuryRestaurant">🥂 Cafe Real ($100000)</option>
            <option value="investInBristolMall">🏬 Bristol Mall ($500000)</option>
            <option value="becomePolitician">👑 Bristol Mayor ($1000000)</option>
        </select>

        <!-- Bristol Decorations -->
        <span class="bristol-decor" id="clock-tower">🕰️</span>
        <span class="bristol-decor" id="mum-festival">🌸</span>
        <span class="bristol-decor" id="espn">📺</span>
        <span class="bristol-decor" id="lake">🎢</span>
        <span class="bristol-decor" id="mum-parade">🎉</span>

        <!-- Directions -->
        <button class="directions-btn" onclick="toggleDirections()">📜</button>
        <div class="rules" id="rules">
            <h2>Bristol Tycoon Party!</h2>
            <p>Own Bristol, CT, with swagger!</p>
            <ul>
                <li>Snag cans like a pro.</li>
                <li>Cash out and buy the town!</li>
                <li>Dodge jail and flops.</li>
                <li>Hit "Mr. Bristol" with ∞ loot!</li>
            </ul>
            <h3>Ranks:</h3>
            <ul>
                <li>Bristol Bum - $0</li>
                <li>Bar Star - $1K</li>
                <li>Biz King - $10K</li>
                <li>Hotshot - $50K</li>
                <li>Land Lord - $200K</li>
                <li>Bell Boss - $1M</li>
                <li>Venture God - $10M</li>
                <li>Bristol Baron - $100M</li>
                <li>Mr. Bristol - $100T</li>
            </ul>
        </div>

        <div id="reflection" class="reflection-note" style="display: none;">
            <h3>You’re Mr. Bristol!</h3>
            <p>BOOM! You’ve ruled Bristol—cans to Clock Tower, it’s all yours. Throw a Mum Fest bash or take over the world next?</p>
        </div>
    </div>

    <script>
        // Confetti & Particle Effect
        const canvas = document.getElementById("particles");
        const ctx = canvas.getContext("2d");
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        let particles = [];

        class Particle {
            constructor(x = Math.random() * canvas.width, y = Math.random() * canvas.height) {
                this.x = x;
                this.y = y;
                this.size = Math.random() * 10 + 5;
                this.speedX = Math.random() * 3 - 1.5;
                this.speedY = Math.random() * 3 - 1.5;
                this.life = Math.random() * 60 + 30;
                this.color = `hsl(${Math.random() * 360}, 100%, 50%)`;
            }
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                this.life--;
                if (this.size > 0.5) this.size -= 0.1;
            }
            draw() {
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function handleParticles() {
            for (let i = 0; i < particles.length; i++) {
                particles[i].update();
                particles[i].draw();
                if (particles[i].life <= 0 || particles[i].size <= 0.5) {
                    particles.splice(i, 1);
                    i--;
                }
            }
        }

        function spawnParticles(x, y) {
            for (let i = 0; i < 20; i++) {
                particles.push(new Particle(x, y));
            }
        }

        setInterval(() => spawnParticles(Math.random() * canvas.width, Math.random() * canvas.height), 200);
        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            handleParticles();
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        // Game Logic
        let gameState = {
            cans: 0,
            money: 0,
            smallBusinesses: 0,
            smallBusinessIncome: 0,
            restaurants: 0,
            restaurantIncome: 0,
            gasStations: 0,
            gasStationIncome: 0,
            groceryStores: 0,
            groceryStoreIncome: 0,
            localShops: 0,
            localShopIncome: 0,
            landmarks: 0,
            landmarkIncome: 0,
            tycoonRank: "Bristol Bum",
            canCollectionRate: 5,
            canValue: 0.05,
            isJailed: false
        };

        const costs = {
            smallBusinessCost: 200,
            restaurantCost: 5000,
            gasStationCost: 10000,
            groceryStoreCost: 20000,
            localShopCost: 25000,
            landmarkCost: 50000,
            betterCartCost: 50,
            flyerDistributorCost: 200,
            hireManagerCost: 500,
            investInFoodTruckCost: 1500,
            buyCoffeeShopCost: 5000,
            openConstructionCost: 10000,
            buyRealEstateCost: 20000,
            buySportsBarCost: 30000,
            expandFranchiseCost: 50000,
            buyLuxuryRestaurantCost: 100000,
            investInBristolMallCost: 500000,
            becomePoliticianCost: 1000000
        };

        // Entry Page
        document.getElementById("enter-btn").addEventListener("click", (e) => {
            document.getElementById("entry-page").style.transform = "scale(0)";
            setTimeout(() => document.getElementById("entry-page").remove(), 1000);
            spawnParticles(e.clientX, e.clientY);
            playSound("https://www.soundjay.com/buttons/beep-01a.mp3");
        });

        // Directions
        function toggleDirections(e) {
            const rules = document.getElementById("rules");
            rules.classList.toggle("active");
            if (rules.classList.contains("active")) spawnParticles(window.innerWidth / 2, window.innerHeight / 2);
            playSound("https://www.soundjay.com/buttons/beep-02.mp3");
        }

        // Sound Function
        function playSound(url) {
            new Audio(url).play().catch(() => {});
        }

        function collectCans(e) {
            gameState.cans += gameState.canCollectionRate;
            updateUI();
            spawnParticles(e.clientX, e.clientY);
            playSound("https://www.soundjay.com/buttons/beep-07.mp3");
        }

        function sellCans(e) {
            if (gameState.cans > 0) {
                gameState.money += gameState.cans * gameState.canValue;
                gameState.cans = 0;
                checkSetbacks();
                updateUI();
                spawnParticles(e.clientX, e.clientY);
                playSound("https://www.soundjay.com/buttons/beep-08b.mp3");
            } else {
                alert("No cans, fam!");
            }
        }

        function investInSmallBusiness(e) {
            if (gameState.money >= costs.smallBusinessCost) {
                gameState.smallBusinesses++;
                gameState.money -= costs.smallBusinessCost;
                costs.smallBusinessCost = Math.floor(costs.smallBusinessCost * 1.15);
                gameState.smallBusinessIncome += 10;
                updateUI();
                spawnParticles(e.clientX, e.clientY);
                playSound("https://www.soundjay.com/buttons/beep-09.mp3");
            } else {
                alert("Broke vibes!");
            }
        }

        function buyRestaurant(e) {
            if (gameState.money >= costs.restaurantCost) {
                gameState.restaurants++;
                gameState.money -= costs.restaurantCost;
                costs.restaurantCost = Math.floor(costs.restaurantCost * 1.2);
                gameState.restaurantIncome += 50;
                updateUI();
                spawnParticles(e.clientX, e.clientY);
                playSound("https://www.soundjay.com/buttons/beep-10.mp3");
            } else {
                alert("Broke vibes!");
            }
        }

        function buyGasStation(e) {
            if (gameState.money >= costs.gasStationCost) {
                gameState.gasStations++;
                gameState.money -= costs.gasStationCost;
                costs.gasStationCost = Math.floor(costs.gasStationCost * 1.2);
                gameState.gasStationIncome += 20;
                updateUI();
                spawnParticles(e.clientX, e.clientY);
                playSound("https://www.soundjay.com/buttons/beep-11.mp3");
            } else {
                alert("Broke vibes!");
            }
        }

        function buyGroceryStore(e) {
            if (gameState.money >= costs.groceryStoreCost) {
                gameState.groceryStores++;
                gameState.money -= costs.groceryStoreCost;
                costs.groceryStoreCost = Math.floor(costs.groceryStoreCost * 1.2);
                gameState.groceryStoreIncome += 100;
                updateUI();
                spawnParticles(e.clientX, e.clientY);
                playSound("https://www.soundjay.com/buttons/beep-12.mp3");
            } else {
                alert("Broke vibes!");
            }
        }

        function buyLocalShop(e) {
            if (gameState.money >= costs.localShopCost) {
                gameState.localShops++;
                gameState.money -= costs.localShopCost;
                costs.localShopCost = Math.floor(costs.localShopCost * 1.2);
                gameState.localShopIncome += 30;
                updateUI();
                spawnParticles(e.clientX, e.clientY);
                playSound("https://www.soundjay.com/buttons/beep-13.mp3");
            } else {
                alert("Broke vibes!");
            }
        }

        function buyLandmark(e) {
            if (gameState.money >= costs.landmarkCost) {
                gameState.landmarks++;
                gameState.money -= costs.landmarkCost;
                costs.landmarkCost = Math.floor(costs.landmarkCost * 1.25);
                gameState.landmarkIncome += 75;
                updateUI();
                spawnParticles(e.clientX, e.clientY);
                playSound("https://www.soundjay.com/buttons/beep-14.mp3");
            } else {
                alert("Broke vibes!");
            }
        }

        function buyUpgrade() {
            const upgrade = document.getElementById("upgrade-options").value;
            if (!upgrade) return;

            const upgrades = {
                cart: { cost: costs.betterCartCost, action: () => gameState.canCollectionRate += 5 },
                flyerDistributor: { cost: costs.flyerDistributorCost, action: () => gameState.canValue += 0.05 },
                hireManager: { cost: costs.hireManagerCost, action: () => gameState.smallBusinessIncome += 5 },
                investInFoodTruck: { cost: costs.investInFoodTruckCost, action: () => gameState.smallBusinessIncome += 15 },
                buyCoffeeShop: { cost: costs.buyCoffeeShopCost, action: () => gameState.restaurantIncome += 20 },
                openConstruction: { cost: costs.openConstructionCost, action: () => gameState.landmarkIncome += 25 },
                buyRealEstate: { cost: costs.buyRealEstateCost, action: () => gameState.localShopIncome += 30 },
                buySportsBar: { cost: costs.buySportsBarCost, action: () => gameState.restaurantIncome += 40 },
                expandFranchise: { cost: costs.expandFranchiseCost, action: () => gameState.groceryStoreIncome += 50 },
                buyLuxuryRestaurant: { cost: costs.buyLuxuryRestaurantCost, action: () => gameState.restaurantIncome += 100 },
                investInBristolMall: { cost: costs.investInBristolMallCost, action: () => gameState.landmarkIncome += 200 },
                becomePolitician: { cost: costs.becomePoliticianCost, action: () => gameState.money += 1000000 }
            };

            if (gameState.money >= upgrades[upgrade].cost) {
                gameState.money -= upgrades[upgrade].cost;
                upgrades[upgrade].action();
                updateUI();
                spawnParticles(window.innerWidth / 2, window.innerHeight / 2);
                playSound("https://www.soundjay.com/buttons/beep-15.mp3");
            } else {
                alert("Broke vibes!");
            }
            document.getElementById("upgrade-options").value = "";
        }

        function checkSetbacks() {
            if (gameState.money < 0 && !gameState.isJailed) {
                alert("Busted! Jail for 30 secs!");
                gameState.isJailed = true;
                clearInterval(incomeInterval);
                setTimeout(() => {
                    gameState.isJailed = false;
                    incomeInterval = setInterval(automateIncome, 1000);
                }, 30000);
                playSound("https://www.soundjay.com/buttons/beep-16.mp3");
            } else if (gameState.money <= 0) {
                const assets = [
                    { count: gameState.smallBusinesses, type: "smallBusinesses", message: "Mum Truck gone!" },
                    { count: gameState.localShops, type: "localShops", message: "Clock Shop gone!" },
                    { count: gameState.restaurants, type: "restaurants", message: "Compounce Eats gone!" }
                ].filter(a => a.count > 0);

                if (assets.length > 0) {
                    const asset = assets[Math.floor(Math.random() * assets.length)];
                    gameState[asset.type]--;
                    alert(`Broke! ${asset.message}`);
                    playSound("https://www.soundjay.com/buttons/beep-17.mp3");
                }
            }
        }

        function updateUI() {
            document.getElementById("cans").innerText = gameState.cans;
            document.getElementById("smallBusinesses").innerText = gameState.smallBusinesses;
            document.getElementById("smallBusinessesIncome").innerText = gameState.smallBusinessIncome.toFixed(2);
            document.getElementById("midVentures").innerText = gameState.localShops;
            document.getElementById("midVenturesIncome").innerText = gameState.localShopIncome.toFixed(2);
            document.getElementById("highVentures").innerText = gameState.landmarks;
            document.getElementById("highVenturesIncome").innerText = gameState.landmarkIncome.toFixed(2);
            document.getElementById("restaurants").innerText = gameState.restaurants;
            document.getElementById("restaurantsIncome").innerText = gameState.restaurantIncome.toFixed(2);
            document.getElementById("gasStations").innerText = gameState.gasStations;
            document.getElementById("gasStationsIncome").innerText = gameState.gasStationIncome.toFixed(2);
            document.getElementById("groceryStores").innerText = gameState.groceryStores;
            document.getElementById("groceryStoresIncome").innerText = gameState.groceryStoreIncome.toFixed(2);
            document.getElementById("money").innerText = gameState.money === Infinity ? "∞" : gameState.money.toFixed(2);
            updateTycoonRank();
        }

        function updateTycoonRank() {
            const ranks = [
                { threshold: 100000000000000, title: "Mr. Bristol" },
                { threshold: 100000000, title: "Bristol Baron" },
                { threshold: 10000000, title: "Venture God" },
                { threshold: 1000000, title: "Bell Boss" },
                { threshold: 200000, title: "Land Lord" },
                { threshold: 50000, title: "Hotshot" },
                { threshold: 10000, title: "Biz King" },
                { threshold: 1000, title: "Bar Star" },
                { threshold: 0, title: "Bristol Bum" }
            ];

            for (const rank of ranks) {
                if (gameState.money >= rank.threshold) {
                    gameState.tycoonRank = rank.title;
                    if (rank.title === "Mr. Bristol") {
                        document.getElementById("reflection").style.display = "block";
                        gameState.money = Infinity;
                        clearInterval(incomeInterval);
                        spawnParticles(window.innerWidth / 2, window.innerHeight / 2);
                        playSound("https://www.soundjay.com/buttons/beep-18.mp3");
                    }
                    break;
                }
            }
            document.getElementById("tycoonRank").innerText = gameState.tycoonRank;
        }

        function automateIncome() {
            if (!gameState.isJailed) {
                const totalIncome = gameState.smallBusinessIncome + gameState.restaurantIncome + gameState.gasStationIncome + 
                                   gameState.groceryStoreIncome + gameState.localShopIncome + gameState.landmarkIncome;
                gameState.money += totalIncome;
                document.getElementById("incomePerSecond").innerText = totalIncome.toFixed(2);
                updateUI();
            }
        }

        let incomeInterval = setInterval(automateIncome, 1000);

        // Resize Canvas
        window.addEventListener("resize", () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        // Click/Tap Confetti
        document.querySelectorAll("button").forEach(btn => {
            btn.addEventListener("click", (e) => spawnParticles(e.clientX, e.clientY));
        });
    </script>
</body>
</html>
