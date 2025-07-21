<!DOCTYPE html><html lang="si">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cash One</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      padding: 40px;
      background-color: #f4f4f4;
    }
    .container {
      background-color: #fff;
      max-width: 400px;
      margin: 0 auto;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    input[type="number"] {
      width: 100%;
      padding: 12px;
      margin: 20px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      padding: 12px 25px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
    }
    button:disabled {
      background-color: #ccc;
      cursor: not-allowed;
    }
    #result {
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Cash One වෙත ඔබව සාදරයෙන් පිළිගන්නවා!</h2>
    <p>ඔබට රුපියල් 40000 සිට රුපියල් 700000 දක්වා මුදලක් ලබා ගැනීමට හැකියාවක් ඇත..කරුණාකර පහලින් ඇප්ලයි කරන්න!</p><label for="amount">මුදලක් සඳහන් කරන්න</label>
<input type="number" id="amount" placeholder="රු. 40000 - 700000">

<button id="applyBtn" disabled>Apply</button>

<div id="result"></div>

  </div>  <script>
    const amountInput = document.getElementById('amount');
    const applyBtn = document.getElementById('applyBtn');
    const result = document.getElementById('result');

    amountInput.addEventListener('input', () => {
      const amount = parseInt(amountInput.value);
      if (amount >= 40000 && amount <= 700000) {
        applyBtn.disabled = false;
      } else {
        applyBtn.disabled = true;
        result.innerHTML = "";
      }
    });

    applyBtn.addEventListener('click', () => {
      const amount = parseInt(amountInput.value);
      let months = 0;
      if (amount >= 40000 && amount < 80000) months = 6;
      else if (amount >= 80000 && amount < 200000) months = 12;
      else if (amount >= 200000 && amount < 400000) months = 24;
      else if (amount >= 400000 && amount <= 700000) months = 30;

      const totalInterest = amount * 0.07;
      const totalPayable = amount + totalInterest;
      const monthlyInstallment = (totalPayable / months).toFixed(2);

      result.innerHTML = `
        <p>මුළු ගෙවීම්: රු. ${totalPayable.toLocaleString()}</p>
        <p>මාසික වාරිකය (${months} මාස): රු. ${monthlyInstallment.toLocaleString()}</p>
      `;
    });
  </script></body>
</html>
