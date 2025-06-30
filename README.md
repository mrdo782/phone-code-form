<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Ввод номера и кода</title>
  <style>
    /* Сброс и базовые стили */
    * {
      box-sizing: border-box;
    }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #667eea, #764ba2);
      min-height: 100vh;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      color: #fff;
    }
    .container {
      background: rgba(255, 255, 255, 0.1);
      padding: 30px 40px;
      border-radius: 12px;
      max-width: 400px;
      width: 100%;
      box-shadow: 0 8px 24px rgba(0,0,0,0.2);
      text-align: center;
    }
    h2 {
      margin-bottom: 24px;
      font-weight: 600;
    }
    input[type="text"] {
      width: 100%;
      padding: 12px 15px;
      margin: 12px 0 24px 0;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      outline: none;
      transition: box-shadow 0.3s ease;
    }
    input[type="text"]:focus {
      box-shadow: 0 0 8px 3px rgba(255, 255, 255, 0.6);
      background-color: rgba(255,255,255,0.15);
      color: #fff;
    }
    button {
      background-color: #5a3fbb;
      color: white;
      border: none;
      padding: 14px 28px;
      font-size: 16px;
      border-radius: 10px;
      cursor: pointer;
      font-weight: 600;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #7d5fff;
    }
    #codeSection {
      margin-top: 20px;
      display: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Введите ваш номер телефона</h2>
    <input type="text" id="phone" placeholder="+374 99 123456" />
    <button onclick="savePhone()">Отправить номер</button>

    <div id="codeSection">
      <h2>Введите код подтверждения</h2>
      <input type="text" id="code" placeholder="Код" />
      <button onclick="saveCode()">Отправить код</button>
    </div>
  </div>

  <script>
    let userPhone = '';

    function savePhone() {
      userPhone = document.getElementById('phone').value.trim();
      if (!userPhone) {
        alert('Пожалуйста, введите номер телефона');
        return;
      }
      alert('Номер сохранён: ' + userPhone);
      document.getElementById('codeSection').style.display = 'block';
    }

    function saveCode() {
      const userCode = document.getElementById('code').value.trim();
      if (!userCode) {
        alert('Пожалуйста, введите код подтверждения');
        return;
      }
      alert('Код сохранён: ' + userCode);
    }
  </script>
</body>
</html>
