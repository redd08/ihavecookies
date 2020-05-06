# jQuery Cookie Consent Plugin (WIP)

Легкий плагин jQuery, который отображает cookie &#x1F36A; сообщение о согласии в соответствии с требованиями государства. Плагин отображает сообщение при первом посещении пользователем вашего веб-сайта и, по умолчанию, снова через 30 дней с момента его последнего посещения.

Посетитель __должен__ кликнуть кнопку «Принять» во всплывающем окне, чтобы установить файл cookie, и тем самым предоставить свое согласие.

## Usage

Загрузите последнюю версию и включите ее на своей странице вместе с jQuery (1.7.4 или более новый).

```html
<script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/jquery/2.x.x/jquery.min.js"></script>
<script type="text/javascript" src="jquery.ihavecookies.min.js"></script>
```

Затем инициализируйте плагин, используя:

```javascript
// С настройками по-умолчанию
$('body').ihavecookies();

// Или изменив настройки
var options = {
    title: ...
}
$('body').ihavecookies(options);
```

Это добавит всплывающее окно cookie к тегу `<body>` с настройками по-умолчанию и стандартным сообщением.

### Настройки

Есть несколько вариантов, доступных для настройки:

Опция | Значение по-умолчанию | Описание
------ | ------------- | -----------
title | "Cookies & Privacy" | A custom title for the popup
message | "Cookies enable you to use shopping carts and to personalize your experience on our sites, tell us which parts of our websites people have visited, help us measure the effectiveness of ads and web searches, and give us insights into user behavior so we can improve our communications and products." | Add your own cookie message here, if you prefer not to use the default one. HTML can be included within this message.
link | "/privacy-policy" | Link to your privacy policy for more information
delay | 2000 | Time before the popup is displayed after page load (in milliseconds)
expires | 30 | Days for the cookie to expire
onAccept | function(){} | Optional callback function when 'Accept' button is clicked
uncheckBoxes | false | Unchecks all checkboxes on page load that have class .ihavecookies applied to them. Set to true to turn this option on
moreInfoLabel | 'More information' | Label for link to privacy policy
acceptBtnLabel | 'Accept All Cookies' | Label for accept cookies button
advancedBtnLabel | 'Customise Cookies' | Label for customise cookies button
cookieTypesTitle | 'Select cookies to accept' | Title for customise cookies section
fixedCookieTypeLabel | 'Necessary' | Label for the "necessary" cookie type
fixedCookieTypeDesc | 'These are cookies that are essential for the website to work correctly.' | Description for the "necessary" cookie type
cookieTypes | Array | Array of cookie types for which to show checkboxes for - See code example below.

### События

#### Повторное открытие сообщения

Используя `reinit` открыть ihavecookies при нажатии на элемент. Откроется сообщение с отмеченными ранее флажками.

```javascript
$('button').click(function(){
    $('body').ihavecookies(options, 'reinit');
});
```

### Пример

Приведенный ниже код показывает пример параметров типов файлов cookie.

```javascript
$('body').ihavecookies({
    // Дополнительный callback при нажатии кнопки «Принять»
    onAccept: function() {
        // Делайте все, что вам нужно здесь ...
    },

    // Массив типов файлов cookie, для которых отображаются флажки.
    // - type: Тип cookie. Это также метка, которая отображается.
    // - value: Значение флажка, чтобы его можно было легко определить в
    //          вашем приложении.
    // - description: Описание для этого типа файлов cookie. Отображается в
    //                title аттрибута.
    cookieTypes: [
        {
            type: 'Настройки сайта',
            value: 'preferences',
            description: 'Данные файлы cookie, связаны с настройками сайта, например, запоминание имени пользователя, темы сайта и т. д.'
        },
        {
            type: 'Analytics',
            value: 'analytics',
            description: 'Файлы cookie, связанные с посещениями сайта, типами браузеров и т. д.'
        },
        {
            type: 'Marketing',
            value: 'marketing',
            description: 'Файлы cookie, связанные с маркетингом, например информационные письма, социальные сети и т. д.'
        }
    ],
});
```

### Методы

`$.fn.ihavecookies.cookie()` возращает значение `cookieControlPrefs` cookie.

`$.fn.ihavecookies.preference(cookieTypeValue)` возвращает `true` если тип cookie принят, иначе `false`.

### Стили

Плагин не содержит CSS, поэтому его можно стилизовать на ваше усмотрение. Сообщение cookie имеет идентификатор `#gdpr-cookie-message`. Образец CSS можно посмотреть в  `example.css` файле.

### Cookie

Когда посетитель принимает сообщение, cookie `cookieControl` со значение `true` устанавливаются вместе с cookie `cookieControlPrefs` который содержит массив принятых типов файлов cookie, например, `["preferences","analytics"]`. Это позволит вам выполнить дополнительные проверки, где это необходимо на вашем сайте.

## Example

Пример сообщения о согласии на использование файлов cookie можно посмотреть по адресу https://iamketan.com.au или в прилагаемом  `example.html` файле.

## Author
[Ketan Mistry](https://iamketan.com.au) ([@ketanumistry](https://twitter.com/ketanumistry))

## License
Этот плагин доступен под лицензией MIT.
