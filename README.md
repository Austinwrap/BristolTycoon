<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Bristol Business Tycoon</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin: 0;
            padding: 10px;
            background-color: #ffefd5;
        }
        .business-status {
            margin-bottom: 10px;
            text-align: center;
            border: 3px solid #8b4513;
            padding: 10px;
            background-color: #fff8dc;
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
            padding: 10px;
            font-size: 16px;
            border: 2px solid #228b22;
            border-radius: 8px;
            background-color: #98fb98;
            color: #4b0082;
            cursor: pointer;
            box-shadow: 2px 2px 5px #888888;
            max-width: 200px;
        }
        button:hover, select:hover {
            background-color: #7cfc00;
        }
        h1 {
            font-family: 'Press Start 2P', cursive;
            color: #00bfff;
            text-shadow: 3px 3px #000;
            font-size: 2em;
            letter-spacing: 1px;
            text-transform: uppercase;
            font-weight: bold;
            text-align: center;
        }
        .rules {
            border: 3px dashed #8b4513;
            padding: 10px;
            margin-top: 20px;
            background-color: #f0e68c;
            border-radius: 10px;
            max-width: 90%;
            box-sizing: border-box;
        }
        .tycoon-rank {
            font-weight: bold;
            font-size: 1.5em;
            color: #ff4500;
            text-shadow: 2px 2px 4px #000;
            letter-spacing: 1px;
        }
        .money-display {
            font-size: 1.5em;
            color: #ffd700;
            font-weight: bold;
            text-shadow: 1px 1px 3px #000;
            padding: 8px;
            background-color: #fff8dc;
            border: 3px solid #228b22;
            border-radius: 10px;
            margin-top: 10px;
        }
        .end-game {
            text-align: center;
            font-size: 1.5em;
            color: red;
            margin-top: 30px;
        }
    </style>
</head>
<body>
    <h1>Bristol Business Tycoon</h1>
    <div class="business-status">
        <p>Cans Collected: <span id="cans">0</span></p>
        <p>Food Trucks Owned: <span id="smallBusinesses">0</span></p>
        <p>Local Shops Owned: <span id="midVentures">0</span></p>
        <p>Landmarks Owned: <span id="highVentures">0</span></p>
        <p>Restaurants Owned: <span id="restaurants">0</span></p>
        <p>Gas Stations Owned: <span id="gasStations">0</span></p>
        <p>Grocery Stores Owned: <span id="groceryStores">0</span></p>
        <p class="money-display">Money: $<span id="money">0</span></p>
        <p>Tycoon Rank: <span id="tycoonRank" class="tycoon-rank">Bristol Bottle Collector</span></p>
    </div>

    <div class="buttons-container">
        <button onclick="collectCans()">🛒 Collect Cans</button>
        <button onclick="sellCans()">💰 Sell Cans</button>
        <button onclick="investInSmallBusiness()">🚚 Invest in "Kens Grille Food Truck" ($200)</button>
        <button onclick="buyRestaurant()">🍽️ Buy "Monterrey On Riverside" ($5000)</button>
        <button onclick="buyGasStation()">⛽ Buy "Middle St Mobil Station" ($10000)</button>
        <button onclick="buyGroceryStore()">🛒 Buy "Price Chopper Bristol" ($20000)</button>
    </div>

    <select id="upgrade-options" onchange="buyUpgrade()">
        <option value="">-- Buy Upgrade --</option>
        <option value="cart">🛒 Buy a Better Cart ($50)</option>
        <option value="flyerDistributor">📄 Become Flyer Distributor ($200)</option>
        <option value="hireManager">👨‍💼 Hire Store Manager ($500)</option>
        <option value="investInFoodTruck">🚚 Invest in "Hidden Cafe" Food Truck ($1500)</option>
        <option value="buyCoffeeShop">☕ Buy "Aroma Joe's" Coffee Shop ($5000)</option>
        <option value="openConstruction">🏗️ Open "Broad Builders" Construction ($10000)</option>
        <option value="buyRealEstate">🏢 Invest in "Price Chopper Plaza" Real Estate ($20000)</option>
        <option value="buySportsBar">🍻 Buy "Sportys" Sports Bar ($30000)</option>
        <option value="expandFranchise">🏪 Expand "GameTime Arcade" Franchise ($50000)</option>
        <option value="buyLuxuryRestaurant">🥂 Buy "New Hibachi Grille" Luxury Restaurant ($100000)</option>
        <option value="investInBristolMall">🏬 Invest in "Bristol Mall" ($500000)</option>
        <option value="becomePolitician">👔 Become Local Politician ($1000000)</option>
    </select>

    <div class="rules">
        <h2>Game Rule Book & Directions</h2>
        <p>Welcome to Bristol Business Tycoon! Here is how you play:</p>
        <ul>
            <li>Start with humble beginnings as a Bristol Bottle Collector and earn money to invest in businesses around Bristol.</li>
            <li>Use your earnings to buy upgrades, invest in businesses, and expand your empire!</li>
            <li>Buy local restaurants, gas stations, grocery stores, and more to grow your influence and wealth.</li>
            <li>Face random setbacks and opportunities—like getting arrested or receiving government grants!</li>
            <li>Your goal is to become the ultimate business tycoon by reaching the highest tycoon rank!</li>
        </ul>
        <h3>Tycoon Ranks:</h3>
        <p>Your tycoon rank will change as you earn more money and expand your empire. Here are the different titles you can achieve:</p>
        <ul>
            <li><strong>Bristol Bottle Collector</strong> - Starting rank</li>
            <li><strong>Bartender - Generating Tips</strong> - Reach $1,000</li>
            <li><strong>Bristol Small Biz Buff</strong> - Reach $10,000</li>
            <li><strong>Local Hotshot Mogul</strong> - Reach $50,000</li>
            <li><strong>Suburban Property Pioneer</strong> - Reach $200,000</li>
            <li><strong>Bell City Business Boss</strong> - Reach $1,000,000</li>
            <li><strong>Master of Bristol Ventures</strong> - Reach $10,000,000</li>
            <li><strong>The Bristol Baron</strong> - Reach $100,000,000</li>
            <li><strong>David Haberfield</strong> - Reach $100,000,000,000,000 - You run this town!</li>
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
        let tycoonRank = "Bristol Bottle Collector";

        let smallBusinessCost = 200;
        let restaurantCost = 5000;
        let gasStationCost = 10000;
        let groceryStoreCost = 20000;

        function collectCans() {
            cans += 5;
            updateBusinessStatus();
        }

        function sellCans() {
            if (cans > 0) {
                money += cans * 0.05;
                cans = 0;
                updateBusinessStatus();
            } else {
                alert("No cans to sell!");
            }
        }

        function investInSmallBusiness() {
            if (money >= smallBusinessCost) {
                smallBusinesses++;
                money -= smallBusinessCost;
                smallBusinessCost = Math.floor(smallBusinessCost * 1.15);
                alert('Congratulations! You have just invested in a food truck: Riverside Food Truck!');
                updateBusinessStatus();
            } else {
                alert("Not enough money to invest in a small business!");
            }
        }

        function buyRestaurant() {
            if (money >= restaurantCost) {
                restaurants++;
                money -= restaurantCost;
                restaurantCost = Math.floor(restaurantCost * 1.15);
                alert('Congratulations! You have just bought a restaurant: Main Street Pint & Plate!');
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a restaurant!");
            }
        }

        function buyGasStation() {
            if (money >= gasStationCost) {
                gasStations++;
                money -= gasStationCost;
                gasStationCost = Math.floor(gasStationCost * 1.15);
                alert('Congratulations! You have just bought a gas station: Middle St Mobil Station!');
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a gas station!");
            }
        }

        function buyGroceryStore() {
            if (money >= groceryStoreCost) {
                groceryStores++;
                money -= groceryStoreCost;
                groceryStoreCost = Math.floor(groceryStoreCost * 1.15);
                alert('Congratulations! You have just purchased a grocery store: Stop & Shop Bristol!');
                updateBusinessStatus();
            } else {
                alert("Not enough money to buy a grocery store!");
            }
        }

        function buyUpgrade() {
            const upgrade = document.getElementById("upgrade-options").value;
            switch(upgrade) {
                case "cart":
                    if (money >= 50) {
                        money -= 50;
                        cans += 10;
                        alert('Better Cart purchased! You can now collect more cans.');
                    } else {
                        alert('Not enough money for a better cart!');
                    }
                    break;
                case "flyerDistributor":
                    if (money >= 200) {
                        money -= 200;
                        alert('You are now a Flyer Distributor. Income slightly increased!');
                    } else {
                        alert('Not enough money to become a Flyer Distributor!');
                    }
                    break;
                case "hireManager":
                    if (money >= 500) {
                        money -= 500;
                        alert('Store Manager hired! Your business runs more smoothly.');
                    } else {
                        alert('Not enough money to hire a store manager!');
                    }
                    break;
                case "investInFoodTruck":
                    if (money >= 1500) {
                        money -= 1500;
                        smallBusinesses++;
                        alert('Invested in Hidden Cafe Food Truck! Food Trucks owned increased.');
                    } else {
                        alert('Not enough money to invest in a food truck!');
                    }
                    break;
                case "buyCoffeeShop":
                    if (money >= 5000) {
                        money -= 5000;
                        restaurants++;
                        alert('You have bought Pure Foods Coffee Shop! Restaurants owned increased.');
                    } else {
                        alert('Not enough money to buy a coffee shop!');
                    }
                    break;
                // Add more upgrades as needed
            }
            updateBusinessStatus();
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
            if (money >= 100000000000000) {
                tycoonRank = "David Haberfield - You run this town!";
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
                tycoonRank = "Bartender - Generating Tips";
            } else {
                tycoonRank = "Bristol Bottle Collector";
            }
            document.getElementById("tycoonRank").innerText = tycoonRank;
        }
    </script>
</body>
</html>
