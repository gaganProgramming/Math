# Tasks
1. [Counter](#head1)
2. [Random Number Generator](#head2)
3. [Calculator](#head3)
4. [Forms](#head4)


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

Algorithm

`````````````````css
1. Initialize CounterValue to 0, store dom element in counterDisplay
2. Define Functions for Counter Operations, increment(), decrement reset and call update in each functions
3. Function to Update Counter Display, set textContent of counterDisplay to current counterValue
4. Add Event Listeners to Buttons, click and functions

``````````````````


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

Algorithm
``````````````````css
Algorithm Steps for Random Number Generator
1. Select DOM Elements store d store it in the variable myButton.
2. Select the label elements with IDs label1, label2, and label3 and store them in an array called labels.
3. Define Range for Random Number [0, 6]
4. Function to Generate a Random Number return Math.floor(Math.random() * max) + min;
5. Function to Update Labels with Random Numbers
6. Add Event Listener to the Button

````````````````````

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

````````````````css
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
    margin: 0;
}

.calculator {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

#display {
    width: 100%;
    height: 50px;
    font-size: 24px;
    text-align: right;
    border: none;
    margin-bottom: 10px;
    padding-right: 10px;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    height: 50px;
    font-size: 18px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: #e0e0e0;
}

button:hover {
    background-color: #d6d6d6;
}

button:active {
    background-color: #cccccc;
}

.zero {
    grid-column: span 2;
}

`````````````````
### <a name="head4">4.Forms</a>
``````````````````````````css
 Algorithm of Forms
Html
1. Forms id, label for= elementName,  [input types = email, password, tel, submit]
2. one more div to display error msg, and css -color, font-size

 Js
1. Add Event Listener for Form Submission, addEventListener(), event.preventDefault()
2. Clear Previous Errors, textContent- clearing error
3. Validate Each Field- email(@), password(10-14), confirm password(value)
4. PhoneNumberValidation, Check Validation Result
5. Check Validation Result- isValid, this.submit
````````````````````````````````````````````````````````````````
``````````````````````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Validation</title>
    <style>
        .error {
            color: red;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <h2>Form Validation</h2>
    <form id="myForm">
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
        <div id="emailError" class="error"></div><br>

        <label for="password">Password (10-14 characters):</label>
        <input type="password" id="password" name="password" required>
        <div id="passwordError" class="error"></div><br>

        <label for="confirmPassword">Confirm Password:</label>
        <input type="password" id="confirmPassword" name="confirmPassword" required>
        <div id="confirmPasswordError" class="error"></div><br>

        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" name="phone" maxlength="10" required>
        <div id="phoneError" class="error"></div><br>
        <label for="password">Email:</label>
        

        <button type="submit">Submit</button>
    </form>

    <script>
        document.getElementById("myForm").addEventListener("submit", function(event) {
            event.preventDefault(); // Prevent form submission

            // Clear previous errors
            document.getElementById("emailError").textContent = "";
            document.getElementById("passwordError").textContent = "";
            document.getElementById("confirmPasswordError").textContent = "";
            document.getElementById("phoneError").textContent = "";

            let isValid = true;

            // Email validation
            const email = document.getElementById("email").value;
            if (!email.includes("@")) {
                document.getElementById("emailError").textContent = "Please enter a valid email address.";
                isValid = false;
            }

            // Password validation
            const password = document.getElementById("password").value;
            if (password.length < 10 || password.length > 14) {
                document.getElementById("passwordError").textContent = "Password must be between 10 and 14 characters.";
                isValid = false;
            }

            // Confirm password validation
            const confirmPassword = document.getElementById("confirmPassword").value;
            if (password !== confirmPassword) {
                document.getElementById("confirmPasswordError").textContent = "Passwords do not match.";
                isValid = false;
            }

            // Phone number validation
            const phone = document.getElementById("phone").value;
            const phonePattern = /^[6789]\d{9}$/;
            if (!phonePattern.test(phone)) {
                document.getElementById("phoneError").textContent = "Phone number must start with 6, 7, 8, or 9 and be 10 digits long.";
                isValid = false;
            }

            // Submit form if valid
            if (isValid) {
                alert("Form submitted successfully!");
                // You can proceed with the form submission or further processing here.
                this.submit();
            }
        });
    </script>
</body>
</html>

```````````````````````````






