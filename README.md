<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Bristol Business Tycoon!</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&display=swap');

        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin: 0;
            padding: 10px;
            background-color: #b0c4de;
        }
        .business-status {
            margin-bottom: 10px;
            text-align: center;
            border: 3px solid #1e3c72;
            padding: 10px;
            background-color: #f0f8ff;
            border-radius: 10px;
            max-width: 90%;
            box-sizing: border-box;
        }
        .buttons-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
            max-width: 90%;
        }
        button, select {
            margin: 5px;
            padding: 15px;
            font-size: 16px;
            border: 2px solid #2e8b57;
            border-radius: 50%;
            background-color: #20b2aa;
            color: #ffffff;
            cursor: pointer;
            box-shadow: 2px 2px 10px #555;
            transition: transform 0.2s, background-color 0.3s;
            max-width: 200px;
        }
        button:hover, select:hover {
            background-color: #3cb371;
            transform: scale(1.1);
        }
        h1 {
            font-family: 'Playfair Display', serif;
            color: #1e90ff;
            text-shadow: 2px 2px #000;
            font-size: 2em;
            letter-spacing: 1px;
            font-weight: bold;
            text-align: center;
        }
        .rules {
            border: 3px dashed #1e3c72;
            padding: 15px;
            margin-top: 20px;
            background-color: #e6e6fa;
            border-radius: 10px;
            max-width: 90%;
            box-sizing: border-box;
        }
        .tycoon-rank {
            font-weight: bold;
            font-size: 1.5em;
            color: #ff6347;
            text-shadow: 2px 2px 4px #000;
            letter-spacing: 1px;
        }
        .money-display {
            font-size: 1.8em;
            color: #ffd700;
            font-weight: bold;
            text-shadow: 1px 1px 3px #000;
            padding: 10px;
            background-color: #f0f8ff;
            border: 3px solid #2e8b57;
            border-radius: 10px;
            margin-top: 10px;
        }
        .end-game {
            text-align: center;
            font-size: 1.5em;
            color: red;
            margin-top: 30px;
        }
        .income-breakdown {
            border: 2px solid #1e3c72;
            padding: 10px;
            margin-top: 10px;
            background-color: #f5deb3;
            border-radius: 10px;
            max-width: 90%;
            text-align: left;
            box-sizing: border-box;
        }
    </style>
</head>
<body>
    <h1>Bristol Business Tycoon!</h1>
    <div class="business-status">
        <p>Income per Second: $<span id="incomePerSecond">0</span></p>
        <p>Cans Collected: <span id="cans">0</span></p>
        <p>Food Trucks Owned: <span id="smallBusinesses">0</span> ($<span id="smallBusinessesIncome">0</span> per second)</p>
        <p>Local Shops Owned: <span id="midVentures">0</span> ($<span id="midVenturesIncome">0</span> per second)</p>
        <p>Landmarks Owned: <span id="highVentures">0</span> ($<span id="highVenturesIncome">0</span> per second)</p>
        <p>Restaurants Owned: <span id="restaurants">0</span> ($<span id="restaurantsIncome">0</span> per second)</p>
        <p>Gas Stations Owned: <span id="gasStations">0</span> ($<span id="gasStationsIncome">0</span> per second)</p>
        <p>Grocery Stores Owned: <span id="groceryStores">0</span> ($<span id="groceryStoresIncome">0</span> per second)</p>
        <p class="money-display">Money: $<span id="money">0</span></p>
        <p>Tycoon Rank: <span id="tycoonRank" class="tycoon-rank">Bristol Bum Bottle Collector</span></p>
    </div>

    <div class="buttons-container">
        <button onclick="collectCans()">🛒 Collect Cans</button>
        <button onclick="sellCans()">💰 Sell Cans</button>
        <button onclick="investInSmallBusiness()">🚚 Invest in "Riverside Food Truck" ($200)</button>
        <button onclick="buyRestaurant()">🍽️ Buy "Waffle House" ($5000)</button>
        <button onclick="buyGasStation()">⛽ Buy "Middle St Mobil Station" ($10000)</button>
        <button onclick="buyGroceryStore()">🛒 Buy "Stop & Shop Bristol" ($20000)</button>
        <button onclick="buyLocalShop()">🏪 Buy "Bristol Boutique Shop" ($25000)</button>
        <button onclick="buyLandmark()">🏛️ Buy "Bell City Landmark" ($50000)</button>
    </div>

    <select id="upgrade-options" onchange="buyUpgrade()">
        <option value="">-- Buy Upgrade --</option>
        <option value="cart">🛒 Buy a Better Cart ($50)</option>
        <option value="flyerDistributor">📄 Become Flyer Distributor ($200)</option>
        <option value="hireManager">👨‍💼 Hire Store Manager ($500)</option>
        <option value="investInFoodTruck">🚚 Invest in "Hidden Cafe" Food Truck ($1500)</option>
        <option value="buyCoffeeShop">☕ Buy "Pure Foods" Coffee Shop ($5000)</option>
        <option value="openConstruction">🏗️ Open "Broad Street Builders" Construction ($10000)</option>
        <option value="buyRealEstate">🏢 Invest in "Price Chopper" Real Estate ($20000)</option>
        <option value="buySportsBar">🍻 Buy "Sportys" Sports Bar ($30000)</option>
        <option value="expandFranchise">🏪 Expand "GameTime Grille" Franchise ($50000)</option>
        <option value="buyLuxuryRestaurant">🥂 Buy "Cafe Real" Luxury Restaurant ($100000)</option>
        <option value="investInBristolMall">🏬 Invest in "Bristol Mall" ($500000)</option>
        <option value="becomePolitician">👔 Become Local Politician ($1000000)</option>
    </select>

    <div class="rules">
        <h2>Game Rule Book & Directions</h2>
        <p>Welcome to Bristol Business Tycoon! Here is how you play:</p>
        <ul>
            <li>Start with humble beginnings as a Bristol Bum Bottle Collector and earn money to invest in businesses around Bristol.</li>
            <li>Use your earnings to buy upgrades, invest in businesses, and expand your empire!</li>
            <li>Buy local restaurants, gas stations, grocery stores, and more to grow your influence and wealth.</li>
            <li>Face random setbacks and opportunities—like getting arrested or receiving government grants!</li>
            <li>Your goal is to become the ultimate business tycoon by reaching the highest tycoon rank!</li>
        </ul>
        <h3>Setbacks:</h3>
        <ul>
            <li><strong>Fraud Jail Time:</strong> Spend too much money too fast and you'll go to jail for fraud, pausing your income for 30 seconds!</li>
            <li><strong>Bankruptcy Reversal:</strong> If your money drops to zero, a random building you own will be taken away as a penalty.</li>
        </ul>
        <h3>Tycoon Ranks:</h3>
        <p>Your tycoon rank will change as you earn more money and expand your empire. Here are the different titles you can achieve:</p>
        <ul>
            <li><strong>Bristol Bum Bottle Collector</strong> - Starting rank</li>
            <li><strong>Dive Bar Bartender</strong> - Reach $1,000</li>
            <li><strong>Bristol Small Biz Buff</strong> - Reach $10,000</li>
            <li><strong>Local Hotshot Mogul</strong> - Reach $50,000</li>
            <li><strong>Suburban Property Pioneer</strong> - Reach $200,000</li>
            <li><strong>Bell City Business Boss</strong> - Reach $1,000,000</li>
            <li><strong>Master of Bristol Ventures</strong> - Reach $10,000,000</li>
            <li><strong>The Bristol Baron</strong> - Reach $100,000,000</li>
            <li><strong>Mr. Bristol</strong> - Reach $100,000,000,000,000 - You run this town!</li>
        </ul>
        <p>Each rank comes with its own unique rewards and challenges, pushing you to expand and automate your empire!</p>
        <h3>Directions:</h3>
        <p>Click the buttons to collect resources and sell them for money. Use the dropdown to buy upgrades to increase your productivity and grow your empire.</p>
        <p>The game continues indefinitely, with each milestone becoming progressively harder to reach, but also offering greater rewards.</p>
    </div>

    <script>
        let cans = 0;
        let smallBusinesses = 0;
        let smallBusinessIncome = 0;
        let restaurants = 0;
        let gasStations = 0;
        let gasStationIncome = 0;
        let groceryStores = 0;
        let groceryStoreIncome = 0;
        let localShops = 0;
        let localShopIncome = 0;
        let landmarks = 0;
        let landmarkIncome = 0;
        let money = 0;
        let tycoonRank = "Bristol Bum Bottle Collector";
        let jailTimeout = null;

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

        // Upgrades effect variables
        let canCollectionRate = 5;
        let canValue = 0.05;

        function collectCans() {
            cans += canCollectionRate;
            updateBusinessStatus();
        }

        function sellCans() {
            if (cans > 0) {
                money += cans * canValue;
                cans = 0;
                checkForSetbacks();
                updateBusinessStatus();
            } else {
                alert("No cans to sell!");
            }
        }

        function investInSmallBusiness() {
            if (money >= costs.smallBusinessCost) {
                smallBusinesses++;
                money -= costs.smallBusinessCost;
                costs.smallBusinessCost = Math.floor(costs.smallBusinessCost * 1.15);
                smallBusinessIncome += 10;
                alert('Congratulations! You have just invested in a food truck: Riverside Food Truck! This now generates passive income.');
                updateBusinessStatus();
            } else {
                alert("Not enough money to invest in a small business!");
            }
        }

        function buyLocalShop() {
            if (money >= costs.localShopCost) {
                localShops++;
                money -= costs.localShopCost;
                costs.localShopCost = Math.floor(costs.localShopCost * 1.2);
                localShopIncome += 30;
                alert('Congratulations! You have just purchased a Bristol Boutique Shop! Generating more passive income.');
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a local shop!");
            }
        }

        function buyLandmark() {
            if (money >= costs.landmarkCost) {
                landmarks++;
                money -= costs.landmarkCost;
                costs.landmarkCost = Math.floor(costs.landmarkCost * 1.25);
                landmarkIncome += 75;
                alert('Congratulations! You have just bought a landmark: Bell City Landmark! Significant income boost.');
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a landmark!");
            }
        }

        function checkForSetbacks() {
            if (money <= 0) {
                // Randomly take away a building as a setback
                if (smallBusinesses > 0) {
                    smallBusinesses--;
                    alert("SETBACK: You've gone bankrupt and lost a food truck!");
                } else if (localShops > 0) {
                    localShops--;
                    alert("SETBACK: You've gone bankrupt and lost a local shop!");
                } else if (restaurants > 0) {
                    restaurants--;
                    alert("SETBACK: You've gone bankrupt and lost a restaurant!");
                } else {
                    alert("SETBACK: You've hit rock bottom. Try collecting more cans to recover!");
                }
                updateBusinessStatus();
            }

            // Fraud Jail Time
            if (money < 0 && !jailTimeout) {
                alert("FRAUD ALERT: You spent too much money too fast! You're going to jail for 30 seconds.");
                pauseIncome();
                jailTimeout = setTimeout(resumeIncome, 30000);
            }
        }

        function pauseIncome() {
            clearInterval(incomeInterval);
        }

        function resumeIncome() {
            incomeInterval = setInterval(automateIncome, 1000);
            jailTimeout = null;
        }

        function updateBusinessStatus() {
            document.getElementById("cans").innerText = cans;
            document.getElementById("smallBusinesses").innerText = smallBusinesses;
            document.getElementById("smallBusinessesIncome").innerText = (smallBusinesses * 10).toFixed(2);
            document.getElementById("midVentures").innerText = localShops;
            document.getElementById("midVenturesIncome").innerText = (localShops * 30).toFixed(2);
            document.getElementById("highVentures").innerText = landmarks;
            document.getElementById("highVenturesIncome").innerText = (landmarks * 75).toFixed(2);
            document.getElementById("restaurants").innerText = restaurants;
            document.getElementById("restaurantsIncome").innerText = (restaurants * 50).toFixed(2);
            document.getElementById("gasStations").innerText = gasStations;
            document.getElementById("gasStationsIncome").innerText = (gasStations * 20).toFixed(2);
            document.getElementById("groceryStores").innerText = groceryStores;
            document.getElementById("groceryStoresIncome").innerText = (groceryStores * 100).toFixed(2);
            document.getElementById("money").innerText = money.toFixed(2);
            updateTycoonRank();
        }

        function updateTycoonRank() {
            if (money >= 100000000000000) {
                tycoonRank = "Mr. Bristol - You run this town!";
                alert("Great Job, YOU ARE MR BRISTOL!");
            } else if (money >= 100000000) {
                tycoonRank = "The Bristol Baron";
            } else if (money >= 10000000) {
                tycoonRank = "Master of Bristol Ventures";
            } else if (money >= 1000000) {
                tycoonRank = "Bell City Business Boss";
            } else if (money >= 200000) {
                tycoonRank = "Suburban Property Pioneer";
            } else if (money >= 50000) {
                tycoonRank = "Local Hotshot Mogul";
            } else if (money >= 10000) {
                tycoonRank = "Bristol Small Biz Buff";
            } else if (money >= 1000) {
                tycoonRank = "Dive Bar Bartender";
            } else {
                tycoonRank = "Bristol Bum Bottle Collector";
            }
            document.getElementById("tycoonRank").innerText = tycoonRank;
        }

        // Automate passive income every second
        let incomeInterval = setInterval(automateIncome, 1000);

        function automateIncome() {
            let incomePerSecond = smallBusinessIncome + gasStationIncome + groceryStoreIncome + localShopIncome + landmarkIncome;
            money += incomePerSecond;
            document.getElementById("incomePerSecond").innerText = incomePerSecond.toFixed(2);
            updateBusinessStatus();
        }
    </script>
</body>
</html>
