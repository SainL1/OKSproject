# +WebToDo<br/>
Cостав команды:<br/>
+ Зимцов Максим - 3 курс, ИВТ-22-22<br/>
+ Петров Иван - 3 курс, ИВТ-22-22<br/>
+ Фалинская Анастасия - 3 курс, ИВТ-22-22<br/>

### Постановка задачи<br/>
Необходимо создать безопасную среду для пользования маркетплейсом. Обеспечить защиту личных данных пользователей. Обеспечить безопасность транзакций. 
Предотвратить мошенничество и кибератаки. Создать надежное взаимодействие между покупателями и продавцами.

### Идея приложения:<br/>
Приложение предназначено для эффективного управления личными и командными задачами. Оно должно позволять пользователям 
создавать задачи, назначать исполнителей, устанавливать сроки выполнения, отслеживать прогресс и отправлять 
уведомления о приближающихся дедлайнах. Приложение будет доступно через веб-интерфейс и мобильное приложение.<br/><br/>

### Модель угроз<br/>
![https://github-production-user-asset-6210df.s3.amazonaws.com/92573287/374643283-02a122c2-70e7-416b-bd0f-ceb3b639c976.jpeg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241015%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241015T141921Z&X-Amz-Expires=300&X-Amz-Signature=346b634c0b4b8ef90a40ae8142d9a7ab70f27325493f32c95bf7edbc55b4d6aa&X-Amz-SignedHeaders=host]

### Модель нарушителя<br/>
![https://sun9-1.userapi.com/s/v1/ig2/hdnHqjjqV0M-1RS7TF2dKL3ZlhsFpwRcQCrgyRxj6hTysUQYpIq56jAURjTGCpVKigp-yD3hGLjCy2MptK10-Tfn.jpg?quality=96&as=32x19,48x28,72x42,108x63,160x94,240x140,360x210,480x281,540x316,640x374,720x421,1080x631,1235x722&from=bu&u=tuI5YvE2QnQUkCFWY_1bOjdA0Vl7h7DuibyOecpuSPU&cs=1235x722]

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
