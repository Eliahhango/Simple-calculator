<!DOCTYPE html>
<html>
<head>
    <title>Enhanced Calculator</title>
    <style>
        .calculator {
            width: 220px;
            margin: 100px auto;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input[type="text"] {
            width: 100%;
            height: 40px;
            text-align: right;
            margin-bottom: 10px;
            font-size: 18px;
            padding: 5px;
        }
        input[type="button"] {
            width: 50px;
            height: 50px;
            margin: 2px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled>
        <br>
        <input type="button" value="1" onclick="appendNumber(1)">
        <input type="button" value="2" onclick="appendNumber(2)">
        <input type="button" value="3" onclick="appendNumber(3)">
        <input type="button" value="+" onclick="appendOperator('+')">
        <br>
        <input type="button" value="4" onclick="appendNumber(4)">
        <input type="button" value="5" onclick="appendNumber(5)">
        <input type="button" value="6" onclick="appendNumber(6)">
        <input type="button" value="-" onclick="appendOperator('-')">
        <br>
        <input type="button" value="7" onclick="appendNumber(7)">
        <input type="button" value="8" onclick="appendNumber(8)">
        <input type="button" value="9" onclick="appendNumber(9)">
        <input type="button" value="*" onclick="appendOperator('*')">
        <br>
        <input type="button" value="C" onclick="clearDisplay()">
        <input type="button" value="0" onclick="appendNumber(0)">
        <input type="button" value="." onclick="appendNumber('.')">
        <input type="button" value="=" onclick="calculate()">
        <input type="button" value="/" onclick="appendOperator('/')">
    </div>

    <script>
        function appendNumber(number) {
            document.getElementById('display').value += number;
        }

        function appendOperator(operator) {
            document.getElementById('display').value += ' ' + operator + ' ';
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function calculate() {
            try {
                let display = document.getElementById('display').value;
                document.getElementById('display').value = eval(display);
            } catch (e) {
                document.getElementById('display').value = 'Error';
            }
        }

        document.addEventListener('keydown', function(event) {
            const key = event.key;
            if (key >= '0' && key <= '9') {
                appendNumber(key);
            } else if (key === '+' || key === '-' || key === '*' || key === '/') {
                appendOperator(key);
            } else if (key === 'Enter') {
                calculate();
            } else if (key === 'Escape') {
                clearDisplay();
            } else if (key === '.') {
                appendNumber('.');
            }
        });
    </script>
</body>
</html>
