<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hypoteční Kalkulačka</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 20px; }
        .container { max-width: 400px; margin: auto; padding: 20px; border: 1px solid #ccc; border-radius: 5px; }
        input, button { margin: 10px 0; width: 100%; padding: 10px; }
    </style>
</head>
<body>
    <div class="container">
        <h2>Hypoteční Kalkulačka</h2>
        <label for="amount">Výše úvěru (Kč):</label>
        <input type="number" id="amount" placeholder="Zadejte částku">
        
        <label for="rate">Úroková sazba (% ročně):</label>
        <input type="number" id="rate" placeholder="Zadejte úrok">
        
        <label for="years">Doba splácení (roky):</label>
        <input type="number" id="years" placeholder="Zadejte roky">
        
        <button onclick="calculateMortgage()">Spočítat</button>
        
        <h3 id="result"></h3>
    </div>

    <script>
        function calculateMortgage() {
            let amount = document.getElementById("amount").value;
            let rate = document.getElementById("rate").value / 100 / 12;
            let years = document.getElementById("years").value * 12;
            
            if (amount <= 0 || rate <= 0 || years <= 0) {
                document.getElementById("result").innerText = "Zadejte platné hodnoty!";
                return;
            }
            
            let monthlyPayment = (amount * rate) / (1 - Math.pow(1 + rate, -years));
            document.getElementById("result").innerText = "Měsíční splátka: " + monthlyPayment.toFixed(2) + " Kč";
        }
    </script>
</body>
</html>
