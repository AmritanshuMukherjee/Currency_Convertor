<!DOCTYPE html>
<html>
<head>
    <title>Currency Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            text-align: center;
            margin: 0;
            padding: 0;
        }

        h1 {
            color: #333;
            background-color: #ffc107;
            padding: 20px;
            margin: 0;
        }

        .container {
            max-width: 400px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
        }

        label {
            font-weight: bold;
            display: block;
            margin: 10px 0;
        }

        input, select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 3px;
        }

        button {
            background-color: #007bff;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        #result {
            margin: 20px 0;
            font-size: 18px;
            color: #333;
        }
    </style>
</head>
<body>
    <h1>Currency Converter</h1>

    <div class="container">
        <div>
            <label for="amount">Amount:</label>
            <input type="number" id="amount" placeholder="Enter amount" />
        </div>

        <div>
            <label for="from">From:</label>
            <select id="from"></select>
        </div>

        <div>
            <label for="to">To:</label>
            <select id="to"></select>
        </div>

        <div>
            <button onclick="convertCurrency()">Convert</button>
        </div>

        <div id="result"></div>
    </div>
    <script>
        const currencies = [
            "USD", "EUR", "GBP", "JPY", "CAD", "AUD", "CHF", "CNY", "SGD", "INR", "AED", "AFN", "ALL", "AMD", "ANG", "AOA", "ARS", "AUD", "AWG" // Add more currencies as needed
        ];

        const fromSelect = document.getElementById("from");
        const toSelect = document.getElementById("to");

        currencies.forEach(currency => {
            const optionFrom = document.createElement("option");
            optionFrom.value = currency;
            optionFrom.textContent = currency;
            fromSelect.appendChild(optionFrom);

            const optionTo = document.createElement("option");
            optionTo.value = currency;
            optionTo.textContent = currency;
            toSelect.appendChild(optionTo);
        });

        function convertCurrency() {
            const amount = parseFloat(document.getElementById("amount").value);
            const fromCurrency = document.getElementById("from").value;
            const toCurrency = document.getElementById("to").value;

            // Replace this part with a real exchange rate API

            // For simplicity, let's assume a simple conversion factor
            const conversionFactors = {
                "USD": 1,
                "EUR": 0.85,
                "GBP": 0.75,
                "JPY": 110,
                "CAD": 1.25,
                "AUD": 1.30,
                "CHF": 0.90,
                "CNY": 6.45,
                "SGD": 1.35,
                "INR": 73.50,
                "AED": 0.27,
                "AFN": 0.013,
                "ALL": 0.0100,
                "AMD": 0.0025,
                "ANG": 0.56,
                "AOA": 0.0012,
                "ARS": 0.0029,
                "AUD": 0.63,
                "AWG": 0.56,
                // Add more conversion factors for additional currencies
            };

            const exchangeRate = conversionFactors[toCurrency] / conversionFactors[fromCurrency];
            const result = (amount * exchangeRate).toFixed(2);
            document.getElementById("result").innerHTML = `${amount} ${fromCurrency} = ${result} ${toCurrency}`;
        }
    </script>
</body>
</html>
