#WebToDo
# Идея приложения:<br/>
Приложение предназначено для эффективного управления личными и командными задачами. Оно должно позволять пользователям 
создавать задачи, назначать исполнителей, устанавливать сроки выполнения, отслеживать прогресс и отправлять 
уведомления о приближающихся дедлайнах. Приложение будет доступно через веб-интерфейс и мобильное приложение.<br/><br/>

# Основные функции:<br/>
Создание задач: Пользователь может создавать задачи с названием, описанием, приоритетом и сроком выполнения.<br/>
Назначение задач: Возможность распределения задач между участниками команды.<br/>
Уведомления: Напоминания о дедлайнах и изменениях статуса задачи.<br/>
Отчеты: Ведение отчета о выполненных задачах и анализ производительности.<br/>
Комментарирование: Возможность добавления комментариев к задачам для обсуждения деталей.<br/>
Уровни доступа: Администраторы, пользователи с ограниченными правами, гости.<br/>
Интеграции: Возможность синхронизации с календарями и другими инструментами управления проектами.<br/>


![6cf288fc7caa9034a483ada299083179](https://github.com/user-attachments/assets/5057c90d-a5e6-4ac0-9bcc-cd07d45a4150)
Блок-схема архитектуры приложения.<br/><br/>

# АРХИТЕКТУРА ПРИЛОЖЕНИЯ<br/>

### Пользовательский интерфейс (UI):<br/>
+ Веб-приложение (React)<br/>
+ Мобильное приложение (React Native)<br/>
### Серверная часть (Backend):<br/>
+ API для взаимодействия с клиентом (Node.js + Express)<br/>
+ База данных (PostgreSQL)<br/>
+ Модуль уведомлений (сервисы пуш-уведомлений, email)<br/>
### Аутентификация и безопасность:<br/>
+ JWT для авторизации<br/>
+ OAuth для интеграции с другими сервисами (Google, Facebook)<br/>
### Хранилище файлов:<br/>
+ S3-совместимое хранилище для прикрепленных файлов.<br/><br/>


# Возможные уязвимости и способы их решения:<br/>

### Уязвимость: SQL-инъекции<br/>
Описание: Хакеры могут манипулировать запросами к базе данных для получения несанкционированного доступа.<br/>
Решение: Использование ORM (например, Sequelize для Node.js) и подготовленных запросов для защиты базы данных от SQL-инъекций.<br/>

### Уязвимость: Межсайтовый скриптинг (XSS)<br/>
Описание: Злоумышленник может внедрить вредоносный код на страницу, который выполнится в браузере пользователя.<br/>
Решение: Внедрение строгой фильтрации и экранирования пользовательских данных перед выводом в HTML, использование Content Security Policy (CSP).<br/>

### Уязвимость: Утечка данных через неправильную конфигурацию API<br/>
Описание: Несанкционированные пользователи могут получить доступ к данным через API.<br/>
Решение: Реализация строгих правил авторизации и аутентификации с использованием JWT и контроля уровней доступа для разных пользователей.<br/>

### Уязвимость: Неправильное управление сессиями<br/>
Описание: Злоумышленники могут похитить сессии пользователей для получения доступа к их данным.<br/>
Решение: Использование защищённых сессий с ограничением времени действия, а также защита от CSRF-атак. <br/>

### Уязвимость: Утечка данных при хранении файлов<br/>
Описание: Вредоносные пользователи могут получить доступ к конфиденциальным файлам.<br/>
Решение: Шифрование файлов и ограничение доступа к хранилищу данных с использованием токенов доступа.<br/>
