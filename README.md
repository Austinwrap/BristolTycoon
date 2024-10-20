<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Bristol Business Tycoon</title>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin: 0;
            padding: 20px;
            background-color: #ffefd5; /* Light peach background */
        }
        .business-status {
            margin-bottom: 20px;
            text-align: center;
            border: 3px solid #8b4513; /* Brown border for urban feel */
            padding: 15px;
            background-color: #fff8dc; /* Cornsilk background for city charm */
            border-radius: 10px;
        }
        .buttons-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
        }
        button, select {
            margin: 10px;
            padding: 12px;
            font-size: 18px;
            border: 2px solid #228b22; /* Forest green border */
            border-radius: 8px;
            background-color: #98fb98; /* Pale green button color */
            color: #4b0082; /* Indigo text for contrast */
            cursor: pointer;
            box-shadow: 2px 2px 5px #888888;
        }
        button:hover, select:hover {
            background-color: #7cfc00; /* Light green for hover effect */
        }
        h1 {
            color: #6b8e23; /* Olive green for city theme */
            text-shadow: 2px 2px #fff;
            font-size: 3em;
            letter-spacing: 2px;
            text-transform: uppercase;
            font-weight: bold;
        }
        .rules {
            border: 3px dashed #8b4513;
            padding: 20px;
            margin-top: 20px;
            background-color: #f0e68c; /* Khaki background for rule book */
            border-radius: 10px;
        }
        .tycoon-rank {
            font-weight: bold;
            font-size: 2em;
            color: #ff4500; /* Orange red to make it stand out */
            text-shadow: 2px 2px 4px #000; /* Shadow for emphasis */
            letter-spacing: 1px;
        }
        .money-display {
            font-size: 2em;
            color: #ffd700; /* Gold color for importance */
            font-weight: bold;
            text-shadow: 1px 1px 3px #000;
            padding: 10px;
            background-color: #fff8dc;
            border: 3px solid #228b22;
            border-radius: 10px;
            margin-top: 15px;
        }
    </style>
</head>
<body>
    <h1>Bristol Business Tycoon</h1>
    <div class="business-status">
        <p>Can Collector Income: <span id="cans">0</span></p>
        <p>Small Businesses Owned: <span id="smallBusinesses">0</span></p>
        <p>Mid-Tier Ventures: <span id="midVentures">0</span></p>
        <p>High-Tier Ventures: <span id="highVentures">0</span></p>
        <p>Restaurants Owned: <span id="restaurants">0</span></p>
        <p>Gas Stations Owned: <span id="gasStations">0</span></p>
        <p>Grocery Stores Owned: <span id="groceryStores">0</span></p>
        <p class="money-display">Money: $<span id="money">0</span></p>
        <p>Tycoon Rank: <span id="tycoonRank" class="tycoon-rank">Homeless Can Collector</span></p>
    </div>

    <div class="buttons-container">
        <button onclick="collectCans()">🛒 Collect Cans</button>
        <button onclick="sellCans()">💰 Sell Cans</button>
        <button onclick="investInSmallBusiness()">🏪 Invest in Small Business</button>
        <button onclick="buyRestaurant()">🍽️ Buy Restaurant</button>
        <button onclick="buyGasStation()">⛽ Buy Gas Station</button>
        <button onclick="buyGroceryStore()">🛒 Buy Grocery Store</button>
    </div>

    <select id="upgrade-options" onchange="buyUpgrade()">
        <option value="">-- Buy Upgrade --</option>
        <option value="cart">🛒 Buy a Better Cart ($50)</option>
        <option value="flyerDistributor">📄 Become Flyer Distributor ($200)</option>
        <option value="hireManager">👨‍💼 Hire Store Manager ($500)</option>
        <option value="investInFoodTruck">🚚 Invest in Food Truck ($1500)</option>
        <option value="buyCoffeeShop">☕ Buy a Coffee Shop ($5000)</option>
        <option value="openConstruction">🏗️ Open "Best Build Co." Construction ($10000)</option>
        <option value="buyRealEstate">🏢 Invest in Real Estate ($20000)</option>
        <option value="buySportsBar">🍻 Buy Sports Bar ($30000)</option>
        <option value="expandFranchise">🏪 Expand Franchise ($50000)</option>
        <option value="buyLuxuryRestaurant">🥂 Buy Luxury Restaurant ($100000)</option>
        <option value="investInBristolMall">🏬 Invest in Bristol Mall ($500000)</option>
        <option value="becomePolitician">👔 Become Local Politician ($1000000)</option>
    </select>

    <div class="rules">
        <h2>Game Rule Book & Directions</h2>
        <p>Welcome to Bristol Business Tycoon! Here is how you play:</p>
        <ul>
            <li>Start with humble beginnings as a can collector and earn money to invest in businesses around Bristol.</li>
            <li>Use your earnings to buy upgrades, invest in businesses, and expand your empire!</li>
            <li>Buy local restaurants, gas stations, grocery stores, and more to grow your influence and wealth.</li>
            <li>Face random setbacks and opportunities—like getting arrested or receiving government grants!</li>
            <li>Your goal is to become the ultimate business tycoon by reaching the highest tycoon rank!</li>
        </ul>
        <h3>Tycoon Ranks:</h3>
        <p>Your tycoon rank will change as you earn more money and expand your empire. Here are the different titles you can achieve:</p>
        <ul>
            <li><strong>Homeless Can Collector</strong> - Starting rank</li>
            <li><strong>Street Hustler Extraordinaire</strong> - Reach $1,000</li>
            <li><strong>Neighborhood Business Whiz</strong> - Reach $10,000</li>
            <li><strong>Local Hotshot Restaurateur</strong> - Reach $50,000</li>
            <li><strong>Suburban Real Estate Shark</strong> - Reach $200,000</li>
            <li><strong>Bristol's Big Deal Tycoon</strong> - Reach $1,000,000</li>
            <li><strong>Master City Mogul</strong> - Reach $10,000,000</li>
            <li><strong>The Bristol Baron</strong> - Reach $100,000,000</li>
        </ul>
        <p>Each rank comes with its own unique rewards and challenges, pushing you to expand and automate your empire!</p>
        <h3>Directions:</h3>
        <p>Click the buttons to collect resources and sell them for money. Use the dropdown to buy upgrades to increase your productivity and grow your empire.</p>
        <p>The game continues indefinitely, with each milestone becoming progressively harder to reach, but also offering greater rewards.</p>
    </div>

    <script>
        let cans = 0;
        let smallBusinesses = 0;
        let midVentures = 0;
        let highVentures = 0;
        let restaurants = 0;
        let gasStations = 0;
        let groceryStores = 0;
        let money = 0;
        let autoCollector = false;
        let autoCollectorInterval = null;
        let tycoonRank = "Homeless Can Collector";

        function collectCans() {
            cans += 5;
            updateBusinessStatus();
        }

        function sellCans() {
            if (cans > 0) {
                money += cans * 0.05; // Cans sell for $0.05 each
                cans = 0;
                updateBusinessStatus();
            } else {
                alert("No cans to sell!");
            }
        }

        function investInSmallBusiness() {
            if (money >= 200) {
                smallBusinesses++;
                money -= 200;
                updateBusinessStatus();
            } else {
                alert("Not enough money to invest in a small business!");
            }
        }

        function buyRestaurant() {
            if (money >= 5000) {
                restaurants++;
                money -= 5000;
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a restaurant!");
            }
        }

        function buyGasStation() {
            if (money >= 10000) {
                gasStations++;
                money -= 10000;
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a gas station!");
            }
        }

        function buyGroceryStore() {
            if (money >= 20000) {
                groceryStores++;
                money -= 20000;
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a grocery store!");
            }
        }

        function buyUpgrade() {
            const upgrade = document.getElementById("upgrade-options").value;
            if (upgrade === "cart" && money >= 50) {
                money -= 50;
                cans += 10; // Boost can collection
            } else if (upgrade === "flyerDistributor" && money >= 200) {
                money -= 200;
                smallBusinesses++;
            } else if (upgrade === "hireManager" && money >= 500) {
                money -= 500;
                autoCollector = true;
                startAutoCollector();
            } else if (upgrade === "investInFoodTruck" && money >= 1500) {
                money -= 1500;
                midVentures++;
            } else if (upgrade === "buyCoffeeShop" && money >= 5000) {
                money -= 5000;
                smallBusinesses++;
            } else if (upgrade === "openConstruction" && money >= 10000) {
                money -= 10000;
                midVentures++;
            } else if (upgrade === "buyRealEstate" && money >= 20000) {
                money -= 20000;
                midVentures++;
            } else if (upgrade === "buySportsBar" && money >= 30000) {
                money -= 30000;
                highVentures++;
            } else if (upgrade === "expandFranchise" && money >= 50000) {
                money -= 50000;
                highVentures++;
            } else if (upgrade === "buyLuxuryRestaurant" && money >= 100000) {
                money -= 100000;
                highVentures++;
            } else if (upgrade === "investInBristolMall" && money >= 500000) {
                money -= 500000;
                highVentures++;
            } else if (upgrade === "becomePolitician" && money >= 1000000) {
                money -= 1000000;
                highVentures++;
            } else {
                alert("Not enough money for this upgrade or invalid option!");
            }
            updateBusinessStatus();
        }

        function startAutoCollector() {
            if (!autoCollectorInterval) {
                autoCollectorInterval = setInterval(() => {
                    collectCans();
                }, 3000); // Collect cans every 3 seconds
            }
        }

        function updateBusinessStatus() {
            document.getElementById("cans").innerText = cans;
            document.getElementById("smallBusinesses").innerText = smallBusinesses;
            document.getElementById("midVentures").innerText = midVentures;
            document.getElementById("highVentures").innerText = highVentures;
            document.getElementById("restaurants").innerText = restaurants;
            document.getElementById("gasStations").innerText = gasStations;
            document.getElementById("groceryStores").innerText = groceryStores;
            document.getElementById("money").innerText = money.toFixed(2);
            updateTycoonRank();
        }

        function updateTycoonRank() {
            if (money >= 100000000) {
                tycoonRank = "The Bristol Baron";
            } else if (money >= 10000000) {
                tycoonRank = "Master City Mogul";
            } else if (money >= 1000000) {
                tycoonRank = "Bristol's Big Deal Tycoon";
            } else if (money >= 200000) {
                tycoonRank = "Suburban Real Estate Shark";
            } else if (money >= 50000) {
                tycoonRank = "Local Hotshot Restaurateur";
            } else if (money >= 10000) {
                tycoonRank = "Neighborhood Business Whiz";
            } else if (money >= 1000) {
                tycoonRank = "Street Hustler Extraordinaire";
            } else {
                tycoonRank = "Homeless Can Collector";
            }
            document.getElementById("tycoonRank").innerText = tycoonRank;
        }
    </script>
</body>
</html>
