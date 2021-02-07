# filmoteka

Team Project - under construction ...

test branch



## Deploying/Publishing

### Деплой сайту на хостинг

В нашому командному проекті було прийнято рішення використати платформу для хостінгу
веб-додатків Netlify. 
Із переваг хостингу через Netlify можна визначити:
1. Єдиний та презентабельніший вигляд url в порівнянні із GitHub.
2. Для коректної роботи Firebase домен сторінки має бути в списку довірених сайтів.
3. Кожен учасник команди зможе зробити собі копію репозиторію без необхідості повторно налаштовувати деплой на хостінг.
4. За умови машатабування проекту та додавання динамічної маршрутиизації це буде можливо зробити.


### Register on Netlify
 
Спочатку потрібно зарееструватися на Netlify. Бажано зробити це за допомогою акаунту GitHub,
оскільки це дасть більше цікавих можливостей в роботі.  

### Add netlify.toml

Далі додаємо в корінь проекту файл netlify.toml.
В даниий документ додаємо необхідні налаштування.

```json
[build]
    publish = "build"

[[redirects]]
    from = "/*"
    to = "/index.html"
    status = 200
```

### Netlify CLI і netlify-скрипти

Для деплою через npm-скрипти портрібно один раз глобально встановити Netlify CLI.
В терміналі виконуємо команду 

```shell
npx install netlify-cli -g
```

Далі отримуємо право доступу до свого netlify акаунту через термінал.
Виконуємо команду

```shell
netlify login
```
В браузері відкриється вкладка де необхідно підтвердити авторизацію.

Наступним кроком в нашому проекті в файлі package.json додаємо npm-скрипти для автоматичного деплою

```json
"predeploy": "npm run build",
"deploy": "netlify deploy -p" 
```

Також в файлі package.json необхідно видалити властивість "homepage".

### Deploy
 
Виконуємо команду:
```shell
npm run deploy
```
Спочатку атоматично запускається скрипт "predeploy" і робить свіжий білд додатку.

При перешому деплою на netlify необхідно створити та налаштувати проект.
Кнопками "вверх", "вниз" обираємо команду "+ Create & configure a new site".

Команду розробників обираємо за замовчуванням натиснувши Enter.

Далі обираємо назву сайту. Це має бути унікальний рядок. Рекомендується на початку або в кінці назви
дописати ваш логін на netlify, але це не обов'язково. Головне, щоб це було унікальне значення.

Через деякий час бачимо результат. Всі детальнашого проекту відображені в терміналі.
Також керування сайтом можна здійснити через браузер в акаунті netlify.

Для кожного наступного деплою вашого додатку виконуємо команду
```shell
npm run deploy
```
