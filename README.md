<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Numeri Primi Colorati</title>
    <style>
        body {
            font-family: 'Verdana', sans-serif;
            text-align: center;
            background: linear-gradient(to right, #f9f9f9, #e8f0ff);
            color: #333;
            margin: 0;
            padding: 20px;
        }
        h1 {
            color: #4A90E2;
            font-size: 2em;
        }
        .numbers {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(50px, 1fr));
            gap: 15px;
            margin: 20px auto;
            max-width: 90%;
            padding: 10px;
            border: 2px solid #4A90E2;
            border-radius: 10px;
            background-color: #fff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .number {
            padding: 15px;
            font-size: 18px;
            text-align: center;
            border-radius: 6px;
            font-weight: bold;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: transform 0.2s;
        }
        .number:hover {
            transform: scale(1.1);
        }
        .prime {
            background-color: #FF6F61;
            color: white;
        }
        .non-prime {
            background-color: #D3E4CD;
            color: #333;
        }
    </style>
</head>
<body>
    <h1>Numeri da 1 a 1000 con Numeri Primi Evidenziati</h1>
    <div id="numbers" class="numbers"></div>

    <script>
        // Funzione per determinare se un numero è primo
        function crivelloEratostene(maxNum) {
            const isPrime = Array(maxNum + 1).fill(true);
            isPrime[0] = isPrime[1] = false; // 0 e 1 non sono numeri primi

            for (let i = 2; i * i <= maxNum; i++) {
                if (isPrime[i]) {
                    for (let j = i * i; j <= maxNum; j += i) {
                        isPrime[j] = false;
                    }
                }
            }
            return isPrime;
        }

        // Funzione principale per creare l'array da 1 a 1000 e colorare i numeri
        function colorareNumeriPrimi() {
            const maxNum = 1000;
            const isPrime = crivelloEratostene(maxNum);
            const numbersContainer = document.getElementById("numbers");

            for (let i = 1; i <= maxNum; i++) {
                const div = document.createElement("div");
                div.classList.add("number");

                // Aggiungi il colore in base se il numero è primo o meno
                if (isPrime[i]) {
                    div.classList.add("prime");
                    div.textContent = i; // Numero primo
                } else {
                    div.classList.add("non-prime");
                    div.textContent = i; // Numero non primo
                }

                // Aggiungi il numero alla griglia
                numbersContainer.appendChild(div);
            }
        }

        // Chiamata alla funzione principale
        colorareNumeriPrimi();
    </script>
</body>
</html>
