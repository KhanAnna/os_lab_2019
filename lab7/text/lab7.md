# Лабораторная работа №7

## Задание 1

### Необходимые знания

1. Компиляция программ на языке С.
2. Аргументы командной строки.
3. Протокол TCP.
4. Протокол UDP.

В этой лабораторной работе вам предстоит потрогать два клиент-серверных приложения. Первое использует проткол TCP, второй UDP. Вам необходимо:

* Скомпилировать все четыре программы.
* Вынести все константы (объявленные через `#define`) в аргументы командной строки.
* Скомпилировать оба приложения через makefile.

## Задание 2
![image.png](https://github.com/KhanAnna/os_lab_2019/blob/master/lab7/text/image%20(3).png?raw=true)

Ответить на следующие вопросы:

1. Что делают оба приложения?

Оба приложения реализуют эхо-сообщения. В клиент-программе пользователь вводит сообщения, сервер принимает их и выводит.

2. Что произойдет, если tcpclient отправит сообщение незапущенному серверу?
3. Что произойдет, если udpclient отправит сообщение незапущенному серверу? 
4. Что произойдет, если tcpclient отвалится во время работы с сервером?

Сервер перезапускается

5. Что произойдет, если udpclient отвалится во время работы с сервером?

Сервер продолжает работу без каких-либо сообщений

6. Что произойдет, если udpclient отправит сообщение на несуществующий / выключенный сервер?
7. Что произойдет, если tcpclient отправит сообщение на несуществующий / выключенный сервер?

Если клиент не получает ответа в течение определенного времени, он повторно отправляет предыдущее сообщение на сервер. Клиент будет продолжать повторно отправлять сообщение, пока не получит ответ от сервера ИЛИ до указанного времени истечения срока действия (в зависимости от реализации). Если это время истекло, предполагаем, что сервер не работает.

Можно отправлять запросы с более коротким интервалом, чем сообщения. Скажем, что всякий раз, когда получаем сообщение от сервера, мы запускаем часы, которые отсчитывают 1 минуту, а затем отправляем команду "ping" (если не получили новое сообщение между ними). Если не получаем ответа на свой "ping" в течение 30 секунд, делаем вывод, что соединение разорвано.

9. В чем отличия UDP и TCP протоколов?

**UDP: отправить сообщение и не оглядываться назад, если оно достигло адресата, протокол без установления соединения
 TCP: отправка сообщения и гарантия достижения адресата, протокол, ориентированный на соединение**

TCP (протокол управления передачей) является наиболее часто используемым протоколом в Интернете. Причина этого в том, что TCP предлагает исправление ошибок. Когда используется протокол TCP, существует "гарантированная доставка". Это в значительной степени частично связано с методом, называемым "управление потоком". Управление потоком определяет, когда данные необходимо повторно отправить, и останавливает поток данных до тех пор, пока предыдущие пакеты не будут успешно переданы. Это работает, потому что при отправке пакета данных может возникнуть коллизия. Когда это происходит, клиент повторно запрашивает пакет с сервера, пока весь пакет не будет завершен и не будет идентичен своему оригиналу.

UDP (протокол пользовательских дейтаграмм) является более распространенным протоколом, используемым в Интернете. Однако UDP никогда не используется для отправки важных данных, таких как веб-страницы, информация базы данных и т. Д.; UDP обычно используется для потоковой передачи аудио и видео. Потоковые носители, такие как аудиофайлы Windows Media (.WMA), Real Player (.RM) и другие, используют UDP, потому что он обеспечивает скорость! Причина, по которой UDP быстрее, чем TCP, заключается в том, что нет формы управления потоком или исправления ошибок. На данные, отправляемые через Интернет, влияют коллизии, и будут присутствовать ошибки. Скорость - основная причина, по которой потоковое мультимедиа не отличается высоким качеством.

## Перед тем, как сдавать

Залейте ваш код в ваш репозиторий на GitHub. Убедитесь, что вы не добавляете в репозиторий бинарные файлы (программы, утилиты, библиотеки и т.д.).
