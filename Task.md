# Tasks
1. [Counter](#head1)
2. [Random Number Generator](#head2)
3. [Calculator](#head3)


### <a name="head1">1. Counter</a>
```````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Counter:<span id="counter-value">0</span></h1>
    <button id="incrementBtn">Increment</button>
    <button id="decrementBtn">Decrement</button>
    <button id="resetBtn">reset</button>

    <script src="index.js"></script>
</body>
</html>
``````````````


``````````````js
let counterValue = 0;
const counterDisplay = document.getElementById('counter-value');

function increment() {
    counterValue++;
    updateCounterDisplay();
}
function decrement() {
    counterValue--;
    updateCounterDisplay();
}
function reset() {
    counterValue = 0;
    updateCounterDisplay();
}
function updateCounterDisplay() {
   counterDisplay.textContent = counterValue;
}
document.getElementById('incrementBtn').addEventListener('click', increment);
document.getElementById('decrementBtn').addEventListener('click', decrement);
document.getElementById('resetBtn').addEventListener('click', reset);

````````````````

### <a name="head2">2. Random Number Generator</a>
```````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <button id="myButton">Generate</button>
    <p><span id="label1">0</span></p>
    <p><span id="label2">0</span></p>
    <p><span id="label3">0</span></p>

    <script src="index.js"></script>
</body>
</html>
``````````````


``````````````js
const myButton = document.getElementById('myButton');
const labels = [
    document.getElementById('label1'),
    document.getElementById('label2'),
    document.getElementById('label3')
];

const min =0;
const max =6;

function generateRandomNumber(){
    return Math.floor(Math.random() * max) + min;
}

function updateLabel(){
    labels.forEach((label) => {
        const randomNumber = generateRandomNumber();    
        label.textContent = randomNumber;
    });
}

myButton.addEventListener('click', updateLabel);
````````````````

### <a name="head3">3. Calculator</a>
```````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculator">
        <!-- Display for the calculator -->
        <input type="text" id="display" disabled>

        <!-- Calculator buttons -->
        <div class="buttons">
            <button>C</button>
            <button>/</button>
            <button>*</button>
            <button>DEL</button>
            
            <button>7</button>
            <button>8</button>
            <button>9</button>
            <button>-</button>
             
            <button>4</button>
            <button>5</button>
            <button>6</button>
            <button>+</button>
            
            <button>1</button>
            <button>2</button>
            <button>3</button>
            <button>=</button>
            
            <button class="zero">0</button>
            <button>.</button>
        </div>
    </div>

    <!-- Linking the JavaScript file -->
    <script src="index.js"></script>
</body>
</html>

``````````````


``````````````js
// Select the display element
const display = document.getElementById('display');

// Select all buttons
const buttons = document.querySelectorAll('.buttons button');

// Attach event listener to each button
buttons.forEach(button => {
    button.addEventListener('click', () => {
        const value = button.textContent;

        if (value === 'C') {
            clearDisplay();
        } else if (value === 'DEL') {
            deleteLast();
        } else if (value === '=') {
            calculate();
        } else {
            appendValue(value);
        }
    });
});

// Function to append values to the display
function appendValue(value) {
    display.value += value;
}

// Function to clear the display
function clearDisplay() {
    display.value = '';
}

// Function to delete the last character
function deleteLast() {
    display.value = display.value.slice(0, -1);
}

// Function to calculate the result
function calculate() {
    try {
        display.value = eval(display.value);
    } catch (error) {
        display.value = 'Error';
    }
}


````````````````
