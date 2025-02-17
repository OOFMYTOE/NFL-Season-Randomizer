<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Randomize NFL Teams</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f0f0f0;
            padding: 20px;
            color: #333;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        h1 {
            color: #2d3e50;
        }
        button {
            background-color: #007BFF;
            color: white;
            font-size: 18px;
            padding: 15px 30px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        button:hover {
            background-color: #0056b3;
            transform: scale(1.05);
        }
        button:active {
            background-color: #004085;
            transform: scale(1);
        }
        #teams-list {
            font-size: 18px;
            font-weight: bold;
            margin-top: 20px;
            width: 100%;
            max-width: 600px;
            text-align: left;
        }
        .division {
            background-color: #ffffff;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        .division strong {
            color: #007BFF;
        }
        ul {
            list-style-type: none;
            padding-left: 20px;
        }
        li {
            padding: 5px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <h1>Randomize NFL Teams into Divisions</h1>
    <p>Click the button below to randomize the teams and assign them to divisions.</p>

    <!-- Button to trigger the randomization -->
    <button onclick="randomizeTeams()">Randomize Teams</button>

    <div id="teams-list">
        <!-- Randomized teams will be displayed here -->
    </div>

    <script>
        // NFL teams for each division
        const divisions = {
            "AFC East": ["Buffalo Bills", "Miami Dolphins", "New England Patriots", "New York Jets"],
            "AFC North": ["Baltimore Ravens", "Cincinnati Bengals", "Cleveland Browns", "Pittsburgh Steelers"],
            "AFC South": ["Houston Texans", "Indianapolis Colts", "Jacksonville Jaguars", "Tennessee Titans"],
            "AFC West": ["Denver Broncos", "Kansas City Chiefs", "Las Vegas Raiders", "Los Angeles Chargers"],
            "NFC East": ["Dallas Cowboys", "New York Giants", "Philadelphia Eagles", "Washington Commanders"],
            "NFC North": ["Chicago Bears", "Detroit Lions", "Green Bay Packers", "Minnesota Vikings"],
            "NFC South": ["Atlanta Falcons", "Carolina Panthers", "New Orleans Saints", "Tampa Bay Buccaneers"],
            "NFC West": ["Arizona Cardinals", "Los Angeles Rams", "San Francisco 49ers", "Seattle Seahawks"]
        };

        // Function to randomize teams and assign to divisions
        function randomizeTeams() {
            // Flatten the teams into one array
            let allTeams = [];
            for (let division in divisions) {
                allTeams = allTeams.concat(divisions[division]);
            }

            // Shuffle the array of teams
            let shuffledTeams = allTeams.sort(() => Math.random() - 0.5);

            // Reset divisions with shuffled teams
            let randomizedDivisions = {
                "AFC East": [],
                "AFC North": [],
                "AFC South": [],
                "AFC West": [],
                "NFC East": [],
                "NFC North": [],
                "NFC South": [],
                "NFC West": []
            };

            // Assign shuffled teams to divisions
            let divisionNames = Object.keys(randomizedDivisions);
            for (let i = 0; i < shuffledTeams.length; i++) {
                let division = divisionNames[Math.floor(i / 4)];  // 4 teams per division
                randomizedDivisions[division].push(shuffledTeams[i]);
            }

            // Display the randomized divisions with improved styling
            let resultHTML = '';
            for (let division in randomizedDivisions) {
                resultHTML += `<div class="division"><strong>${division}:</strong><ul>`;
                randomizedDivisions[division].forEach(team => {
                    resultHTML += `<li>${team}</li>`;
                });
                resultHTML += `</ul></div>`;
            }

            // Show the result in the div
            document.getElementById("teams-list").innerHTML = resultHTML;
        }
    </script>
</body>
</html>
