<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pollo HollyWood Menu</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8f8f8;
            margin: 0;
            padding: 20px;
            text-align: center;
        }

        h1 {
            color: #d4380d;
            margin-bottom: 30px;
        }

        .menu-section {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            margin: 20px auto;
            max-width: 600px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        h2 {
            color: #d4380d;
            border-bottom: 2px solid #d4380d;
            padding-bottom: 10px;
        }

        .options {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            margin: 30px 0;
        }

        .option {
            padding: 20px;
            border: 3px solid #ccc;
            border-radius: 10px;
            cursor: pointer;
            width: 180px;
            transition: all 0.3s;
        }

        .option:hover {
            background-color: #fff3e6;
        }

        .option.selected {
            border-color: #d4380d;
            background-color: #ffe6d9;
            font-weight: bold;
        }

        .price-tag {
            font-weight: bold;
            color: #d4380d;
            font-size: 18px;
            margin-top: 8px;
        }

        #total-price {
            font-size: 28px;
            font-weight: bold;
            color: #d4380d;
            margin: 40px 0;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        #whatsapp-button {
            margin: 30px auto;
            padding: 15px 30px;
            font-size: 24px;
            background-color: #25D366;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            display: none;
        }

        #whatsapp-button:hover {
            background-color: #128C7E;
        }

        .slider-container {
            margin: 30px 0;
        }

        #grams-display {
            font-size: 32px;
            font-weight: bold;
            color: #d4380d;
            margin-bottom: 10px;
        }

        input[type="range"] {
            width: 80%;
            height: 10px;
            border-radius: 5px;
            background: #ddd;
            outline: none;
        }

        input[type="range"]::-webkit-slider-thumb {
            appearance: none;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: #d4380d;
            cursor: pointer;
        }
    </style>
</head>

<body>

    <h1>Pollo HollyWood</h1>

    <div class="menu-section">
        <h2>Paso 1: Cantidad de pollo (lbs)</h2>
        <div class="slider-container">
            <div id="grams-display">5 lbs</div>
            <h2>Delezar<h2>
            <input type="range" id="grams-slider" min="1" max="10" value="5" step="1">
            <p style="margin-top: 20px; color: #555;">
                Price: $<span id="chicken-price">7.50</span>
                <small>($0.015 per .25/lb)</small>
            </p>
        </div>
    </div>

    <div class="menu-section">
        <h2>Paso 2: Acompañante</h2>
        <div class="options" id="side-options">
            <div class="option" data-value="Plantain Chips" data-extra="0">Tostones<br><span
                    class="price-tag">Included</span></div>
            <div class="option" data-value="Pasta" data-extra="3">Pasta<br><span class="price-tag">+ $3.00</span></div>
        </div>
    </div>

    <div class="menu-section">
        <h2>Paso 3: Salsa</h2>
        <div class="options" id="sauce-options">
            <div class="option" data-value="Tomato Basil" data-extra="0">Tomato Basil<br><span
                    class="price-tag">Included</span></div>
            <div class="option" data-value="Alfredo" data-extra="0">Alfredo<br><span class="price-tag">Included</span>
            </div>
            <div class="option" data-value="Mixed Sauce" data-extra="1">Mixed Sauce<br><span class="price-tag">+
                    $1.00</span></div>
        </div>
    </div>

    <div id="total-price">
        Total Price: <span id="price-display">$7.50</span>
    </div>

    <button id="whatsapp-button">Order on WhatsApp 📱</button>

    <script>
        // === CHANGE THIS TO SET YOUR CHICKEN PRICE ===
        const PRICE_PER_GRAM = 0.015;  // $0.015 per gram → 1000g = $15.00

        // Replace with your real WhatsApp number (international format, no + or spaces)
        const YOUR_WHATSAPP_NUMBER = '593986785366';

        let selections = {
            grams: 500,
            side: '',
            sauce: ''
        };

        let extraSide = 0;
        let extraSauce = 0;

        const gramsSlider = document.getElementById('grams-slider');
        const gramsDisplay = document.getElementById('grams-display');
        const chickenPriceDisplay = document.getElementById('chicken-price');

        function updateAll() {
            selections.grams = parseInt(gramsSlider.value);
            gramsDisplay.textContent = selections.grams + ' grams';

            const chickenPrice = selections.grams * PRICE_PER_GRAM;
            chickenPriceDisplay.textContent = chickenPrice.toFixed(2);

            const total = chickenPrice + extraSide + extraSauce;
            document.getElementById('price-display').textContent = '$' + total.toFixed(2);

            // Show button only when side and sauce are selected
            if (selections.side && selections.sauce) {
                document.getElementById('whatsapp-button').style.display = 'block';
            } else {
                document.getElementById('whatsapp-button').style.display = 'none';
            }
        }

        function generateWhatsAppLink() {
            const chickenPrice = selections.grams * PRICE_PER_GRAM;
            const total = chickenPrice + extraSide + extraSauce;

            const message = `Hola Pollo HollyWood! Me gustaría ordenar:\n\n` +
                `${selections.grams}g de pollo\n` +
                `Acomonantes: ${selections.side}\n` +
                `Salsa: ${selections.sauce}\n\n` +
                `Total: $${total.toFixed(2)}\n\n` +
                `Gracias!`;

            const encodedMessage = encodeURIComponent(message);
            return `https://wa.me/${YOUR_WHATSAPP_NUMBER}?text=${encodedMessage}`;
        }

        // Side selection
        document.getElementById('side-options').addEventListener('click', function (e) {
            const clicked = e.target.closest('.option');
            if (!clicked) return;

            this.querySelectorAll('.option').forEach(opt => opt.classList.remove('selected'));
            clicked.classList.add('selected');

            selections.side = clicked.dataset.value;
            extraSide = parseFloat(clicked.dataset.extra || 0);
            updateAll();
        });

        // Sauce selection
        document.getElementById('sauce-options').addEventListener('click', function (e) {
            const clicked = e.target.closest('.option');
            if (!clicked) return;

            this.querySelectorAll('.option').forEach(opt => opt.classList.remove('selected'));
            clicked.classList.add('selected');

            selections.sauce = clicked.dataset.value;
            extraSauce = parseFloat(clicked.dataset.extra || 0);
            updateAll();
        });

        // Slider
        gramsSlider.addEventListener('input', updateAll);

        // WhatsApp button
        document.getElementById('whatsapp-button').addEventListener('click', function () {
            const link = generateWhatsAppLink();
            window.open(link, '_blank');
        });

        // Initial calculation
        updateAll();
    </script>

</body>

</html>
