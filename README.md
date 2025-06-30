# phone-code-form
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Ввод номера и кода</title>
  <style>
    body { font-family: sans-serif; padding: 40px; background: #f2f2f2; }
    input, button { margin: 10px 0; padding: 10px; font-size: 16px; }
  </style>
</head>
<body>
  <h2>Введите ваш номер телефона:</h2>
  <input type="text" id="phone" placeholder="+374..." />
  <button onclick="savePhone()">Отправить номер</button>

  <div id="codeSection" style="display:none;">
    <h2>Введите код подтверждения:</h2>
    <input type="text" id="code" placeholder="Код" />
    <button onclick="saveCode()">Отправить код</button>
  </div>

  <script>
    let userPhone = '';

    function savePhone() {
      userPhone = document.getElementById('phone').value;
      console.log("Номер телефона:", userPhone);
      alert("Номер сохранён: " + userPhone);
      document.getElementById('codeSection').style.display = 'block';
    }

    function saveCode() {
      const userCode = document.getElementById('code').value;
      console.log("Введённый код:", userCode);
      alert("Код сохранён: " + userCode);
    }
  </script>
</body>
</html>
