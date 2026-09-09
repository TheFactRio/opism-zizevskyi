# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

| | |
|---|---|
| **Прізвище, ім’я** | Зізевський Михайло |
| **Група** | КБЗІ-2.02 |
| **Номер варіанта** | 9 |
| **Домен варіанта** | `itu.int` |
| **Середовище виконання** | Windows |
| **Версія curl** | curl 8.21.0 (Windows) libcurl/8.21.0 Schannel zlib/1.3.2 WinIDN WinLDAP |
| **Дата виконання** | 09.09.2026 |

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:**

```
curl -v https://itu.int
```

**Вивід:**

```
* Host itu.int:443 was resolved.
* IPv6: (none)
* IPv4: 156.106.253.250
*   Trying 156.106.253.250:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server did not agree on a protocol. Uses default.
* Established connection to itu.int (156.106.253.250 port 443) from 192.168.0.197 port 60189
* using HTTP/1.x
> GET / HTTP/1.1
> Host: itu.int
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< Location: https://www.itu.int/
< Connection: close
< Content-Length: 0
<
* shutting down connection #0
```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```
curl -v http://neverssl.com
```

**Вивід:**

```
* Host neverssl.com:80 was resolved.
* IPv6: (none)
* IPv4: 34.223.124.45
*   Trying 34.223.124.45:80...
* connect to 34.223.124.45 port 80 from 0.0.0.0 port 64543 failed: Timed out
* Failed to connect to neverssl.com:80 after 21081 ms: Could not connect to server
* closing connection #0
curl: (28) Failed to connect to neverssl.com:80 after 21081 ms: Could not connect to server
```

---

### A.3. Запит до служби доменних імен

*Windows: `Resolve-DnsName ВАШ_ДОМЕН`*

**Команда (перше виконання):**

```
Resolve-DnsName itu.int
```

**Вивід:**

```

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
itu.int                                        AAAA   1652  Answer     2a00:7580:60:a252::3250
itu.int                                        A      1652  Answer     156.106.253.250

Name      : itu.int
QueryType : NS
TTL       : 85352
Section   : Authority
NameHost  : ns7.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85352
Section   : Authority
NameHost  : ns.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85352
Section   : Authority
NameHost  : ns8.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85352
Section   : Authority
NameHost  : ns6.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85352
Section   : Authority
NameHost  : ns3.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85352
Section   : Authority
NameHost  : ns2.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85352
Section   : Authority
NameHost  : ns5.itu.ch

ns.itu.ch                                      A      1652  Additional 156.106.192.121
ns2.itu.ch                                     A      1652  Additional 4.156.158.244
ns3.itu.ch                                     A      1652  Additional 20.101.208.60
ns5.itu.ch                                     A      1652  Additional 205.251.192.35
ns6.itu.ch                                     A      1652  Additional 205.251.195.44
ns7.itu.ch                                     A      2552  Additional 205.251.196.40
ns8.itu.ch                                     A      2552  Additional 205.251.199.74
ns.itu.ch                                      AAAA   1652  Additional 2a00:7580:60:2141::10
ns2.itu.ch                                     AAAA   1652  Additional 2603:1030:20e:c::175
ns3.itu.ch                                     AAAA   1652  Additional 2603:1020:203:3::20c
ns5.itu.ch                                     AAAA   1652  Additional 2600:9000:5300:2300::1
ns6.itu.ch                                     AAAA   1652  Additional 2600:9000:5303:2c00::1
ns7.itu.ch                                     AAAA   2552  Additional 2600:9000:5304:2800::1
ns8.itu.ch                                     AAAA   2552  Additional 2600:9000:5307:4a00::1
```

**Команда (повторне виконання через 5–7 хвилин):**

```
Resolve-DnsName itu.int
```

**Вивід:**

```

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
itu.int                                        AAAA   1324  Answer     2a00:7580:60:a252::3250
itu.int                                        A      1324  Answer     156.106.253.250

Name      : itu.int
QueryType : NS
TTL       : 85024
Section   : Authority
NameHost  : ns.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85024
Section   : Authority
NameHost  : ns2.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85024
Section   : Authority
NameHost  : ns7.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85024
Section   : Authority
NameHost  : ns8.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85024
Section   : Authority
NameHost  : ns3.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85024
Section   : Authority
NameHost  : ns6.itu.ch


Name      : itu.int
QueryType : NS
TTL       : 85024
Section   : Authority
NameHost  : ns5.itu.ch

ns.itu.ch                                      A      1324  Additional 156.106.192.121
ns2.itu.ch                                     A      1324  Additional 4.156.158.244
ns3.itu.ch                                     A      1324  Additional 20.101.208.60
ns5.itu.ch                                     A      1324  Additional 205.251.192.35
ns6.itu.ch                                     A      1324  Additional 205.251.195.44
ns7.itu.ch                                     A      2224  Additional 205.251.196.40
ns8.itu.ch                                     A      2224  Additional 205.251.199.74
ns.itu.ch                                      AAAA   1324  Additional 2a00:7580:60:2141::10
ns2.itu.ch                                     AAAA   1324  Additional 2603:1030:20e:c::175
ns3.itu.ch                                     AAAA   1324  Additional 2603:1020:203:3::20c
ns5.itu.ch                                     AAAA   1324  Additional 2600:9000:5300:2300::1
ns6.itu.ch                                     AAAA   1324  Additional 2600:9000:5303:2c00::1
ns7.itu.ch                                     AAAA   2224  Additional 2600:9000:5304:2800::1
ns8.itu.ch                                     AAAA   2224  Additional 2600:9000:5307:4a00::1
```

**Зафіксовані значення:**

| Параметр | Перше виконання | Повторне виконання |
|---|---|---|
| Час виконання (год:хв) | 10:55 | 11:00 |
| IP-адреса | `156.106.253.250`, `2a00:7580:60:a252::3250` | `156.106.253.250`, `2a00:7580:60:a252::3250` |
| Значення TTL | 1652 | 1324 |

---

### A.4. Контрольний ресурс

**Команда:**

```
curl -v https://google.com
```

**Вивід:**

```
* Host google.com:443 was resolved.
* IPv6: (none)
* IPv4: 142.250.109.113, 142.250.109.101, 142.250.109.139, 142.250.109.102, 142.250.109.138, 142.250.109.100
*   Trying 142.250.109.113:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to google.com (142.250.109.113 port 443) from 192.168.0.197 port 51497
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
< Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-_UCSfIzY7zzdt8Is_6aWeQ' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
< Date: Wed, 09 Sep 2026 06:24:56 GMT
< Expires: Fri, 09 Oct 2026 06:24:56 GMT
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
```

---

### A.5. Ресурси з некоректною конфігурацією сертифіката

**Випадок 1**

```
curl -v https://expired.badssl.com
```

```
* Host expired.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.
* closing connection #0
curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.
```

**Випадок 2**

```
curl -v https://wrong.host.badssl.com
```

```
* Host wrong.host.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.
* closing connection #0
curl: (60) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

**Випадок 3**

```
curl -v https://self-signed.badssl.com
```

```
* Host self-signed.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.
* closing connection #0
curl: (60) schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

---

## Частина B. Власна модель рівнів

**Кількість виділених груп:** 5

| № | Назва групи (власне формулювання) | Рядки виводу, віднесені до групи | Обґрунтування |
|---|---|---|---|
| 1 | Створення вебзапиту та отримання відповіді | `> GET / HTTP/1.1`<br>`> Host: itu.int`<br>`> User-Agent: curl/8.21.0`<br>`> Accept: */*`<br>`< HTTP/1.1 301 Moved Permanently`<br>`< Location: https://www.itu.int/`<br>`< Connection: close`<br>`< Content-Length: 0`<br>`< Content-Type: text/html; charset=UTF-8`<br>`< Server: gws`<br>`<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">`<br>`<H1>301 Moved</H1>`<br>`The document has moved` | Ці рядки містять вебзапити клієнта та відповідь вебсервера. |
| 2 | Узгодження протоколу обміну | `* ALPN: curl offers http/1.1`<br>`* ALPN: server did not agree on a protocol. Uses default.`<br>`* ALPN: server accepted http/1.1`<br>`* using HTTP/1.x` | Рядки описують узгодження протоколу обміну |
| 3 | Захист з’єднання та сертифікати | `* schannel: disabled automatic use of client certificate`<br>`* schannel: remote party requests renegotiation`<br>`* schannel: renegotiating SSL/TLS connection`<br>`* schannel: SSL/TLS connection renegotiated`<br>`* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.`<br>`curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.`<br>`* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.`<br>`curl: (60) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.`<br>`* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.`<br>`curl: (60) schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.` | Рядки описують роботу захищеного TLS-з’єднання та перевірку сертифіката. |
| 4 | Установлення та завершення з’єднання | `* Trying 156.106.253.250:443...`<br>`* Established connection to itu.int (156.106.253.250 port 443) from 192.168.0.197 port 60189`<br>`* Request completely sent off`<br>`* shutting down connection #0`<br>`* Trying 34.223.124.45:80...`<br>`* connect to 34.223.124.45 port 80 from 0.0.0.0 port 64543 failed: Timed out`<br>`* Failed to connect to neverssl.com:80 after 21081 ms: Could not connect to server`<br>`* closing connection #0`<br>`curl: (28) Failed to connect to neverssl.com:80 after 21081 ms: Could not connect to server`<br>`* Connection #0 to host google.com:443 left intact` | Ці рядки показують спробу встановлення з’єднання, надсилання запиту та завершення з’єднання. |
| 5 | Визначення мережевої адреси | `* Host itu.int:443 was resolved.`<br>`* IPv6: (none)`<br>`* IPv4: 156.106.253.250`<br>`itu.int AAAA 1652 Answer 2a00:7580:60:a252::3250`<br>`itu.int A 1652 Answer 156.106.253.250`<br>`QueryType : NS`<br>`TTL : 85352`<br>`Section : Authority`<br>`NameHost : ns7.itu.ch`<br>`ns.itu.ch A 1652 Additional 156.106.192.121`<br>`ns.itu.ch AAAA 1652 Additional 2a00:7580:60:2141::10` | Рядки показують перетворення доменного імені на IPv4- та IPv6-адреси. |

*Групи впорядковано від найближчої до користувача (№ 1) до найближчої до апаратного забезпечення. Зайві рядки вилучити, за потреби — додати.*

**Рядки, які не вдалося віднести до жодної групи:**

| Рядок виводу | Причина утруднення |
|---|---|
| `More details here: https://curl.se/docs/sslcerts.html` | Це локальне посилання на документацію curl. |
| `To learn more about this situation and how to fix it, please visit the webpage mentioned above.` | Це повідомлення утіліти curl після помилки. |

---

## Контрольні питання

**1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?**

> Дані сторінки не були отримані через відповідь `HTTP/1.1 301 Moved Permanently`. До першого рядка HTTP-відповіді `< HTTP/1.1 301 Moved Permanently` було виведено 15 діагностичних рядків і рядків запиту.

**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

> У A.1 є рядки Schannel і ALPN: `* schannel: disabled automatic use of client certificate`, `* ALPN: curl offers http/1.1`,  `* ALPN: server did not agree on a protocol. Uses default.`. Вони відсутні в A.2, тому що A.1 використовує захищений протокол HTTPS. Також в A.2 відсутні рядки HTTP-запиту та відповіді, оскільки з’єднання із сервером було невдалим.

**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

> Це tcp порт, який відповідає за протокол *https*. Спроба звернутися до будь-якої вебсторінки супроводжується встановленням з'єднання з IP-адресою вебсервером і портом `80`(*http*) чи `443`, який сервер тримає відкритим, щоб користувачі мали можливість потрапити до вебсайту.

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

> TTL - це значення DNS-запису, яке означає Time-To-Live. Це залишок часу, протягом якого DNS-запис може зберігатися. Після завершення цього часу резолвер повинен повторно запитати актуальні дані. У завданні (A.3) TTL зменшився з 1652 до 1324 секунд, тобто через 1324 секунд дані оновляться.

**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` | Термін дії сертифіката закінчився |
| `wrong.host` | Сертифікат виданий не для того доменного імені|
| `self-signed` | Сертифікат підписаний самим власником |

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 | `* ALPN: server did not agree on a protocol. Uses default.` | A.1 |
| 2 | `* schannel: remote party requests renegotiation` | A.4 |
| 3 | `< Alt-Svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000` | A.4 |

*Пояснення до цих рядків не потрібне.*
---

## Висновки

*150–300 слів. Спиратися на власні спостереження, а не на матеріал лекції.*

**D.1. Що виявилося неочевидним або несподіваним**

*Назвати конкретно, з посиланням на рядок виводу.*

> Різні результати `curl` і `Resolve-DnsName` трохи дивні. Під час запиту до `itu.int` curl вивів рядок `* IPv6: (none)` і використав IPv4-адресу `156.106.253.250`. Водночас команда `Resolve-DnsName itu.int` знайшла для цього домену запис типу `AAAA` з IPv6-адресою `2a00:7580:60:a252::3250`. Схоже, наявність IPv6-адреси в DNS-відповіді не означає, що конкретна програма використає її для встановлення з’єднання. У моєму випадку curl виконав підключення через IPv4, що підтверджує рядок `* Trying 156.106.253.250:443...`.

**D.2. Чому саме така кількість груп у частині B**

*На якій підставі ухвалено рішення. Що змусило б його змінити.*

> Було виділено п’ять груп. Групи були сформовані через п’ять різних за призначенням процесів: обмін HTTP-даними, узгодження протоколу, захист і перевірка сертифікатів, установлення з’єднання та визначення мережевої адреси. Це дозволило віднести рядки до груп і не змішування їхнє призначення. Якщо б у виводі команд була додаткова інформація, наприклад про маршрутизацію чи передавання кадрів, ймовірно, кількість груп зросла б. 

**D.3. Питання, яке залишилося без відповіді**

> З'єднання з доменом `neverssl.com` через порт 80 завершилося повідомленням `Timed out`, проте домен успішно перетворився на IP-адресу `34.223.124.45`. Це могло бути через обмеження локальної мережі, фільтрацію незахищеного HTTP-трафіку чи тимчасову недоступність сервера.

---

## Використання штучного інтелекту

*Розділ обов'язковий. Заповнюється незалежно від того, чи використовувався ШІ. Детальні вимоги — у документі «Політика використання технологій штучного інтелекту».*

**Факт використання:** використано 

**Установлений рівень для цієї роботи:** Р3 — ШІ як співвиконавець

**Фактичний рівень використання:** Р3 - ШІ як співвиконавець

### Використані системи

| Система | Версія або модель | Період використання |
|---|---|---|
| GPT | 5.6 Sol | 09.09.2026 |

### Промпти

*Наводити дослівно, у тому вигляді, у якому запит було надано системі. Переказ не приймається.*

| № | Розділ роботи | Текст промпта |
|---|---|---|
| 1 | частина B | зроби пояснення части B(завантажив pdf і md практичної) |
| 2 | частина B | перевір віднесені рядки до груп (вставив таблицю "Власна модель рівнів") |
| 3 | Увесь звіт | перевір на помилки і неточністі (завантажив md з відповідями) |

### Дії з отриманим результатом

| № промпта | Що перевірено | Що змінено | Що відхилено і чому |
|---|---|---|---|
| 1 | Перевірено коректність розуміння завдання частини B | - | Стало зрозуміло, що модель OSI для цього завдання не підійде |
| 2 | Перевірено коректність віднесення рядків | - | - |
| 3 | Перевірено звіт на технічні та граматичні помилки | Виправлено граматичні помилки і уточнено деякі формулювання | Частину запропонованих формулювань не використано, оскільки не змінюють сутність |

### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---