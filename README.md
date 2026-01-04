<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pollo Park Menu</title>
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
            max-width: 700px;
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
            position: relative;
        }

        .option:hover {
            background-color: #fff3e6;
        }

        .option.selected {
            border-color: #d4380d;
            background-color: #ffe6d9;
        }

        .price-tag {
            font-weight: bold;
            color: #d4380d;
            font-size: 18px;
            margin-top: 8px;
        }

        .quantity-controls {
            position: absolute;
            top: -15px;
            right: -15px;
            background: white;
            border: 3px solid #d4380d;
            border-radius: 50px;
            padding: 5px 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 2px 6px rgba(0, 0, 0, 0.2);
            font-weight: bold;
            font-size: 20px;
        }

        .quantity-controls button {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            width: 30px;
            height: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .quantity-controls button:disabled {
            color: #aaa;
            cursor: not-allowed;
        }

        .quantity-controls button:hover:not(:disabled) {
            color: #d4380d;
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

        .limit-note {
            font-size: 18px;
            color: #d4380d;
            font-weight: bold;
            margin-top: 20px;
            background-color: #ffe6d9;
            padding: 15px;
            border-radius: 8px;
            line-height: 1.6;
        }

        /* Donation Section */
        .donation-section {
            background-color: white;
            border-radius: 10px;
            padding: 30px;
            margin: 40px auto;
            max-width: 700px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
        }

        #donation-reminder {
            font-size: 18px;
            font-weight: bold;
            color: #d4380d;
            margin-bottom: 20px;
            line-height: 1.5;
        }

        .gfm-embed {
            width: 100%;
            max-width: 500px;
            margin: 0 auto;
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
        <h2 data-en="Step 1: How Much Chicken? (pounds)" data-es="Paso 1: ¿Cuánto pollo quieres? (libras)">
            Paso 1: ¿Cuánto pollo quieres? (libras)
        </h2>
        <div class="slider-container">
            <p class="slider-instruction" data-en="👈 Slide the bar to choose the amount 👉"
                data-es="👈 Desliza la barra para elegir la cantidad 👉">
                👈 Desliza la barra para elegir la cantidad 👉
            </p>
            <div id="lbs-display">3.00 libras</div>
            <input type="range" id="lbs-slider" min="1" max="10" value="3" step="0.25">
            <p style="margin-top: 20px; color: #555;">
                <span data-en="Chicken price:" data-es="Precio del pollo:"></span>
                $<span id="chicken-price">9.00</span>
                <small data-en="($3.00 per lb)" data-es="($3.00 por libra)">($3.00 por libra)</small>
            </p>
            <!-- <p class="limit-note" id="limits-note"></p> -->
        </div>
    </div>

    <div class="menu-section">
        <h2 data-en="Step 2: Sides (click to add, then use +/−)"
            data-es="Paso 2: Acompañamientos (toca para agregar, luego usa +/−)">
            Paso 2: Acompañamientos (toca para agregar, luego usa +/−)
        </h2>
        <div class="options" id="side-options">
            <div class="option" data-name-en="Plantain Chips" data-name-es="Chips de Plátano" data-price="0">
                Chips de Plátano<br><span class="price-tag" data-en="Free each" data-es="Gratis cada uno">Gratis cada
                    uno</span>
            </div>
            <div class="option" data-name-en="Pasta" data-name-es="Pasta" data-price="3">
                Pasta<br><span class="price-tag">+ $3.00 c/u</span>
            </div>
        </div>
    </div>

    <div class="menu-section">
        <h2 data-en="Step 3: Sauces (click to add, then use +/−)"
            data-es="Paso 3: Salsas (toca para agregar, luego usa +/−)">
            Paso 3: Salsas (toca para agregar, luego usa +/−)
        </h2>
        <div class="options" id="sauce-options">
            <div class="option" data-name-en="Tomato Basil" data-name-es="Tomate Albahaca" data-price="0">
                Tomate Albahaca<br><span class="price-tag" data-en="Free each" data-es="Gratis cada una">Gratis cada
                    una</span>
            </div>
            <div class="option" data-name-en="Alfredo" data-name-es="Alfredo" data-price="0">
                Alfredo<br><span class="price-tag" data-en="Free each" data-es="Gratis cada una">Gratis cada una</span>
            </div>
            <div class="option" data-name-en="Mixed Sauce" data-name-es="Salsa Mixta" data-price="1">
                Salsa Mixta<br><span class="price-tag">+ $1.00 c/u</span>
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

    <!-- DONATION SECTION -->
    <div class="donation-section">
        <div id="donation-reminder" data-en="Please make your payment in the form of a donation through the link below:"
            data-es="Por favor, haga su pago en forma de donación a través del enlace abajo:">
            Por favor, haga su pago en forma de donación a través del enlace abajo:
        </div>

        <div class="gfm-embed"
            data-url="https://www.gofundme.com/f/nutritious-meals-for-guayaquils-children/widget/large?sharesheet=undefined&attribution_id=sl:f568b931-52c2-46f4-bbe9-40f94caa815a">
        </div>
    </div>

    <script defer src="https://www.gofundme.com/static/js/embed.js"></script>

    <script>
        // === CHANGE PRICES HERE ===
        const PRICE_PER_LB = 3.00;
        const PASTA_PRICE = 3.00;
        const MIXED_SAUCE_PRICE = 1.00;

        const YOUR_WHATSAPP_NUMBER = 'YOUR_PHONE_NUMBER_HERE';

        let currentLang = 'es';
        let selections = {
            lbs: 3.0,
            sides: {},
            sauces: {}
        };

        const lbsSlider = document.getElementById('lbs-slider');
        const lbsDisplay = document.getElementById('lbs-display');
        const chickenPriceDisplay = document.getElementById('chicken-price');
        const limitsNote = document.getElementById('limits-note');

        function getTotalSides() {
            return Object.values(selections.sides).reduce((a, b) => a + b, 0);
        }

        function getTotalSauces() {
            return Object.values(selections.sauces).reduce((a, b) => a + b, 0);
        }

        function getMaxAllowed() {
            return Math.floor(selections.lbs);
        }

        function updatePlusButtons() {
            const max = getMaxAllowed();
            const totalSides = getTotalSides();
            const totalSauces = getTotalSauces();

            document.querySelectorAll('#side-options .plus').forEach(btn => {
                btn.disabled = totalSides >= max;
            });
            document.querySelectorAll('#sauce-options .plus').forEach(btn => {
                btn.disabled = totalSauces >= max;
            });
        }

        function createQuantityControls(option, qty = 0) {
            const controls = document.createElement('div');
            controls.className = 'quantity-controls';
            controls.innerHTML = `
                <button class="minus">−</button>
                <span class="qty">${qty}</span>
                <button class="plus">+</button>
            `;
            option.appendChild(controls);

            controls.querySelector('.minus').addEventListener('click', (e) => {
                e.stopPropagation();
                updateQuantity(option, -1);
            });
            controls.querySelector('.plus').addEventListener('click', (e) => {
                e.stopPropagation();
                updateQuantity(option, 1);
            });

            return controls;
        }

        function updateQuantity(option, change) {
            const isSide = option.parentElement.id === 'side-options';
            const collection = isSide ? selections.sides : selections.sauces;
            const nameKey = currentLang === 'en' ? 'En' : 'Es';
            const name = option.dataset[`name${nameKey}`];
            const current = collection[name] || 0;
            let newQty = current + change;

            if (newQty < 0) newQty = 0;

            const max = getMaxAllowed();
            const currentTotal = isSide ? getTotalSides() : getTotalSauces();
            if (change > 0 && currentTotal >= max) {
                return;
            }

            if (newQty === 0) {
                delete collection[name];
                option.classList.remove('selected');
                const controls = option.querySelector('.quantity-controls');
                if (controls) controls.remove();
            } else {
                collection[name] = newQty;
                option.classList.add('selected');
                let controls = option.querySelector('.quantity-controls');
                if (!controls) controls = createQuantityControls(option, newQty);
                controls.querySelector('.qty').textContent = newQty;
            }

            updateAll();
        }

        function updateAll() {
            selections.lbs = parseFloat(lbsSlider.value);
            lbsDisplay.textContent = selections.lbs.toFixed(2) + (currentLang === 'es' ? ' libras' : ' lbs');

            const chickenPrice = selections.lbs * PRICE_PER_LB;
            chickenPriceDisplay.textContent = chickenPrice.toFixed(2);

            const max = getMaxAllowed();
            const remainingSides = max - getTotalSides();
            const remainingSauces = max - getTotalSauces();

            limitsNote.innerHTML = currentLang === 'es'
                ? `¡Buena elección! Con \( {selections.lbs.toFixed(2)} libras de pollo, puedes agregar hasta <strong> \){max} acompañamientos</strong> (te quedan \( {remainingSides}) y hasta <strong> \){max} salsas</strong> (te quedan ${remainingSauces}).`
                : `Great choice! With \( {selections.lbs.toFixed(2)} lbs of chicken, you can add up to <strong> \){max} sides</strong> (\( {remainingSides} left) and up to <strong> \){max} sauces</strong> (${remainingSauces} left).`;

            let extras = 0;
            Object.keys(selections.sides).forEach(name => {
                const opt = [...document.querySelectorAll('#side-options .option')].find(o => o.dataset[`name${currentLang === 'en' ? 'En' : 'Es'}`] === name);
                extras += selections.sides[name] * parseFloat(opt.dataset.price);
            });
            Object.keys(selections.sauces).forEach(name => {
                const opt = [...document.querySelectorAll('#sauce-options .option')].find(o => o.dataset[`name${currentLang === 'en' ? 'En' : 'Es'}`] === name);
                extras += selections.sauces[name] * parseFloat(opt.dataset.price);
            });

            const total = chickenPrice + extras;
            document.getElementById('price-display').textContent = '$' + total.toFixed(2);

            const hasExtras = Object.keys(selections.sides).length > 0 || Object.keys(selections.sauces).length > 0;
            document.getElementById('whatsapp-button').style.display = hasExtras ? 'block' : 'none';

            updatePlusButtons();
        }

        function switchLanguage(lang) {
            currentLang = lang;
            document.querySelectorAll('[data-en]').forEach(el => {
                el.textContent = el[`data-${lang}`] || el.textContent;
            });
            document.querySelectorAll('[data-name-en]').forEach(option => {
                const mainText = option.querySelector('br').previousSibling;
                if (mainText) mainText.textContent = option[`data-name-${lang}`] + ' ';
            });
            document.getElementById('btn-en').classList.toggle('active', lang === 'en');
            document.getElementById('btn-es').classList.toggle('active', lang === 'es');
            document.documentElement.lang = lang;
            updateAll();
        }

        function generateWhatsAppLink() {
            const chickenPrice = selections.lbs * PRICE_PER_LB;
            let extras = 0;
            let orderLines = [];

            orderLines.push(`${selections.lbs.toFixed(2)} ${currentLang === 'es' ? 'libras de pollo' : 'lbs of chicken'}`);

            Object.keys(selections.sides).forEach(name => {
                const qty = selections.sides[name];
                orderLines.push(`${qty}× ${name}`);
                const opt = [...document.querySelectorAll('#side-options .option')].find(o => o.dataset[`name${currentLang === 'en' ? 'En' : 'Es'}`] === name);
                extras += qty * parseFloat(opt.dataset.price);
            });
            Object.keys(selections.sauces).forEach(name => {
                const qty = selections.sauces[name];
                orderLines.push(`${qty}× ${name}`);
                const opt = [...document.querySelectorAll('#sauce-options .option')].find(o => o.dataset[`name${currentLang === 'en' ? 'En' : 'Es'}`] === name);
                extras += qty * parseFloat(opt.dataset.price);
            });

            const total = chickenPrice + extras;

            const message = currentLang === 'es'
                ? `¡Hola Pollo Park! Quiero ordenar:\n\n` + orderLines.join('\n') + `\n\nTotal: \[ {total.toFixed(2)}\n\n¡Gracias!`
                : `Hi Pollo Park! I'd like to order:\n\n` + orderLines.join('\n') + `\n\nTotal: \]{total.toFixed(2)}\n\nThank you!`;

            return `https://wa.me/\( {YOUR_WHATSAPP_NUMBER}?text= \){encodeURIComponent(message)}`;
        }

        document.querySelectorAll('.option').forEach(option => {
            option.addEventListener('click', () => {
                const isSide = option.parentElement.id === 'side-options';
                const currentTotal = isSide ? getTotalSides() : getTotalSauces();
                if (currentTotal < getMaxAllowed()) {
                    updateQuantity(option, 1);
                }
            });
        });

        document.getElementById('btn-en').addEventListener('click', () => switchLanguage('en'));
        document.getElementById('btn-es').addEventListener('click', () => switchLanguage('es'));

        lbsSlider.addEventListener('input', updateAll);

        document.getElementById('whatsapp-button').addEventListener('click', () => {
            window.open(generateWhatsAppLink(), '_blank');
        });

        // Update prices from constants
        document.querySelector('#side-options .option[data-name-en="Pasta"]').dataset.price = PASTA_PRICE;
        document.querySelector('#sauce-options .option[data-name-en="Mixed Sauce"]').dataset.price = MIXED_SAUCE_PRICE;

        updateAll();
    </script>

</body>

</html>
