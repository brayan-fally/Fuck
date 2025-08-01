<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Global Trading - Paiement en ligne</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f2f5f9;
      padding: 20px;
    }
    .container {
      max-width: 650px;
      background: white;
      margin: auto;
      padding: 30px;
      border-radius: 8px;
      box-shadow: 0 0 12px rgba(0,0,0,0.08);
    }
    h1 {
      text-align: center;
      color: #003366;
      margin-bottom: 25px;
    }
    label {
      font-weight: bold;
      margin-bottom: 10px;
      display: block;
    }
    select {
      width: 100%;
      padding: 10px;
      margin-bottom: 20px;
      font-size: 1rem;
      border-radius: 6px;
    }
    .payment-methods {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: space-between;
    }
    .method {
      flex: 1 1 45%;
      background: #0077cc;
      color: white;
      text-align: center;
      padding: 15px;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s;
    }
    .method:hover {
      background: #005fa3;
    }
    .message {
      margin-top: 25px;
      background: #e6f0ff;
      padding: 20px;
      border-radius: 6px;
      font-weight: 600;
      color: #003366;
      display: none;
    }
    .message p {
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Global Trading - Paiement en ligne</h1>

    <label for="language">Choisissez votre langue / Choose your language :</label>
    <select id="language">
      <option value="fr">Français</option>
      <option value="en">English</option>
    </select>

    <label>Sélectionnez un moyen de paiement :</label>
    <div class="payment-methods" id="methods">
      <div class="method" data-method="Orange Money">Orange Money</div>
      <div class="method" data-method="Mobile Money">Mobile Money</div>
      <div class="method" data-method="Moov">Moov</div>
      <div class="method" data-method="Wave">Wave</div>
      <div class="method" data-method="Mynita">Mynita</div>
      <div class="method" data-method="Natcash">Natcash</div>
      <div class="method" data-method="Airtel Money">Airtel Money</div>
      <div class="method" data-method="PayPal">PayPal</div>
      <div class="method" data-method="Virement bancaire">Virement bancaire</div>
      <div class="method" data-method="Western Union">Western Union</div>
      <div class="method" data-method="RIA France">RIA France</div>
      <div class="method" data-method="RFI BANQUE">RFI BANQUE</div>
      <div class="method" data-method="Zelle">Zelle</div>
      <div class="method" data-method="App Cash">App Cash</div>
      <div class="method" data-method="Google Pay">Google Pay</div>
    </div>

    <div class="message" id="response">
      <p id="thankyou-text"></p>
      <p id="contact-info"></p>
      <p id="proof-info"></p>
    </div>
  </div>

  <script>
    const languageSelect = document.getElementById('language');
    const methods = document.querySelectorAll('.method');
    const response = document.getElementById('response');
    const thankyouText = document.getElementById('thankyou-text');
    const contactInfo = document.getElementById('contact-info');
    const proofInfo = document.getElementById('proof-info');

    const text = {
      fr: {
        thankyou: method => `Merci d’avoir choisi le mode de paiement : ${method}`,
        contact: `Veuillez contacter le numéro WhatsApp +237686829074 pour obtenir les coordonnées du dépôt.`,
        proof: `Après votre dépôt, envoyez une capture d’écran à l’agent chez qui vous avez lancé votre investissement.`
      },
      en: {
        thankyou: method => `Thank you for choosing payment method: ${method}`,
        contact: `Please contact WhatsApp number +237686829074 to get the deposit details.`,
        proof: `After your deposit, please send a screenshot to the agent where you started your investment.`
      }
    };

    methods.forEach(button => {
      button.addEventListener('click', () => {
        const lang = languageSelect.value;
        const method = button.dataset.method;
        thankyouText.textContent = text[lang].thankyou(method);
        contactInfo.textContent = text[lang].contact;
        proofInfo.textContent = text[lang].proof;
        response.style.display = 'block';
      });
    });
  </script>
</body>
</html>
