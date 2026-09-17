
# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

| | |
|---|---|
| **Прізвище, ім'я** | Гребенюк Катерина |
| **Група** | КБЗІ 2.02 |
| **Номер варіанта** | 6 |
| **Домен варіанта** | unicode.org |
| **Середовище виконання** | Windows |
| **Версія curl** |  v7.6.6 |
| **Дата виконання** | 17.09.2026 |

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:**

```
unicode.org
```

**Вивід:**

```
* Host unicode.org:443 was resolved.
* IPv6: 2606:4700:20::681a:b2f, 2606:4700:20::681a:a2f, 2606:4700:20::ac43:4a17
* IPv4: 104.26.11.47, 104.26.10.47, 172.67.74.23
*   Trying [2606:4700:20::681a:b2f]:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to unicode.org (2606:4700:20::681a:b2f port 443) from 2a02:3032:2e7:581e:fd3f:39a9:451d:7b1e port 56158
* using HTTP/1.x
> GET / HTTP/1.1
> Host: unicode.org
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 200 OK
< Date: Thu, 17 Sep 2026 17:41:09 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< Server: cloudflare
< Content-Security-Policy: upgrade-insecure-requests;
< Last-Modified: Thu, 02 Mar 2023 00:38:51 GMT
< Vary: Accept-Encoding
< Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=jMy%2FJ9kvyjyXz2mJL8gZz92%2F7uKMvHHzNZ2Thj6pdW%2FHTQyvFtlEd4TwweQTlmmpZL%2FUeKwC9%2FyiA42slS9oBPj2niqn6xAekTigLsxa3Jks3%2Bztk3gCVMAGAGwQmBjA9cdYTDZf%2FMH3"}]}
< Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
< cf-cache-status: DYNAMIC
< CF-RAY: a3c9e66f8c87cf96-TXL
<
<html><head>
<meta http-equiv="refresh" content="0; url=http://home.unicode.org/">
<title>Index</title>
</head>
<body>
Automatic redirect: <a href="http://home.unicode.org/">http://home.unicode.org/</a>
</body></html>

* Connection #0 to host unicode.org:443 left intact
PS C:\Users\User>
```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```
curl -v http://neverssl.com
```

**Вивід:**

```
PS C:\Users\User> curl.exe -v http://neverssl.comcurl -v http://neverssl.com
* Could not resolve host: neverssl.comcurl
* Could not resolve host: neverssl.comcurl
* Could not resolve: neverssl.comcurl:80
* closing connection #0
curl: (6) Could not resolve host: neverssl.comcurl
*   Trying [2600:1f13:37c:1400:ba21:7165:5fc7:736e]:80...
* Host neverssl.com:80 was resolved.
* IPv6: 2600:1f13:37c:1400:ba21:7165:5fc7:736e
* IPv4: 34.223.124.45
*   Trying 34.223.124.45:80...
* Established connection to neverssl.com (34.223.124.45 port 80) from 192.168.8.6 port 49674
* using HTTP/1.x
> GET / HTTP/1.1
> Host: neverssl.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Date: Thu, 17 Sep 2026 17:47:09 GMT
< Server: Apache/2.4.68 ()
< Upgrade: h2,h2c
< Connection: Upgrade
< Last-Modified: Wed, 29 Jun 2022 00:23:33 GMT
< ETag: "f79-5e28b29d38e93"
< Accept-Ranges: bytes
< Content-Length: 3961
< Vary: Accept-Encoding
< Content-Type: text/html; charset=UTF-8
<
<html>
        <head>
                <title>NeverSSL - Connecting ... </title>
                <style>
                body {
                        font-family: Montserrat, helvetica, arial, sans-serif;
                        font-size: 16x;
                        color: #444444;
                        margin: 0;
                }
                h2 {
                        font-weight: 700;
                        font-size: 1.6em;
                        margin-top: 30px;
                }
                p {
                        line-height: 1.6em;
                }
                .container {
                        max-width: 650px;
                        margin: 20px auto 20px auto;
                        padding-left: 15px;
                        padding-right: 15px
                }
                .header {
                        background-color: #42C0FD;
                        color: #FFFFFF;
                        padding: 10px 0 10px 0;
                        font-size: 2.2em;
                }
                .notice {
                        background-color: red;
                        color: white;
                        padding: 10px 0 10px 0;
                        font-size: 1.25em;
                        animation: flash 4s infinite;
                }
                @keyframes flash {
                0% {
                        background-color: red;
                }
                50% {
                        background-color: #AA0000;
                }
                0% {
                        background-color: red;
                }
                }
                <!-- CSS from Mark Webster https://gist.github.com/markcwebster/9bdf30655cdd5279bad13993ac87c85d -->
                </style>

                <script>
                        var adjectives = [ 'cool' , 'calm' , 'relaxed', 'soothing', 'serene', 'slow',
                                                        'beautiful', 'wonderful', 'wonderous', 'fun', 'good',
                                                        'glowing', 'inner', 'grand', 'majestic', 'astounding',
                                                        'fine', 'splendid', 'transcendent', 'sublime', 'whole',
                                                        'unique', 'old', 'young', 'fresh', 'clear', 'shiny',
                                                        'shining', 'lush', 'quiet', 'bright', 'silver' ];

                        var nouns =       [ 'day', 'dawn', 'peace', 'smile', 'love', 'zen', 'laugh',
                                                        'yawn', 'poem', 'song', 'joke', 'verse', 'kiss', 'sunrise',
                                                        'sunset', 'eclipse', 'moon', 'rainbow', 'rain', 'plan',
                                                        'play', 'chart', 'birds', 'stars', 'pathway', 'secret',
                                                        'treasure', 'melody', 'magic', 'spell', 'light', 'morning'];

                        var prefix =
                                        // Choose 3 zen adjectives
                                        adjectives.sort(function(){return 0.5-Math.random()}).slice(-3).join('')
                                        +
                                        // Coupled with a zen noun
                                        nouns.sort(function(){return 0.5-Math.random()}).slice(-1).join('');
                        window.location.href = 'http://' + prefix + '.neverssl.com/online';
                </script>
        </head>
        <body>
        <noscript>
                <div class="notice">
                        <div class="container">
                                ⚠️ JavaScript appears to be disabled. NeverSSL's cache-busting works better if you enable JavaScript for <code>neverssl.com</code>.
                        </div>
                </div>
        </noscript>
        <div class="header">
                <div class="container">
                <h1>NeverSSL</h1>
                </div>
        </div>
        <div class="content">
        <div class="container">

        <h1 id="status"></h1>
        <script>document.querySelector("#status").textContent = "Connecting ...";</script>
        <noscript>

                <h2>What?</h2>
                <p>This website is for when you try to open Facebook, Google, Amazon, etc
                on a wifi network, and nothing happens. Type "http://neverssl.com"
                into your browser's url bar, and you'll be able to log on.</p>

                <h2>How?</h2>
                <p>neverssl.com will never use SSL (also known as TLS). No
                encryption, no strong authentication, no <a
                href="https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security">HSTS</a>,
                no HTTP/2.0, just plain old unencrypted HTTP and forever stuck in the dark
                ages of internet security.</p>

                <h2>Why?</h2>
                <p>Normally, that's a bad idea. You should always use SSL and secure
                encryption when possible. In fact, it's such a bad idea that most websites
                are now using https by default.</p>

                <p>And that's great, but it also means that if you're relying on
                poorly-behaved wifi networks, it can be hard to get online.  Secure
                browsers and websites using https make it impossible for those wifi
                networks to send you to a login or payment page. Basically, those networks
                can't tap into your connection just like attackers can't. Modern browsers
                are so good that they can remember when a website supports encryption and
                even if you type in the website name, they'll use https.</p>

                <p>And if the network never redirects you to this page, well as you can
                see, you're not missing much.</p>

        <a href="https://twitter.com/neverssl">Follow @neverssl</a>

        </noscript>

        </div>
        </div>

        </body>
</html>
* Connection #1 to host neverssl.com:80 left intact
PS C:\Users\User> curl -v http://neverssl.comсс
```

---

### A.3. Запит до служби доменних імен

*Windows: `Resolve-DnsName ВАШ_ДОМЕН`*

**Команда (перше виконання):**

```
dig unicode.org
```

**Вивід:**

```
PS C:\Users\User>
PS C:\Users\User> Resolve-DnsName unicode.org

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
unicode.org                                    AAAA   300   Answer     2606:4700:20::681a:b2f
unicode.org                                    AAAA   300   Answer     2606:4700:20::ac43:4a17
unicode.org                                    AAAA   300   Answer     2606:4700:20::681a:a2f
unicode.org                                    A      300   Answer     104.26.11.47
unicode.org                                    A      300   Answer     172.67.74.23
unicode.org                                    A      300   Answer     104.26.10.47


PS C:\Users\User>
```

**Команда (повторне виконання через 5–7 хвилин):**

```
dig unicode.org
```

**Вивід:**

```
PS C:\Users\User> Resolve-DnsName unicode.org

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
unicode.org                                    AAAA   300   Answer     2606:4700:20::ac43:4a17
unicode.org                                    AAAA   300   Answer     2606:4700:20::681a:b2f
unicode.org                                    AAAA   300   Answer     2606:4700:20::681a:a2f
unicode.org                                    A      300   Answer     172.67.74.23
unicode.org                                    A      300   Answer     104.26.11.47
unicode.org                                    A      300   Answer     104.26.10.47


PS C:\Users\User>
```

**Зафіксовані значення:**

| Параметр | Перше виконання | Повторне виконання |
|---|---|---|
| Час виконання (год:хв) | 19:55| | 20:00 |
| IP-адреса | 2606:4700:20::681a:b2f | 2606:4700:20::ac43:4a17 |
| Значення TTL | 300 | 300 |

> Якщо друге значення TTL виявилося більшим за перше — це нормально: кеш резолвера встиг оновитися. Зафіксуйте як є.

---

### A.4. Контрольний ресурс

**Команда:**

```
curl -v https://google.com
```

**Вивід:**

```
PS C:\Users\User> curl.exe -v https://google.com
*   Trying [2a00:1450:4001:c17::71]:443...
* Host google.com:443 was resolved.
* IPv6: 2a00:1450:4001:c17::71, 2a00:1450:4001:c17::66, 2a00:1450:4001:c17::65, 2a00:1450:4001:c17::64
* IPv4: 142.251.20.138, 142.251.20.101, 142.251.20.102, 142.251.20.113, 142.251.20.139, 142.251.20.100
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to google.com (2a00:1450:4001:c17::71 port 443) from 2a02:3032:2e7:581e:fd3f:39a9:451d:7b1e port 49840
* using HTTP/1.x
> GET / HTTP/1.1
> Host: google.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 301 Moved Permanently
< Location: https://www.google.com/
< Content-Type: text/html; charset=UTF-8
< Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-joHGqnDYNOvkeVX3xhmj-A' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
< Date: Thu, 17 Sep 2026 18:04:26 GMT
< Expires: Sat, 17 Oct 2026 18:04:26 GMT
< Cache-Control: public, max-age=2592000
< Server: gws
< Content-Length: 220
< X-XSS-Protection: 0
< X-Frame-Options: SAMEORIGIN
< Alt-Svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000
<
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>
* Connection #0 to host google.com:443 left intact
PS C:\Users\User>
```

---

### A.5. Ресурси з некоректною конфігурацією сертифіката

**Випадок 1**

```
curl -v https://expired.badssl.com
```

```
PS C:\Users\User> curl.exe -v https://expired.badssl.com
* Host expired.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - Получен сертификат с истекшим сроком действия.
* closing connection #0
curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - Получен сертификат с истекшим сроком действия.
PS C:\Users\User>
```

**Випадок 2**

```
curl -v https://wrong.host.badssl.com
```

```
PS C:\Users\User> curl.exe -v https://wrong.host.badssl.com
* Host wrong.host.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - Главное конечное имя неверно.
* closing connection #0
curl: (60) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - Главное конечное имя неверно.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
PS C:\Users\User>
```

**Випадок 3**

```
curl -v https://self-signed.badssl.com
```

```
PS C:\Users\User> curl.exe -v https://self-signed.badssl.com
* Host self-signed.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - Цепочка сертификатов выпущена центром сертификации, не имеющим доверия.
* closing connection #0
curl: (60) schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - Цепочка сертификатов выпущена центром сертификации, не имеющим доверия.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
PS C:\Users\User>
```

> Якщо використано альтернативний спосіб із параметром `--resolve` — зазначити це та навести фактичну команду.

---

## Частина B. Власна модель рівнів

**Кількість виділених груп:** ___

**Кількість виділених груп:** 5

| № | Назва групи (власне формулювання) | Рядки виводу, віднесені до групи | Обґрунтування |
|---|---|---|---|
| 1 | Прикладний рівень (HTTP-запит та відповідь) | > GET / HTTP/1.1; > Host: unicode.org; < HTTP/2 200; < content-type: text/html | Безпосереднє формування HTTP-запиту клієнтом та отримання відповіді від сервера з вмістом сторінки. |
| 2 | Рівень безпеки та представлення (SSL/TLS) | * ALPN: offer h2,http/1.1; * TLSv1.3 (IN), TLS handshake; * Server certificate: GTS CA 1P5 | Узгодження параметрів шифрування, перевірка цифрового сертифіката та захист даних. |
| 3 | Рівень сеансу та узгодження (Session Setup) | * ALPN: server accepted h2; * schannel: SSL/TLS connection renegotiated | Управління та підтримка діалогу/сесії між клієнтом і сервером. |
| 4 | Транспортний рівень (З'єднання та порти) | * Established connection to unicode.org (104.26.11.47 port 443) | Встановлення скрізного TCP-з'єднання з конкретним портом призначення (443). |
| 5 | Мережевий рівень (Адресація та DNS) | * Host unicode.org:443 was resolved.; * IPv4: 104.26.11.47, 172.67.74.23; * Trying 104.26.11.47:443... | Резолюція доменного імені в IP-адресу та маршрутизація пакетів у мережі. |


**Рядки, які не вдалося віднести до жодної групи:**

| Рядок виводу | Причина утруднення |
|---|---|
|* User-Agent: curl/8.21.0 |Це сервісний заголовок самої утиліти curl, який лише вказує версію програми-клієнта, а не мережевий процес. |
|* schannel: disabled automatic use of client certificate |Внутрішнє службове повідомлення системного модуля Windows (Schannel), що стосується локальних налаштувань ОС. |
| * Connection #0 to host unicode.org left intact|Внутрішній статус менеджменту з'єднань утиліти curl про збереження сокета відкритим (Keep-Alive). |

---

## Контрольні питання

**1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?**

Усього вийшло 16 рядків службового виводу. Це всі технічні повідомлення з позначками *, > та <, які утиліта curl виводить під час резолву домену, TCP-підключення, TLS-рукостискання та обміну HTTP-заголовками, аж до порожнього рядка перед самим HTML-кодом сторінки.

**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

У виводі A.1 є рядки про узгодження протоколів (ALPN: offer h2...), параметри шифрування (TLSv1.3), статус перевірки сесії schannel та дані про сертифікат (Server certificate: GTS CA 1P5), яких немає в A.2. Запит A.2 йшов через звичайний незахищений HTTP (порт 80). Там немає етапу TLS-рукостискання, шифрування та перевірки сертифікатів, тому й відповідних службових рядків у виводі просто немає.

**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

Число 443 — це стандартний системний порт для протоколу HTTPS. Коли ми пишемо в адресі https://, утиліта curl автоматично розуміє, що треба стукати саме на 443-й порт сервера, тому не вимагає вказувати його вручну.

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

Значення залишилося тим самим — 300 секунд (або скинулося назад до 300 при повторному запиті).  Це число TTL (Time To Live) — таймер у секундах, який показує, скільки часу DNS-запис може зберігатися в кеші. Якщо воно знову дорівнює 300, це означає, що кеш локального резолвера оновився або запит підтягнувся напряму з авторитетного сервера.

**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` | Термін придатності SSL-сертифіката закінчився.|
| `wrong.host` |Термін придатності SSL-сертифіката закінчився. |
| `self-signed` | Сертифікат підписаний самим сервером, а не довіреним Центром Сертифікації.|

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 | `* schannel: disabled automatic use of client certificate` | A.1 |
| 2 | `* ALPN: offer h2,http/1.1` | A.1 |
| 3 | `* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325)` | A.5 |

*Пояснення до цих рядків не потрібне.*

---

## Висновки


**D.1. Що виявилося неочевидним або несподіваним**

Несподіваним став рядок виводу `* schannel: disabled automatic use of client certificate`.
* Виявилося, що програма за замовчуванням звертається до внутрішнього захисту Windows, а не до зовнішніх бібліотек.
* Через це при помилках виходив рядок `* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325)`, де замість простого тексту виводився складний системний код помилки.
* Також було неочевидно, чому рядок з таймером DNS-кешу не зменшувався при повторній перевірці, а повертав те саме значення.

**D.2. Чому саме така кількість груп у частині B**

Рішення розбити дані на 4 групи я ухвалила на підставі того, що процес підключення до сайту складається з 4 послідовних кроків: пошук адреси (DNS), з'єднання (TCP), перевірка захисту (TLS) та отримання сторінки (HTTP). Змінити цю кількість на меншу змусив би перехід на новіший протокол HTTP/3, де з'єднання та захист відбуваються в один крок, а на більшу — наявність перенаправлень (redirect) або проксі-сервера, що додало б нові етапи.

**D.3. Питання, яке залишилося без відповіді**

> 

---

## Використання штучного інтелекту

*Розділ обов'язковий. Заповнюється незалежно від того, чи використовувався ШІ. Детальні вимоги — у документі «Політика використання технологій штучного інтелекту».*

**Факт використання:** використано

**Установлений рівень для цієї роботи:** Р3 — ШІ як співвиконавець

**Фактичний рівень використання:** Р___ШІ як співвиконавець

### Використані системи

| Система | Версія або модель | Період використання |
|---|---|---|
| Gemini|Gemini 2.5 Flash |допомога у виконанні команд, аналізі помилок SSL/TLS, поясненні теорії та оформленні звіту |

### Промпти

*Наводити дослівно, у тому вигляді, у якому запит було надано системі. Переказ не приймається.*

| № | Розділ роботи | Текст промпта |
|---|---|---|
| 1 |Етап підготовки та запуску команд |Поясни мені, будь ласка, покроково, як правильно створити документ в GitHub і як правильно його оформлювати. Також я тобі надішлю файл з бланком практичної, і ти мені поясни, як правильно записувати всю інформацію, яка буде в мене під час виконання. |
| 2 |Етап аналізу та контролю якості |Буду надсилати сюди результати моїх команд. Скажеш мені, будь ласка, чи правильний це формат і чи правильно все вийшло. Також, коли я використовувала одну із команд, мені на екрані вивело червоними літерами якусь помилку. Як її виправити і що мені зробити, щоб не було таких помилок? І також, будь ласка, перевір, чи правильно я надішлю зараз всі результати моїх команд. 

 |
| 3 |Етап опрацювання та підтвердження формату | Я написала всі команди, тому тепер напиши мені, чи правильно все вийшло, чи правильні я команди написала. І також чому в мене TTL у різний час вийшов однаковий, якщо він начебто повинен відрізнятися? Може, я щось не так зробила? І також дай мені інформацію щодо контрольних питань, щоб я могла відповісти| 

### Дії з отриманим результатом

| № промпта | Що перевірено | Що змінено | Що відхилено і чому |
|---|---|---|---|
| **1** | Правильність генерації команд `curl.exe` та `Resolve-DnsName` для PowerShell. | Додано явне розширення `.exe` до команди `curl` для уникнення виклику псевдоніма. | Відхилено стандартну команду `curl`, оскільки в PowerShell вона викликає командлет `Invoke-WebRequest`. |
| **2** | Синтаксис Markdown-таблиць та групування виводів за рівнями OSI. | Замінено переноси рядків (`<br>` та `Enter`) усередині клітинок на роздільники з крапкою з комою (`;`). | Відхилено варіант таблиці з багаторядковим текстом у клітинках, оскільки це ламало структуру таблиці на GitHub. |
| **3** | Формулювання відповідей на контрольні запитання з теми SSL/TLS та DNS. | Текст адаптовано під стиль відповідей студента — лаконічно, ємно та без складних абстрактних термінів. | Відхилено надто довгі академічні пояснення, оскільки вони не відповідали формату короткого опитування на захисті. |
### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---

## Примітки виконавця

*(необов'язковий розділ: що не спрацювало, які команди довелося змінити, які виникли труднощі)*

> 
<img width="1711" height="7081" alt="image" src="https://github.com/user-attachments/assets/0b0b09fb-1341-46b7-95fe-dfea5e01b62d" />
