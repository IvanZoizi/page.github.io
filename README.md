<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            color: var(--tg-theme-text-color);
            background: var(--tg-theme-bg-color);
        }

        .Main {
            width: 100%;
            padding: 25px;
            text-align: center;

        }

        h1 {
            margin-top: 40px;
            margin-bottom: 10px;
        }

        img {
            width: 70px;
            margin: 30px auto;
        }

        .btn {
            border: 0;
            border-radius: 5px;
            margin-top: 50px;
            height: 60px;
            width: 200px;
            font-style: 20px;
            font-weight: 500;
            cursor: pointer;
            color: var(--tg-theme-button-text-color);
            background: var(--tg-theme-button-color);
        }

        form {
            display: none;
            text-align: center;
        }

        input {
            outline: none;
            border-radius: 5px;
            border: 2px solid #535353;
            padding: 15px 10px;
            margin: 10px 0 0;
            background: var(--tg-theme-section-separator-color);
            color: var(--tg-theme-text-color);
            transition: all .2s;
        }

        input:focus {
            border-color: var(--tg-theme-secondary-bg-color)
        }

    </style>
</head>
<body>
    <div class="Main">
        <h1>Тестовое приложение</h1>
        <img src="{{ url_for('static', filename='bot.png') }}" alt="">
        <p></p>
        <button class="btn f-btn">Тест отправки данных</button>
    </div>
    <form class="test-form">
        <input type="text" placeholder="Введите заголовок" class="title-inp">
        <input type="text" placeholder="Введите описание" class="desc-inp">
        <input type="text" placeholder="Введите текст" class="text-inp">
        <button class="btn s-btn">Отправить</button>
    </form>

    <script src="https://telegram.org/js/telegram-web-app.js"></script>

    <script>
        let tg = window.Telegram.WebApp;

        let fBtn = document.getElementsByClassName("f-btn")[0]
        let sBtn = document.getElementsByClassName("s-btn")[0]

        fBtn.addEventListener("click", () => {
            document.getElementsByClassName("Main")[0].style.display = "none";
            document.getElementsByClassName("test-form")[0].style.display = "block";
        });

        sBtn.addEventListener("click", () => {
            let title = document.getElementsByClassName("title-inp")[0];
            let description = document.getElementsByClassName("desc-inp")[0];
            let text = document.getElementsByClassName("text-inp")[0];


            let data = {
                title: title.value,
                desc: description.value,
                text: text.value
            }

            tg.sendData(JSON.stringify(data));
        });
    </script>
</body>
</html>
