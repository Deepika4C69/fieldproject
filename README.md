<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Restaurant Menu</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #e74c3c;
        }
        h2 {
            color: #2c3e50;
            border-bottom: 2px solid #e74c3c;
            padding-bottom: 5px;
        }
        .menu-category {
            margin-bottom: 30px;
        }
        .menu-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid #ddd;
        }
        .menu-item:last-child {
            border-bottom: none;
        }
        .item-name {
            font-weight: bold;
        }
        .item-price {
            font-style: italic;
            color: #e74c3c;
        }
        .description {
            font-size: 14px;
            color: #7f8c8d;
        }
        .order-summary, .payment-section {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .payment-section input {
            width: calc(100% - 20px);
            padding: 10px;
            margin: 5px 0;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Our Restaurant Menu</h1>
        <label for="language-select">Choose a language:</label>
        <select id="language-select" onchange="updateMenu()">
            <option value="en">English</option>
            <option value="es">Spanish</option>
            <option value="fr">French</option>
            <option value="de">German</option>
            <option value="it">Italian</option>
        </select>

        <div class="menu-category" id="appetizers">
            <h2>Appetizers</h2>
            <div class="menu-item">
                <input type="checkbox" id="appetizer1-checkbox" value="8.99">
                <span class="item-name" id="appetizer1">Bruschetta</span>
                <span class="item-price" id="appetizer1-price">$8.99</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="appetizer2-checkbox" value="9.49">
                <span class="item-name" id="appetizer2">Stuffed Mushrooms</span>
                <span class="item-price" id="appetizer2-price">$9.49</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="appetizer3-checkbox" value="11.99">
                <span class="item-name" id="appetizer3">Chicken Wings</span>
                <span class="item-price" id="appetizer3-price">$11.99</span>
            </div>
        </div>

        <div class="menu-category" id="main-course">
            <h2>Main Course</h2>
            <div class="menu-item">
                <input type="checkbox" id="main1-checkbox" value="22.99">
                <span class="item-name" id="main1">Grilled Salmon</span>
                <span class="item-price" id="main1-price">$22.99</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="main2-checkbox" value="24.99">
                <span class="item-name" id="main2">Steak Frites</span>
                <span class="item-price" id="main2-price">$24.99</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="main3-checkbox" value="17.99">
                <span class="item-name" id="main3">Pasta Primavera</span>
                <span class="item-price" id="main3-price">$17.99</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="main4-checkbox" value="19.99">
                <span class="item-name" id="main4">Chicken Parmesan</span>
                <span class="item-price" id="main4-price">$19.99</span>
            </div>
        </div>

        <div class="menu-category" id="desserts">
            <h2>Desserts</h2>
            <div class="menu-item">
                <input type="checkbox" id="dessert1-checkbox" value="7.99">
                <span class="item-name" id="dessert1">Tiramisu</span>
                <span class="item-price" id="dessert1-price">$7.99</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="dessert2-checkbox" value="6.49">
                <span class="item-name" id="dessert2">Cheesecake</span>
                <span class="item-price" id="dessert2-price">$6.49</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="dessert3-checkbox" value="8.49">
                <span class="item-name" id="dessert3">Chocolate Lava Cake</span>
                <span class="item-price" id="dessert3-price">$8.49</span>
            </div>
        </div>

        <div class="menu-category" id="drinks">
            <h2>Drinks</h2>
            <div class="menu-item">
                <input type="checkbox" id="drink1-checkbox" value="2.49">
                <span class="item-name" id="drink1">Coke</span>
                <span class="item-price" id="drink1-price">$2.49</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="drink2-checkbox" value="2.99">
                <span class="item-name" id="drink2">Iced Tea</span>
                <span class="item-price" id="drink2-price">$2.99</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="drink3-checkbox" value="7.99">
                <span class="item-name" id="drink3">House Wine</span>
                <span class="item-price" id="drink3-price">$7.99</span>
            </div>
            <div class="menu-item">
                <input type="checkbox" id="drink4-checkbox" value="9.99">
                <span class="item-name" id="drink4">Margarita</span>
                <span class="item-price" id="drink4-price">$9.99</span>
            </div>
        </div>

        <button onclick="calculateTotal()">Place Order</button>

        <div class="order-summary">
            <h2>Order Summary</h2>
            <div id="order-details"></div>
            <div id="total-cost"></div>
        </div>

        <div class="payment-section">
            <h2 id="payment-title">Payment Information</h2>
            <input type="text" id="card-name" placeholder="Name on Card" required>
            <input type="text" id="card-number" placeholder="Card Number" required>
            <input type="text" id="expiration-date" placeholder="MM/YY" required>
            <input type="text" id="cvv" placeholder="CVV" required>
            <button onclick="processPayment()">Pay Now</button>
        </div>
    </div>

    <script>
        const menu = {
            en: {
                appetizers: [
                    { name: "Bruschetta", price: "$8.99" },
                    { name: "Stuffed Mushrooms", price: "$9.49" },
                    { name: "Chicken Wings", price: "$11.99" }
                ],
                mainCourse: [
                    { name: "Grilled Salmon", price: "$22.99" },
                    { name: "Steak Frites", price: "$24.99" },
                    { name: "Pasta Primavera", price: "$17.99" },
                    { name: "Chicken Parmesan", price: "$19.99" }
                ],
                desserts: [
                    { name: "Tiramisu", price: "$7.99" },
                    { name: "Cheesecake", price: "$6.49" },
                    { name: "Chocolate Lava Cake", price: "$8.49" }
                ],
                drinks: [
                    { name: "Coke", price: "$2.49" },
                    { name: "Iced Tea", price: "$2.99" },
                    { name: "House Wine", price: "$7.99" },
                    { name: "Margarita", price: "$9.99" }
                ],
                payment: {
                    title: "Payment Information",
                    cardName: "Name on Card",
                    cardNumber: "Card Number",
                    expirationDate: "MM/YY",
                    cvv: "CVV",
                    payButton: "Pay Now"
                }
            },
            es: {
                appetizers: [
                    { name: "Bruschetta", price: "$8.99" },
                    { name: "Champiñones Rellenos", price: "$9.49" },
                    { name: "Alitas de Pollo", price: "$11.99" }
                ],
                mainCourse: [
                    { name: "Salmón a la Parrilla", price: "$22.99" },
                    { name: "Steak Frites", price: "$24.99" },
                    { name: "Pasta Primavera", price: "$17.99" },
                    { name: "Pollo a la Parmesana", price: "$19.99" }
                ],
                desserts: [
                    { name: "Tiramisú", price: "$7.99" },
                    { name: "Cheesecake", price: "$6.49" },
                    { name: "Pastel de Lava de Chocolate", price: "$8.49" }
                ],
                drinks: [
                    { name: "Coca-Cola", price: "$2.49" },
                    { name: "Té Helado", price: "$2.99" },
                    { name: "Vino de la Casa", price: "$7.99" },
                    { name: "Margarita", price: "$9.99" }
                ],
                payment: {
                    title: "Información de Pago",
                    cardName: "Nombre en la Tarjeta",
                    cardNumber: "Número de Tarjeta",
                    expirationDate: "MM/AA",
                    cvv: "CVV",
                    payButton: "Pagar Ahora"
                }
            },
            fr: {
                appetizers: [
                    { name: "Bruschetta", price: "$8.99" },
                    { name: "Champignons Farcis", price: "$9.49" },
                    { name: "Ailes de Poulet", price: "$11.99" }
                ],
                mainCourse: [
                    { name: "Saumon Grillé", price: "$22.99" },
                    { name: "Steak Frites", price: "$24.99" },
                    { name: "Pâtes Primavera", price: "$17.99" },
                    { name: "Poulet Parmesan", price: "$19.99" }
                ],
                desserts: [
                    { name: "Tiramisu", price: "$7.99" },
                    { name: "Cheesecake", price: "$6.49" },
                    { name: "Gâteau Fondant au Chocolat", price: "$8.49" }
                ],
                drinks: [
                    { name: "Coca-Cola", price: "$2.49" },
                    { name: "Thé Glacé", price: "$2.99" },
                    { name: "Vin de Maison", price: "$7.99" },
                    { name: "Margarita", price: "$9.99" }
                ],
                payment: {
                    title: "Informations de Paiement",
                    cardName: "Nom sur la Carte",
                    cardNumber: "Numéro de Carte",
                    expirationDate: "MM/AA",
                    cvv: "CVV",
                    payButton: "Payer Maintenant"
                }
            },
            de: {
                appetizers: [
                    { name: "Bruschetta", price: "$8.99" },
                    { name: "Gefüllte Champignons", price: "$9.49" },
                    { name: "Hähnchenflügel", price: "$11.99" }
                ],
                mainCourse: [
                    { name: "Gegrillter Lachs", price: "$22.99" },
                    { name: "Steak Frites", price: "$24.99" },
                    { name: "Pasta Primavera", price: "$17.99" },
                    { name: "Hähnchen Parmesan", price: "$19.99" }
                ],
                desserts: [
                    { name: "Tiramisu", price: "$7.99" },
                    { name: "Käsekuchen", price: "$6.49" },
                    { name: "Schokoladen-Lava-Kuchen", price: "$8.49" }
                ],
                drinks: [
                    { name: "Coca-Cola", price: "$2.49" },
                    { name: "Eistee", price: "$2.99" },
                    { name: "Hauswein", price: "$7.99" },
                    { name: "Margarita", price: "$9.99" }
                ],
                payment: {
                    title: "Zahlungsinformationen",
                    cardName: "Name auf der Karte",
                    cardNumber: "Kartennummer",
                    expirationDate: "MM/JJ",
                    cvv: "CVV",
                    payButton: "Jetzt Bezahlen"
                }
            },
            it: {
                appetizers: [
                    { name: "Bruschetta", price: "$8.99" },
                    { name: "Funghi Ripieni", price: "$9.49" },
                    { name: "Ali di Pollo", price: "$11.99" }
                ],
                mainCourse: [
                    { name: "Salmone Grigliato", price: "$22.99" },
                    { name: "Steak Frites", price: "$24.99" },
                    { name: "Pasta Primavera", price: "$17.99" },
                    { name: "Pollo alla Parmigiana", price: "$19.99" }
                ],
                desserts: [
                    { name: "Tiramisù", price: "$7.99" },
                    { name: "Cheesecake", price: "$6.49" },
                    { name: "Torta al Cioccolato", price: "$8.49" }
                ],
                drinks: [
                    { name: "Coca-Cola", price: "$2.49" },
                    { name: "Tè Freddo", price: "$2.99" },
                    { name: "Vino della Casa", price: "$7.99" },
                    { name: "Margarita", price: "$9.99" }
                ],
                payment: {
                    title: "Informazioni di Pagamento",
                    cardName: "Nome sulla Carta",
                    cardNumber: "Numero della Carta",
                    expirationDate: "MM/AA",
                    cvv: "CVV",
                    payButton: "Paga Ora"
                }
            }
        };

        function updateMenu() {
            const selectedLanguage = document.getElementById("language-select").value;
            const menuData = menu[selectedLanguage];

            // Update Appetizers
            document.getElementById("appetizer1").textContent = menuData.appetizers[0].name;
            document.getElementById("appetizer1-price").textContent = menuData.appetizers[0].price;
            document.getElementById("appetizer2").textContent = menuData.appetizers[1].name;
            document.getElementById("appetizer2-price").textContent = menuData.appetizers[1].price;
            document.getElementById("appetizer3").textContent = menuData.appetizers[2].name;
            document.getElementById("appetizer3-price").textContent = menuData.appetizers[2].price;

            // Update Main Course
            document.getElementById("main1").textContent = menuData.mainCourse[0].name;
            document.getElementById("main1-price").textContent = menuData.mainCourse[0].price;
            document.getElementById("main2").textContent = menuData.mainCourse[1].name;
            document.getElementById("main2-price").textContent = menuData.mainCourse[1].price;
            document.getElementById("main3").textContent = menuData.mainCourse[2].name;
            document.getElementById("main3-price").textContent = menuData.mainCourse[2].price;
            document.getElementById("main4").textContent = menuData.mainCourse[3].name;
            document.getElementById("main4-price").textContent = menuData.mainCourse[3].price;

            // Update Desserts
            document.getElementById("dessert1").textContent = menuData.desserts[0].name;
            document.getElementById("dessert1-price").textContent = menuData.desserts[0].price;
            document.getElementById("dessert2").textContent = menuData.desserts[1].name;
            document.getElementById("dessert2-price").textContent = menuData.desserts[1].price;
            document.getElementById("dessert3").textContent = menuData.desserts[2].name;
            document.getElementById("dessert3-price").textContent = menuData.desserts[2].price;

            // Update Drinks
            document.getElementById("drink1").textContent = menuData.drinks[0].name;
            document.getElementById("drink1-price").textContent = menuData.drinks[0].price;
            document.getElementById("drink2").textContent = menuData.drinks[1].name;
            document.getElementById("drink2-price").textContent = menuData.drinks[1].price;
            document.getElementById("drink3").textContent = menuData.drinks[2].name;
            document.getElementById("drink3-price").textContent = menuData.drinks[2].price;
            document.getElementById("drink4").textContent = menuData.drinks[3].name;
            document.getElementById("drink4-price").textContent = menuData.drinks[3].price;

            // Update Payment Section
            document.getElementById("payment-title").textContent = menuData.payment.title;
            document.getElementById("card-name").placeholder = menuData.payment.cardName;
            document.getElementById("card-number").placeholder = menuData.payment.cardNumber;
            document.getElementById("expiration-date").placeholder = menuData.payment.expirationDate;
            document.getElementById("cvv").placeholder = menuData.payment.cvv;
            document.querySelector(".payment-section button").textContent = menuData.payment.payButton;
        }

        function calculateTotal() {
            const checkboxes = document.querySelectorAll('input[type="checkbox"]');
            let total = 0;
            let orderDetails = '';

            checkboxes.forEach(checkbox => {
                if (checkbox.checked) {
                    const itemName = checkbox.nextElementSibling.textContent;
                    const itemPrice = parseFloat(checkbox.value);
                    total += itemPrice;
                    orderDetails += `${itemName}: $${itemPrice.toFixed(2)}<br>`;
                }
            });

            document.getElementById("order-details").innerHTML = orderDetails || "No items selected.";
            document.getElementById("total-cost").textContent = `Total Cost: $${total.toFixed(2)}`;
        }

        function processPayment() {
            const name = document.getElementById("card-name").value;
            const cardNumber = document.getElementById("card-number").value;
            const expirationDate = document.getElementById("expiration-date").value;
            const cvv = document.getElementById("cvv").value;

            if (name && cardNumber && expirationDate && cvv) {
                alert("Payment processed successfully!");
                // Here you can add further payment processing logic
            } else {
                alert("Please fill in all payment details.");
            }
        }
    </script>
</body>
</html>
