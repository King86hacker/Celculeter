<!DOCTYPE html>
<html>
<head>
    <title>Simple Calculator</title>
    <style>
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
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .display {
            margin-bottom: 10px;
            font-size: 2em;
            height: 50px;
            text-align: right;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #e0e0e0;
        }
        .button {
            width: 60px;
            height: 60px;
            margin: 5px;
            font-size: 1.5em;
            cursor: pointer;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        .button:hover {
            background-color: #f0f0f0;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <button class="button" onclick="appendNumber('1')">1</button>
        <button class="button" onclick="appendNumber('2')">2</button>
        <button class="button" onclick="appendNumber('3')">3</button>
        <button class="button" onclick="setOperation('+')">+</button><br>
        <button class="button" onclick="appendNumber('4')">4</button>
        <button class="button" onclick="appendNumber('5')">5</button>
        <button class="button" onclick="appendNumber('6')">6</button>
        <button class="button" onclick="setOperation('-')">-</button><br>
        <button class="button" onclick="appendNumber('7')">7</button>
        <button class="button" onclick="appendNumber('8')">8</button>
        <button class="button" onclick="appendNumber('9')">9</button>
        <button class="button" onclick="setOperation('*')">*</button><br>
        <button class="button" onclick="appendNumber('0')">0</button>
        <button class="button" onclick="clearDisplay()">C</button>
        <button class="button" onclick="calculate()">=</button>
        <button class="button" onclick="setOperation('/')">/</button>
    </div>

    <script>
        let display = document.getElementById('display');
        let currentNumber = '';
        let previousNumber = '';
        let operation = null;

        function appendNumber(number) {
            if (currentNumber.length < 10) {
                currentNumber += number;
                display.innerText = currentNumber;
            }
        }

        function setOperation(op) {
            if (currentNumber === '') return;
            if (previousNumber !== '') {
                calculate();
            }
            operation = op;
            previousNumber = currentNumber;
            currentNumber = '';
        }

        function calculate() {
            let result;
            const prev = parseFloat(previousNumber);
            const current = parseFloat(currentNumber);
            if (isNaN(prev) || isNaN(current)) return;
            switch (operation) {
                case '+':
                    result = prev + current;
                    break;
                case '-':
                    result = prev - current;
                    break;
                case '*':
                    result = prev * current;
                    break;
                case '/':
                    result = prev / current;
                    break;
                default:
                    return;
            }
            currentNumber = result.toString();
            operation = null;
            previousNumber = '';
            display.innerText = currentNumber;
        }

        function clearDisplay() {
            currentNumber = '';
            previousNumber = '';
            operation = null;
            display.innerText = '0';
        }
    </script>
<link rel="stylesheet" href="new.css">
</body>
</html>
