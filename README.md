<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Buy a Book</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      text-align: center;
      margin-top: 100px;
      background-color: #fffbea; /* Soft Cream Yellow */
    }
    .book {
      padding: 30px;
      border: 1px solid #ddd;
      display: inline-block;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 550px;
      background-color: #ffffff;
      border-radius: 10px;
    }
    h1, h3 {
      color: #c1121f; /* Deep Red */
    }
    em {
      color: #444;
      font-size: 15px;
    }
    button {
      padding: 12px 24px;
      font-size: 16px;
      margin-top: 20px;
      cursor: pointer;
      background-color: #0056b3; /* Royal Blue */
      color: white;
      border: none;
      border-radius: 5px;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #004494;
    }
    #paymentInstructions {
      display: none;
      margin-top: 20px;
      text-align: left;
      color: #333;
    }
    #confirmButton {
      display: none;
      margin-top: 20px;
    }
    ul {
      text-align: left;
      margin-left: 40px;
      color: #333;
    }
    a button {
      background-color: #0077cc;
    }
    a button:hover {
      background-color: #005fa3;
    }
  </style>
</head>
<body>

  <div class="book">
    <h1>The Mystery and the Power of the Holy Spirit</h1>
    <p><em>Designed to deepen your understanding and relationship with the Holy Spirit, this edition challenges and encourages Christians to live Spirit-filled lives with purpose and passion..</em></p>
    <p><strong>Price:</strong> KES 200</p>
    <button onclick="buyBook()">Buy Now</button>

    <div id="paymentInstructions">
      <h3>Payment Instructions</h3>
      <p><strong>Send KES 200 via M-Pesa to:</strong></p>
      <ul>
        <li><strong>Name:</strong> Mindset Tech Connections</li>
        <li><strong>Till Number:</strong> 9537119</li>
        <li><strong>Reference:</strong> Your Full Name</li>
      </ul>
      <p>After payment, click the button below to confirm via WhatsApp.</p>
    </div>

    <div id="confirmButton">
      <a href="https://wa.me/254726172770?text=Hi%20Andrew%2C%20I%E2%80%99ve%20just%20paid%20KES%20500%20for%20the%20eBook.%20Please%20send%20it%20to%20me." target="_blank">
        <button>Confirm Payment</button>
      </a>
    </div>

    <p id="message" style="color: green; font-weight: bold;"></p>
  </div>

  <script>
    function buyBook() {
      document.getElementById('paymentInstructions').style.display = 'block';
      document.getElementById('confirmButton').style.display = 'block';
      document.getElementById('message').innerText = "";
    }
  </script>

</body>
</html>
