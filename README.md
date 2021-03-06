Федеральное государственное бюджетное образовательное учреждение высшего образования

# «ФИНАНСОВЫЙ УНИВЕРСИТЕТ ПРИ ПРАВИТЕЛЬСТВЕРОССИЙСКОЙ ФЕДЕРАЦИИ» 

## Департамент анализа данных и машинного обучения

## Факультет информационных технологий и анализа больших данных

Выпускная квалификационная работа

на тему:

# Разработка ПО для расширения полномочий доверенных веб-страниц

Выполнил студент группы ПИ17-1

## Носко Максим Михайлович

---

Компоненты Системы Расширения Полномочий:
* Портал СРП - веб-приложения для работы со списком приложений (папка Portal SRP)
* Клиент СРП - приложение для пользователей системы (папка Client SRP)
* Сервер СРП - приложение для проверки команды (папка Server SRP)
* Клиентская библиотека СРП - JS-файл, с помощью которого приложение может связаться с Клиентом СРП (папка ClientLib SRP)
* Серверная библиотека СРП - Python-файл, с помощью которого сервер приложения может подписать команду клиента приложения (папка ServerLib SRP)
* Блокнот - пример приложения, осуществляющего чтение и запись текстовых файлов (папка Notepad)
* Проводник - пример приложения, осуществляющего отображение списка файлов, переименование, удаление, а также создание папок (папка Explorer)

Также, в папке Скриншоты приведены скриншоты всех компонентов, имеющих графический интерфейс, в работе

---

# Портал СРП

## Пользователю

Пользователь на Портале может просматривать список приложений и информацию о каждом приложении

![Список приложений](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты%20с%20подписями/Портал%20СРП/Портал%20список%20приложений.png?raw=true)

![Страница приложения](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20карточка%20условоного%20приложения%201.png?raw=true)

![Страница приложения](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20карточка%20условоного%20приложения%202.png?raw=true)

## Разработчику

Для добавления приложения (в статусе заявки) разработчику необходимо заполнить форму добавления и отметить все требующиеся приложению разрешения

![Форма](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20анкета%201.png?raw=true)

![Форма](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20анкета%202.png?raw=true)

Непосредственно после добавления, разработчику будет показан на экране секретный ключ приложения. Повторно он не показывается (но можно запросить новый):

![Секретный ключ](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20секретный%20ключ.png?raw=true)

Далее, разработчику необходимо отслеживать статус приложения: администрация сделает приложение доверенным или отклонённым. Как только приложение будет доверенным, то есть ему будет разрешено выполнение хотя бы одной команды, приложение сможет использовать разрешённые команды.

Также, разработчику, по текущему паролю, доступны смена пароля и запрос нового секретного ключа, а также удаление приложения:

![Редактирование](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20управление.png)


## Администратору

Запуск портала:

Для запуска необходимо запустить код в файле "Portal SRP.ipynb", который расположен в папке:

https://github.com/MaximNosko/VKR_SRP/tree/main/Portal%20SRP

Пароль администратора будет задан из файла ".ADMIN_PASSWORD", который расположен в той же папке. При отсутствии файла, он будет сгенерирован с паролем "ADMIN_PASSWORD"

При запуске необходимо проверить значения переменных PORTAL_PORT - порт для сайта портала, PORTAL_HOST - хост сайта портала, DATABASE_PORT - порт запущенной базы данных MongoDB.

Для администрирования списка приложений, необходимо открыть на сайте портала страницу "/admin":

![Главная для администратора](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20главная%20для%20администоров.png)

Далее, необходимо выбрать приложение, которым администратор хочет управлять, и внести нужные изменения, подтвердив свои полномочия паролем администратора:

![Администрирование](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20редактирование%201.png)

![Администрирование](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20редактирование%202.png)

![Администрирование](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Портал%20СРП/Портал%20редактирование%20разрешения.png)

# Сервер СРП

Запуск сервера:

Для запуска необходимо запустить код в файле "Server SRP.ipynb", который расположен в папке:

https://github.com/MaximNosko/VKR_SRP/tree/main/Server%20SRP

При запуске необходимо проверить значения переменных SERVER_PORT - порт для веб-сервера, SERVER_HOST - хост сайта сервера, DATABASE_PORT - порт запущенной базы данных MongoDB.

Сетевой адрес Сервера СРП должен быть известен Клиенту СРП

# Клиент СРП

Запуск клиента:

Для запуска необходимо запустить код в файле "Client SRP.ipynb", который расположен в папке:

https://github.com/MaximNosko/VKR_SRP/tree/main/Client%20SRP

При запуске необходимо проверить значения переменных CLIENT_PORT - порт для веб-сервера, CLIENT_HOST - хост сайта клиента, SERVER_URL - сетевой адрес запущенного Сервера СРП.

# Клиентская библиотека СРП

Для использования в приложении, необходимо подключить следующий файл как JS-скрипт:

https://github.com/MaximNosko/VKR_SRP/blob/main/ClientLib%20SRP/appSRP.js

В рамках Библиотеки, реализована функция, с которой и должен работать код приложения:

runSRPCommand(appID,type,args,signURL,onWaiting,onDone,onError,onReturn)
* appID - идентификатор приложения
* type - тип команды
* args - объект, содержащий в себе аргументы команды
* signURL - адрес, по которому можно осуществить подпись хеша команды
* onWaiting - функция, которая будет вызвана во время ожидания завершения команды, аргументы не передаются
* onDone - функция, которая будет вызвана при успешном завершении команды, аргументы не передаются
* onError - функция, которая будет вызвана при неуспешном завершении команды, аргументы не передаются
* onReturn - функция, которая будет вызвана при успешном завершении, в качестве аргументов передаются объект результата выполнения команды и объект команды

# Серверная библиотека СРП 

Для использования в приложении, необходимо подключить следующий файл как Python-библиотеку:

https://github.com/MaximNosko/VKR_SRP/blob/main/ServerLib%20SRP/appServerSRP.py

В рамках Библиотеки, реализована функция, с которой и должен работать код приложения:

signSRP(secret_key,commandHash)
* secret_key - секретный ключ приложения
* commandHash - хеш команды

Функция возвращает строку - подпись команды

# Команды

Объект команды, который формируется и возвращается аргументом onReturn:

{"type":<тип команды>,"args":<аргументы>,"appID":<идентификатор приложения>,"serverSign":<подпись сервера приложения>}

## Чтение

* type - "read"
* args - {"path":<путь>}

Возвращает объект:

{"auth":<результат проверки разрешения>, "result":{"success":<успех выполнения>,"path":<путь выполнения команды>,"bytes":<список байтов>}}

## Запись

* type - "write"
* args - {"path":<путь>,"bytes":<массив байтов>}

Возвращает объект:

{"auth":<результат проверки разрешения>, "result":{"success":<успех выполнения>,"path":<путь выполнения команды>}}

## Список файлов и папок

* type - "list"
* args - {"path":<путь папки>}

Пустой путь позволяет просмотреть список дисков

Переменная окружения позволяет получить путь и выполнить команду по данному пути

Возвращает объект:

{"auth":<результат проверки разрешения>, "result":{"success":<успех выполнения>,"path":<путь выполнения команды>,"files":<список файлов>,"files":<список папок>}}

Файл:

{"title":<имя>,"modify":<время изменения>,"create":<время создания>,"path":<полный путь>,"size":<размер в байтах>}

Папка:

{"title":<имя>,"modify":<время изменения>,"create":<время создания>,"path":<полный путь>}

## Удаление

* type - "delete"
* args - {"path":<путь файла или папки>}

Возвращает объект:

{"auth":<результат проверки разрешения>, "result":{"success":<успех выполнения>,"path":<путь выполнения команды>}}

## Создание папки

* type - "mkdir"
* args - {"path":<путь, включающий в себя создаваемую папку>}

{"auth":<результат проверки разрешения>, "result":{"success":<успех выполнения>,"path":<путь выполнения команды>}}

## Переименование

* type - "mkdir"
* args - {"path":<путь файла или папки>,"newName":<новое наименование объекта>}

Возвращает объект:

{"auth":<результат проверки разрешения>, "result":{"success":<успех выполнения>,"path":<путь выполнения команды>}}

# Блокнот

Пример приложения, использующего СРП

![Блокнот](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Блокнот/Блокнот%20успешно.png)

# Проводник

Пример приложения, использующего СРП

![Проводник](https://github.com/MaximNosko/VKR_SRP/blob/main/Скриншоты/Проводник/Проводник%20успешно.png)
