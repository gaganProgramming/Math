

# counterprogram

````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Counter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        #countLabel {
            font-size: 2rem;
            display: block;
            margin: 20px 0;
        }
        button {
            font-size: 1.2rem;
            margin: 5px;
            padding: 10px 15px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <h1>Counter</h1>
    <span id="countLabel">0</span>
    <br>
    <button id="decreaseBtn">Decrease</button>
    <button id="resetBtn">Reset</button>
    <button id="increaseBtn">Increase</button>

    <script>
        const countLabel = document.getElementById("countLabel");
        let count = 0;

        document.addEventListener("click", (event) => {
            if (event.target.id === "increaseBtn") count++;
            if (event.target.id === "decreaseBtn") count--;
            if (event.target.id === "resetBtn") count = 0;
            
            countLabel.textContent = count;
        });
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

# randomNumberGenerator
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dice Roller</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
        .dice-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        .dice {
            font-size: 24px;
            font-weight: bold;
            width: 50px;
            height: 50px;
            line-height: 50px;
            border: 2px solid black;
            border-radius: 8px;
            display: inline-block;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <h1>Roll the Dice</h1>
    <div class="dice-container">
        <span class="dice">🎲</span>
        <span class="dice">🎲</span>
        <span class="dice">🎲</span>
    </div>
    
    <button id="myButton">Roll Dice</button>

    <script>
        document.getElementById("myButton").onclick = () => {
            document.querySelectorAll(".dice").forEach(dice => {
                dice.textContent = Math.floor(Math.random() * 6) + 1;
            });
        };
    </script>

</body>
</html>


````````````````````````````````````````````````````````````````````````````````````
   
# numberGuessingGame
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number Guessing Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }
        h1 {
            color: #333;
        }
        input {
            padding: 10px;
            width: 80%;
            margin-top: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            margin-top: 10px;
            padding: 10px 15px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            background-color: #28a745;
            color: white;
            border-radius: 5px;
        }
        button:hover {
            background-color: #218838;
        }
        .message {
            margin-top: 15px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Number Guessing Game</h1>
        <p>Guess a number between <b>1 and 100</b></p>
        <input type="number" id="userGuess" placeholder="Enter your guess">
        <button id="guessBtn">Submit Guess</button>
        <p class="message" id="message"></p>
    </div>

    <script>
        const minNum = 1, maxNum = 100;
        const answer = Math.floor(Math.random() * (maxNum - minNum + 1)) + minNum; 
        let attempts = 0;

        document.getElementById("guessBtn").onclick = () => {
            const guess = Number(document.getElementById("userGuess").value);
            const message = document.getElementById("message");

            if (isNaN(guess) || guess < minNum || guess > maxNum) {
                message.textContent = "Please enter a valid number!";
                message.style.color = "red";
                return;
            }

            attempts++;
            if (guess < answer) {
                message.textContent = "Too low! Try again.";
                message.style.color = "blue";
            } else if (guess > answer) {
                message.textContent = "Too high! Try again.";
                message.style.color = "blue";
            } else {
                message.textContent = `Correct! The answer was ${answer}. Attempts: ${attempts}`;
                message.style.color = "green";
            }
        };
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

# temperatureConversion
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 350px;
            margin: auto;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }
        h1 {
            color: #333;
        }
        input, button {
            padding: 10px;
            width: 80%;
            margin-top: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #007bff;
            color: white;
            font-size: 16px;
            cursor: pointer;
            border: none;
        }
        button:hover {
            background-color: #0056b3;
        }
        .message {
            margin-top: 15px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Temperature Converter</h1>
        <input type="number" id="textBox" placeholder="Enter temperature">
        <br><br>
        <label><input type="radio" name="unit" id="toFahrenheit"> Convert to Fahrenheit</label>
        <br>
        <label><input type="radio" name="unit" id="toCelsius"> Convert to Celsius</label>
        <br><br>
        <button onclick="convert()">Convert</button>
        <p class="message" id="result"></p>
    </div>

    <script>
        function convert() {
            const temp = Number(document.getElementById("textBox").value);
            const toFahrenheit = document.getElementById("toFahrenheit").checked;
            const toCelsius = document.getElementById("toCelsius").checked;
            const result = document.getElementById("result");

            if (isNaN(temp)) {
                result.textContent = "Enter a valid number!";
                result.style.color = "red";
                return;
            }

            result.style.color = "black";
            result.textContent = toFahrenheit
                ? `${(temp * 9 / 5 + 32).toFixed(1)}°F`
                : toCelsius
                ? `${((temp - 32) * 5 / 9).toFixed(1)}°C`
                : "Select a unit!";
        }
    </script>

</body>
</html>
````````````````````````````````````````````````````````````````````````````````````

diceRollerProgram
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dice Roller</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 50px;
        }
        .container {
            background: white;
            padding: 20px;
            max-width: 400px;
            margin: auto;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }
        h1 {
            color: #333;
        }
        input, button {
            padding: 10px;
            width: 80%;
            margin-top: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #007bff;
            color: white;
            font-size: 16px;
            cursor: pointer;
            border: none;
        }
        button:hover {
            background-color: #0056b3;
        }
        .dice-container {
            margin-top: 20px;
        }
        .dice-container img {
            width: 50px;
            margin: 5px;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Dice Roller 🎲</h1>
        <input type="number" id="numOfDice" min="1" max="6" placeholder="Enter number of dice (1-6)">
        <br><br>
        <button onclick="rollDice()">Roll Dice</button>
        <p id="diceResult"></p>
        <div class="dice-container" id="diceImages"></div>
    </div>

    <script>
        function rollDice() {
            const numOfDice = document.getElementById("numOfDice").value;
            const diceResult = document.getElementById("diceResult");
            const diceImages = document.getElementById("diceImages");

            if (!numOfDice || numOfDice < 1 || numOfDice > 6) {
                diceResult.textContent = "Please enter a number between 1 and 6!";
                diceResult.style.color = "red";
                return;
            }

            diceResult.style.color = "black";
            const values = [];
            const images = [];

            for (let i = 0; i < numOfDice; i++) {
                const value = Math.floor(Math.random() * 6) + 1;
                values.push(value);
                images.push(`<img src="dice_images/${value}.png" alt="Dice ${value}">`);
            }

            diceResult.textContent = `Dice: ${values.join(", ")}`;
            diceImages.innerHTML = images.join("");
        }
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````-

# randomPasswordGenerator
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 50px;
        }
        .container {
            background: white;
            padding: 20px;
            max-width: 400px;
            margin: auto;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }
        h1 {
            color: #333;
        }
        label {
            display: block;
            margin: 10px 0;
        }
        input, button {
            padding: 10px;
            width: 80%;
            margin-top: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #007bff;
            color: white;
            font-size: 16px;
            cursor: pointer;
            border: none;
        }
        button:hover {
            background-color: #0056b3;
        }
        #passwordOutput {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
            color: #333;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Password Generator 🔐</h1>
        <label>
            Length: <input type="number" id="length" min="4" max="20" value="12">
        </label>
        <label>
            <input type="checkbox" id="lowercase" checked> Include Lowercase (a-z)
        </label>
        <label>
            <input type="checkbox" id="uppercase" checked> Include Uppercase (A-Z)
        </label>
        <label>
            <input type="checkbox" id="numbers" checked> Include Numbers (0-9)
        </label>
        <label>
            <input type="checkbox" id="symbols" checked> Include Symbols (!@#$%^&*)
        </label>
        <button onclick="generateAndDisplayPassword()">Generate Password</button>
        <p id="passwordOutput"></p>
    </div>

    <script>
        function generatePassword(length, includeLowercase, includeUppercase, includeNumbers, includeSymbols) {
            const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
            const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
            const numberChars = "0123456789";
            const symbolChars = "!@#$%^&*()_+-=";

            let allowedChars = "";
            let password = "";

            if (includeLowercase) allowedChars += lowercaseChars;
            if (includeUppercase) allowedChars += uppercaseChars;
            if (includeNumbers) allowedChars += numberChars;
            if (includeSymbols) allowedChars += symbolChars;

            if (length <= 0) return "Password length must be at least 1!";
            if (allowedChars.length === 0) return "Select at least one character set!";

            for (let i = 0; i < length; i++) {
                const randomIndex = Math.floor(Math.random() * allowedChars.length);
                password += allowedChars[randomIndex];
            }

            return password;
        }

        function generateAndDisplayPassword() {
            const length = document.getElementById("length").value;
            const includeLowercase = document.getElementById("lowercase").checked;
            const includeUppercase = document.getElementById("uppercase").checked;
            const includeNumbers = document.getElementById("numbers").checked;
            const includeSymbols = document.getElementById("symbols").checked;

            const password = generatePassword(length, includeLowercase, includeUppercase, includeNumbers, includeSymbols);
            document.getElementById("passwordOutput").textContent = `Generated Password: ${password}`;
        }
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

 #digitalClockProgram
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Digital Clock</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #282c34;
            color: white;
            margin: 50px;
        }
        .clock-container {
            display: inline-block;
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
        }
        #clock {
            font-size: 50px;
            font-weight: bold;
            letter-spacing: 2px;
        }
    </style>
</head>
<body>

    <div class="clock-container">
        <p id="clock">Loading...</p>
    </div>

    <script>
        function updateClock() {
            const now = new Date();
            let hours = now.getHours();
            const meridiem = hours >= 12 ? "PM" : "AM";
            hours = hours % 12 || 12;
            const minutes = now.getMinutes().toString().padStart(2, "0");
            const seconds = now.getSeconds().toString().padStart(2, "0");
            const timeString = `${hours}:${minutes}:${seconds} ${meridiem}`;
            document.getElementById("clock").textContent = timeString;
        }

        updateClock();
        setInterval(updateClock, 1000);
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

 # stopwatchProgram
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #282c34;
            color: white;
            margin: 50px;
        }
        .stopwatch-container {
            display: inline-block;
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
        }
        #display {
            font-size: 50px;
            font-weight: bold;
            letter-spacing: 2px;
        }
        .buttons {
            margin-top: 20px;
        }
        button {
            font-size: 18px;
            padding: 10px 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        #startBtn { background-color: #4CAF50; color: white; }
        #stopBtn { background-color: #f44336; color: white; }
        #resetBtn { background-color: #008CBA; color: white; }
    </style>
</head>
<body>

    <div class="stopwatch-container">
        <p id="display">00:00:00:00</p>
        <div class="buttons">
            <button id="startBtn" onclick="start()">Start</button>
            <button id="stopBtn" onclick="stop()">Stop</button>
            <button id="resetBtn" onclick="reset()">Reset</button>
        </div>
    </div>

    <script>
        const display = document.getElementById("display");
        let timer = null;
        let startTime = 0;
        let elapsedTime = 0;
        let isRunning = false;

        function start() {
            if (!isRunning) {
                startTime = Date.now() - elapsedTime;
                timer = setInterval(update, 10);
                isRunning = true;
            }
        }

        function stop() {
            if (isRunning) {
                clearInterval(timer);
                elapsedTime = Date.now() - startTime;
                isRunning = false;
            }
        }

        function reset() {
            clearInterval(timer);
            startTime = 0;
            elapsedTime = 0;
            isRunning = false;
            display.textContent = "00:00:00:00";
        }

        function update() {
            const currentTime = Date.now();
            elapsedTime = currentTime - startTime;
            let hours = Math.floor(elapsedTime / (1000 * 60 * 60));
            let minutes = Math.floor((elapsedTime / (1000 * 60)) % 60);
            let seconds = Math.floor((elapsedTime / 1000) % 60);
            let milliseconds = Math.floor((elapsedTime % 1000) / 10);

            display.textContent = 
                `${String(hours).padStart(2, "0")}:` +
                `${String(minutes).padStart(2, "0")}:` +
                `${String(seconds).padStart(2, "0")}:` +
                `${String(milliseconds).padStart(2, "0")}`;
        }
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

 # calculatorProgram
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #282c34;
            color: white;
            margin: 50px;
        }
        .calculator {
            display: inline-block;
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
        }
        #display {
            width: 100%;
            height: 50px;
            font-size: 24px;
            text-align: right;
            padding: 10px;
            border: none;
            border-radius: 5px;
            margin-bottom: 10px;
            background: #222;
            color: white;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 60px);
            gap: 10px;
            justify-content: center;
        }
        button {
            font-size: 20px;
            padding: 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background-color: #444;
            color: white;
        }
        button:active {
            background-color: #666;
        }
        .operator {
            background-color: #f39c12;
        }
        .operator:active {
            background-color: #e67e22;
        }
        .equal {
            background-color: #2ecc71;
        }
        .equal:active {
            background-color: #27ae60;
        }
        .clear {
            background-color: #e74c3c;
        }
        .clear:active {
            background-color: #c0392b;
        }
    </style>
</head>
<body>

    <div class="calculator">
        <input type="text" id="display" readonly>
        <div class="buttons">
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('*')">*</button>
            
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            
            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button class="clear" onclick="clearDisplay()">C</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>

            <button class="equal" style="grid-column: span 4;" onclick="calculate()">=</button>
        </div>
    </div>

    <script>
        const display = document.getElementById("display");

        function appendToDisplay(input) {
            display.value += input;
        }

        function clearDisplay() {
            display.value = "";
        }

        function calculate() {
            try {
                display.value = eval(display.value);
            } catch (error) {
                display.value = "Error";
            }
        }
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

 # rockPaperScissors
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock Paper Scissors</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #282c34;
            color: white;
            margin: 50px;
        }
        h1 {
            margin-bottom: 20px;
        }
        .choices {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 20px;
        }
        button {
            font-size: 18px;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        .rock { background-color: #f39c12; }
        .paper { background-color: #3498db; }
        .scissors { background-color: #e74c3c; }
        button:active { opacity: 0.8; }
        .result {
            margin-top: 20px;
            font-size: 22px;
            font-weight: bold;
        }
        .greenText { color: #2ecc71; }
        .redText { color: #e74c3c; }
    </style>
</head>
<body>

    <h1>Rock Paper Scissors</h1>

    <div class="choices">
        <button class="rock" onclick="playGame('rock')">Rock</button>
        <button class="paper" onclick="playGame('paper')">Paper</button>
        <button class="scissors" onclick="playGame('scissors')">Scissors</button>
    </div>

    <p id="playerDisplay">PLAYER: </p>
    <p id="computerDisplay">COMPUTER: </p>
    <p id="resultDisplay" class="result"></p>

    <h2>Score</h2>
    <p>Player: <span id="playerScoreDisplay">0</span></p>
    <p>Computer: <span id="computerScoreDisplay">0</span></p>

    <script>
        const choices = ["rock", "paper", "scissors"];
        const playerDisplay = document.getElementById("playerDisplay");
        const computerDisplay = document.getElementById("computerDisplay");
        const resultDisplay = document.getElementById("resultDisplay");
        const playerScoreDisplay = document.getElementById("playerScoreDisplay");
        const computerScoreDisplay = document.getElementById("computerScoreDisplay");
        let playerScore = 0;
        let computerScore = 0;

        function playGame(playerChoice) {
            const computerChoice = choices[Math.floor(Math.random() * 3)];
            let result = "";

            if (playerChoice === computerChoice) {
                result = "It's a TIE!";
            } else {
                switch (playerChoice) {
                    case "rock":
                        result = (computerChoice === "scissors") ? "YOU WIN!" : "You LOSE!";
                        break;
                    case "paper":
                        result = (computerChoice === "rock") ? "YOU WIN!" : "You LOSE!";
                        break;
                    case "scissors":
                        result = (computerChoice === "paper") ? "YOU WIN!" : "You LOSE!";
                        break;
                }
            }

            playerDisplay.textContent = `PLAYER: ${playerChoice}`;
            computerDisplay.textContent = `COMPUTER: ${computerChoice}`;
            resultDisplay.textContent = result;

            resultDisplay.classList.remove("greenText", "redText");

            switch (result) {
                case "YOU WIN!":
                    resultDisplay.classList.add("greenText");
                    playerScore++;
                    playerScoreDisplay.textContent = playerScore;
                    break;
                case "You LOSE!":
                    resultDisplay.classList.add("redText");
                    computerScore++;
                    computerScoreDisplay.textContent = computerScore;
                    break;
            }
        }
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

 # imageSlider
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Slider</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #282c34;
            color: white;
        }
        .slider-container {
            width: 500px;
            height: 300px;
            overflow: hidden;
            position: relative;
            margin: auto;
            border-radius: 10px;
        }
        .slides img {
            width: 100%;
            height: 100%;
            display: none;
        }
        .displaySlide {
            display: block;
        }
        .controls {
            margin-top: 10px;
        }
        button {
            padding: 10px 15px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            background-color: #3498db;
            color: white;
            border-radius: 5px;
        }
        button:hover {
            background-color: #2980b9;
        }
    </style>
</head>
<body>

    <h1>Image Slider</h1>
    <div class="slider-container">
        <div class="slides">
            <img src="https://source.unsplash.com/random/500x300?nature" alt="Slide 1">
            <img src="https://source.unsplash.com/random/500x300?mountains" alt="Slide 2">
            <img src="https://source.unsplash.com/random/500x300?water" alt="Slide 3">
        </div>
    </div>
    
    <div class="controls">
        <button onclick="prevSlide()">Previous</button>
        <button onclick="nextSlide()">Next</button>
    </div>

    <script>
        const slides = document.querySelectorAll(".slides img");
        let slideIndex = 0;
        let intervalId = null;

        document.addEventListener("DOMContentLoaded", initializeSlider);

        function initializeSlider() {
            if (slides.length > 0) {
                slides[slideIndex].classList.add("displaySlide");
                intervalId = setInterval(nextSlide, 3000);
            }
        }

        function showSlide(index) {
            if (index >= slides.length) {
                slideIndex = 0;
            } else if (index < 0) {
                slideIndex = slides.length - 1;
            } else {
                slideIndex = index;
            }

            slides.forEach(slide => {
                slide.classList.remove("displaySlide");
            });

            slides[slideIndex].classList.add("displaySlide");
        }

        function prevSlide() {
            clearInterval(intervalId);
            slideIndex--;
            showSlide(slideIndex);
            restartInterval();
        }

        function nextSlide() {
            clearInterval(intervalId);
            slideIndex++;
            showSlide(slideIndex);
            restartInterval();
        }

        function restartInterval() {
            intervalId = setInterval(nextSlide, 3000);
        }
    </script>

</body>
</html>

````````````````````````````````````````````````````````````````````````````````````

# weatherAppProject
````````````````````````````````````````````````````````````````````````````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="container">
        <h2>🌤️ Weather App</h2>
        <form class="weatherForm">
            <input type="text" class="cityInput" placeholder="Enter city name..." required>
            <button type="submit">Get Weather</button>
        </form>
        <div class="card hidden">
            <h1 class="cityDisplay"></h1>
            <p class="tempDisplay"></p>
            <p class="humidityDisplay"></p>
            <p class="descDisplay"></p>
            <p class="weatherEmoji"></p>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>

````````````````````````````````````````````````````````````````````````````````````
