<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pollo Park</title>
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
            margin-bottom: 10px;
        }

        .lang-toggle {
            margin-bottom: 30px;
        }

        .lang-toggle button {
            padding: 10px 20px;
            font-size: 16px;
            margin: 0 5px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .lang-toggle .active {
            background-color: #d4380d;
            color: white;
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
            margin: 40px 0;
        }

        #lbs-display {
            font-size: 40px;
            font-weight: bold;
            color: #d4380d;
            margin: 20px 0;
        }

        .slider-instruction {
            font-size: 20px;
            color: #333;
            margin-bottom: 20px;
            font-weight: bold;
        }

        input[type="range"] {
            width: 80%;
            height: 15px;
            border-radius: 8px;
            background: #ddd;
            outline: none;
        }

        input[type="range"]::-webkit-slider-thumb {
            appearance: none;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            background: #d4380d;
            cursor: pointer;
        }
    </style>
</head>

<body>

    <h1 data-en="Pollo Park" data-es="Pollo Park">Pollo Park</h1>

    <div class="lang-toggle">
        <button id="btn-en">English</button>
        <button id="btn-es" class="active">Español</button>
    </div>

    <div class="menu-section">
        <h2 data-en="Step 1: How Much Chicken? (pounds)" data-es="Paso 1: ¿Cuánta pollo quieres? (libras)">
            Paso 1: ¿Cuánta pollo quieres? (libras)
        </h2>
        <div class="slider-container">
            <p class="slider-instruction" data-en="👈 Slide the bar to choose the amount 👉"
                data-es="👈 Desliza la barra para elegir la cantidad 👉">
                👈 Desliza la barra para elegir la cantidad 👉
            </p>
            <div id="lbs-display">3 libras</div>
            <input type="range" id="lbs-slider" min="1" max="10" value="3" step="0.5">
            <p style="margin-top: 20px; color: #555;">
                <span data-en="Price for chicken:" data-es="Precio del pollo:"></span>
                $<span id="chicken-price">9.00</span>
                <small data-en="($3.00 per lb)" data-es="($3.00 por libra)">($3.00 por libra)</small>
            </p>
        </div>
    </div>

    <div class="menu-section">
        <h2 data-en="Step 2: Side Dish" data-es="Paso 2: Acompañamiento">
            Paso 2: Acompañamiento
        </h2>
        <div class="options" id="side-options">
            <div class="option" data-value-en="Plantain Chips" data-value-es="Chips de Plátano" data-extra="0">
                Chips de Plátano<br><span class="price-tag" data-en="Included" data-es="Incluido">Incluido</span>
            </div>
            <div class="option" data-value-en="Pasta" data-value-es="Pasta" data-extra="3">
                Pasta<br><span class="price-tag">+ $3.00</span>
            </div>
        </div>
    </div>

    <div class="menu-section">
        <h2 data-en="Step 3: Sauce" data-es="Paso 3: Salsa">
            Paso 3: Salsa
        </h2>
        <div class="options" id="sauce-options">
            <div class="option" data-value-en="Tomato Basil" data-value-es="Tomate Albahaca" data-extra="0">
                Tomate Albahaca<br><span class="price-tag" data-en="Included" data-es="Incluido">Incluido</span>
            </div>
            <div class="option" data-value-en="Alfredo" data-value-es="Alfredo" data-extra="0">
                Alfredo<br><span class="price-tag" data-en="Included" data-es="Incluido">Incluido</span>
            </div>
            <div class="option" data-value-en="Mixed Sauce" data-value-es="Salsa Mixta" data-extra="1">
                Salsa Mixta<br><span class="price-tag">+ $1.00</span>
            </div>
        </div>
    </div>

    <div id="total-price">
        <span data-en="Total Price:" data-es="Precio Total:">Precio Total:</span>
        <span id="price-display">$9.00</span>
    </div>

    <button id="whatsapp-button" data-en="Order on WhatsApp 📱" data-es="Ordenar por WhatsApp 📱">
        Ordenar por WhatsApp 📱
    </button>

    <script>
        // === CHANGE PRICE PER POUND HERE ===
        const PRICE_PER_LB = 3.00;  // $3.00 per pound

        // Replace with your real WhatsApp number (international format, no +)
        const YOUR_WHATSAPP_NUMBER = '593986785366';

        let currentLang = 'es'; // Default: Spanish
        let selections = {
            lbs: 3,
            side: '',
            sauce: ''
        };

        let extraSide = 0;
        let extraSauce = 0;

        const lbsSlider = document.getElementById('lbs-slider');
        const lbsDisplay = document.getElementById('lbs-display');
        const chickenPriceDisplay = document.getElementById('chicken-price');

        function updateAll() {
            selections.lbs = parseFloat(lbsSlider.value);
            lbsDisplay.textContent = selections.lbs.toFixed(1) + (currentLang === 'es' ? ' libras' : ' lbs');

            const chickenPrice = selections.lbs * PRICE_PER_LB;
            chickenPriceDisplay.textContent = chickenPrice.toFixed(2);

            const total = chickenPrice + extraSide + extraSauce;
            document.getElementById('price-display').textContent = '$' + total.toFixed(2);

            if (selections.side && selections.sauce) {
                document.getElementById('whatsapp-button').style.display = 'block';
            } else {
                document.getElementById('whatsapp-button').style.display = 'none';
            }
        }

        function switchLanguage(lang) {
            currentLang = lang;
            document.querySelectorAll('[data-en]').forEach(el => {
                el.textContent = el[`data-${lang}`] || el.textContent;
            });
            document.querySelectorAll('[data-value-en]').forEach(el => {
                const optionText = el.querySelector('div, span'); // find main text
                if (optionText && !optionText.classList.contains('price-tag')) {
                    optionText.childNodes[0].textContent = el[`data-value-${lang}`];
                }
            });
            document.getElementById('btn-en').classList.toggle('active', lang === 'en');
            document.getElementById('btn-es').classList.toggle('active', lang === 'es');
            document.documentElement.lang = lang;
            updateAll(); // refresh lbs text
        }

        function generateWhatsAppLink() {
            const chickenPrice = selections.lbs * PRICE_PER_LB;
            const total = chickenPrice + extraSide + extraSauce;

            const sideText = document.querySelector('#side-options .selected div, #side-options .selected span')
                .childNodes[0].textContent.trim();
            const sauceText = document.querySelector('#sauce-options .selected div, #sauce-options .selected span')
                .childNodes[0].textContent.trim();

            const message = currentLang === 'es'
                ? `¡Hola Shellychicken! Quiero ordenar:\n\n${selections.lbs.toFixed(1)} libras de pollo\nAcompañamiento: ${sideText}\nSalsa: ${sauceText}\n\nTotal: \[ {total.toFixed(2)}\n\n¡Gracias!`
                : `Hi Shellychicken! I'd like to order:\n\n${selections.lbs.toFixed(1)} lbs of chicken\nSide: ${sideText}\nSauce: ${sauceText}\n\nTotal: \]{total.toFixed(2)}\n\nThank you!`;

            const encodedMessage = encodeURIComponent(message);
            return `https://wa.me/\( {YOUR_WHATSAPP_NUMBER}?text= \){encodedMessage}`;
        }

        // Language buttons
        document.getElementById('btn-en').addEventListener('click', () => switchLanguage('en'));
        document.getElementById('btn-es').addEventListener('click', () => switchLanguage('es'));

        // Side selection
        document.getElementById('side-options').addEventListener('click', function (e) {
            const clicked = e.target.closest('.option');
            if (!clicked) return;
            this.querySelectorAll('.option').forEach(opt => opt.classList.remove('selected'));
            clicked.classList.add('selected');
            selections.side = clicked.querySelector('div, span').childNodes[0].textContent.trim();
            extraSide = parseFloat(clicked.dataset.extra || 0);
            updateAll();
        });

        // Sauce selection
        document.getElementById('sauce-options').addEventListener('click', function (e) {
            const clicked = e.target.closest('.option');
            if (!clicked) return;
            this.querySelectorAll('.option').forEach(opt => opt.classList.remove('selected'));
            clicked.classList.add('selected');
            selections.sauce = clicked.querySelector('div, span').childNodes[0].textContent.trim();
            extraSauce = parseFloat(clicked.dataset.extra || 0);
            updateAll();
        });

        // Slider
        lbsSlider.addEventListener('input', updateAll);

        // WhatsApp button
        document.getElementById('whatsapp-button').addEventListener('click', function () {
            const link = generateWhatsAppLink();
            window.open(link, '_blank');
        });

        // Initial load
        updateAll();
    </script>

</body>

</html>
