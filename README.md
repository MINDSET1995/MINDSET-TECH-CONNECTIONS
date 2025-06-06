<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>MINDSET TECH CONNECTIONS - Digital Services</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
      background-color: #e6f7ff; /* Light Blue */
    }

    .banner {
      padding: 20px;
      background: linear-gradient(90deg, #a8e6a2, #7cd87c); /* Light Green */
      color: white;
    }

    .banner h1 {
      margin: 0;
      font-size: 28px;
      font-weight: bold;
      letter-spacing: 2px;
      color: #ff6600; /* Orange */
    }

    .banner p {
      margin: 5px 0 0;
      font-size: 14px;
      font-style: italic;
      color: #003366; /* Dark Blue */
    }

    .book {
      padding: 30px;
      margin: 30px auto;
      border: 1px solid #ddd;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 90%;
      width: 500px;
      background-color: #e6f7ff; /* Light Blue */
      border-radius: 10px;
    }

    h1, h3 {
      color: #1a7f3c;
    }

    em {
      color: #555;
      font-size: 15px;
    }

    button {
      padding: 12px 24px;
      font-size: 16px;
      margin-top: 20px;
      cursor: pointer;
      background-color: #28a745;
      color: white;
      border: none;
      border-radius: 5px;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: #1e7e34;
    }

    .service-list {
      text-align: left;
      margin-top: 20px;
    }

    .service-item {
      margin: 5px 0;
    }

    input[type="text"] {
      padding: 10px;
      width: 90%;
      margin-top: 15px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    #total {
      font-weight: bold;
      margin-top: 15px;
      color: #ff6600; /* Orange */
    }

    #paymentInstructions, #confirmButton {
      display: none;
      margin-top: 20px;
      text-align: left;
      color: #333;
    }

    #message {
      margin-top: 20px;
      color: green;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="banner">
    <h1>MINDSET TECH CONNECTIONS</h1>
    <p>Your Trusted Online Cyber Café</p>
  </div>

  <div class="book">
    <h1>Affordable Digital Services</h1>
    <p><em>Select services, enter your details, and follow payment instructions.</em></p>

    <!-- Service List -->
    <div class="service-list" id="serviceList">
      <label class="service-item"><input type="checkbox" value="KRA P9 Form - KES 400" data-price="400"> KRA P9 Form - KES 400</label><br>
      <label class="service-item"><input type="checkbox" value="KRA Nil Return - KES 100" data-price="100"> KRA Nil Return - KES 100</label><br>
      <label class="service-item"><input type="checkbox" value="NTSA Services - KES 300" data-price="300"> NTSA Services - KES 300</label><br>
      <label class="service-item"><input type="checkbox" value="eCitizen Services - KES 500" data-price="500"> eCitizen Services - KES 500</label><br>
      <label class="service-item"><input type="checkbox" value="Earphones - KES 100" data-price="100"> Earphones - KES 100</label><br>
      <label class="service-item"><input type="checkbox" value="Phone Chargers (Type C) - KES 200" data-price="200"> Phone Chargers (Type C) - KES 200</label><br>
      <label class="service-item"><input type="checkbox" value="Common Charges - KES 150" data-price="150"> Common Charges - KES 150</label><br>
      <label class="service-item"><input type="checkbox" value="Document Formatting - KES 100–500" data-price="300"> Document Formatting - KES 100–500</label><br>
      <label class="service-item"><input type="checkbox" value="Card Design - KES 300" data-price="300"> Card Design - KES 300</label><br>
      <label class="service-item"><input type="checkbox" value="Computer Hardware Support - KES 1000" data-price="1000"> Computer Hardware Support - KES 1000</label><br>
      <label class="service-item"><input type="checkbox" value="Computer Software Support - KES 1000" data-price="1000"> Computer Software Support - KES 1000</label>
    </div>

    <!-- Total Cost -->
    <p id="total">Total: KES 0</p>

    <!-- User Info -->
    <input type="text" id="fullName" placeholder="Your Full Name" required>

    <!-- Request Services -->
    <button onclick="buyServices()">Request Services</button>

    <!-- Payment Instructions -->
    <div id="paymentInstructions">
      <h3>Payment Instructions</h3>
      <p><strong>Send payment via M-Pesa to:</strong></p>
      <ul>
        <li><strong>Name:</strong> Mindset Tech Connections</li>
        <li><strong>Till Number:</strong> 9537119</li>
        <li><strong>Reference:</strong> Your Full Name + Services</li>
      </ul>
      <p>After payment, click below to confirm via WhatsApp.</p>
    </div>

    <!-- WhatsApp Confirmation -->
    <div id="confirmButton">
      <a id="whatsappLink" href="#" target="_blank" onclick="showConfirmationMessage()">
        <button>Confirm Payment</button>
      </a>
    </div>

    <!-- Confirmation Message -->
    <p id="message"></p>
  </div>

  <script>
    const checkboxes = document.querySelectorAll('#serviceList input[type="checkbox"]');
    const totalDisplay = document.getElementById('total');

    checkboxes.forEach(cb => cb.addEventListener('change', updateTotal));

    function updateTotal() {
      let total = 0;
      checkboxes.forEach(cb => {
        if (cb.checked) {
          total += parseInt(cb.getAttribute('data-price'));
        }
      });
      totalDisplay.innerText = `Total: KES ${total}`;
    }

    function buyServices() {
      const selected = Array.from(checkboxes).filter(cb => cb.checked);
      const fullName = document.getElementById('fullName').value.trim();

      if (selected.length === 0) {
        alert('Please select at least one service.');
        return;
      }

      if (!fullName) {
        alert('Please enter your full name.');
        return;
      }

      const serviceList = selected.map(cb => cb.value).join(', ');
      const encodedMessage = encodeURIComponent(
        `Hi Andrew, I’ve just paid for the following services: ${serviceList}. My name is ${fullName}. Kindly proceed.`
      );

      const whatsappLink = `https://wa.me/254726172770?text=${encodedMessage}`;
      document.getElementById('whatsappLink').href = whatsappLink;

      document.getElementById('paymentInstructions').style.display = 'block';
      document.getElementById('confirmButton').style.display = 'block';
      document.getElementById('message').innerText = "";
    }

    function showConfirmationMessage() {
      document.getElementById('message').innerText = "Confirmation sent! Andrew will contact you shortly.";
    }
  </script>

</body>
</html>
