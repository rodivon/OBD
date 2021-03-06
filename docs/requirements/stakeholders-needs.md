# Statt_. Запити зацікавлених осіб

## Вступ

У цьому документі зазначені всі основні принципи та мету системи Statt_. 

Розглянули короткий огляд та характеристику ділових процесів даної системи

Створили список вимог стосовно: функціональності, практичністі, надійності, продуктивності та експлуатації придатності системи.

-------------

### Мета 

Метою документу є визначити головні вимоги до функціональності, продуктивності, надійності, зручності, доступності, а також визначити бізнес-правила та технологічні обмеження, що накладаються на предмет розробки.

-------------

### Контекст

Перелік вимог, зазначених у данному документі, є основою технічного завдання для розробки веб-сервісу, який допоможе користувачам виконувати пошук зображення за рейтингом.

-------------

### Посилання
 - ["Основні визначення та скорочення"](../requirements/state-of-the-art.md)
------------

## Короткий зміст

Ми вже розглянули:

- [Вступ](#вступ)
- [Мету](#мета)
- [Контекст](#контекст)
- [Посилання](#посилання)

Далі зазначено такі теми:

- [Характеристика ділових процесів](#характеристика-ділових-процесів)
- [Короткий огляд продукту](#короткий-огляд-продукту)
- [Функціональність](#функціональність)
- [Практичність](#практичність)
- [Надійність](#надійність)
- [Продуктивність](#продуктивність)
- [Експлуатаційна придатність](#експлуатаційна-придатність)

-----------

## Характеристика ділових процесів

***ID:*** AD.0b1

***Назва:*** Додавання об’єкту

***Учасники:*** Модератор, система

***Передумови:*** Користувач авторизований, користувач належить до групи «модератори», чи груп, що наслідують групу «модератори»

***Результат:*** Створення і заповнення строки у БД об’єктів

***Основний сценарій:*** 
1. Модератор відправляє запит на додавання об’єкту
2. Система підготовлює форму з наступними полями:
    1. Назва об’єкту (обов’язкове)
     2. Прапорець «Видимість об’єкту» (by default = true)
     3. Тип об’єкту (обов’язкове)
     4. Теги (обов’язкове)
     5. Координати (обов’язкове)
     6. Фото
     7. Коментар
3. Модератор заповнює форму 
4. Система зберігає данні у БД
5. Система виводить повідомлення про успішне додавання об’єкту
    
***Виключні ситуації:***
- Система тимчасово не доступна
- Незаповнені обов’язкові поля
   
!["Діаграма 1"](../images/dia12.png?raw=true)

-------------
    
***ID:*** ED.Ob1

***Назва:*** Редагування об’єкту

***Учасники:*** Модератор, система

***Передумови:*** Користувач авторизований, користувач належить до групи «модератори», чи груп, що наслідують групу «модератори»

***Результат:*** Заміна даних у БД об’єктів

***Основний сценарій:*** 
1. Модератор відправляє запит на редагування об’єкту
2. Система підготовлює форму з наступними полями:
    1. Назва об’єкту (обов’язкове)
    2. Прапорець «Видимість об’єкту»
    3. Тип об’єкту (обов’язкове)
    4. Теги (обов’язкове)
    5. Координати (обов’язкове)
    6. Фото
    7. Коментар
3. Система заповнює форму з БД
4. Модератор редагує данні у формі
5. Система замінює данні у БД
6. Система виводить повідомлення про успішну заміну даних у БД

***Виключні ситуації:***
- Система тимчасово не доступна
- Незаповнені обов’язкові поля
    
!["Діаграма 2"](../images/dia22.png?raw=true)    

-------------
        
***ID:*** AD.M1

***Назва:*** Призначення модератора

***Учасники:*** Адміністратор, система

***Передумови:*** Користувач авторизований, користувач належить до групи «адміністратори», чи груп, що наслідують групу «адміністратори»

***Результат:*** Перенесення користувача з групи «користувачі» в групу «модератори»

***Основний сценарій:*** 
1. Адміністратор вибирає модератора, клацає на кнопку «призначити модератором»
2. Система переносить користувача з групи «користувачі» до групи «модератори»
3. Система виводить повідомлення про успішне перенесення користувача у групу «модератори»

***Виключні ситуації:*** 
- Система тимчасово не доступна

!["Діаграма 3"](../images/dia3.png?raw=true)
    
-------------

***ID:*** RM.M1

***Назва:*** Видалення модератора

***Учасники:*** Адміністратор, система

***Передумови:*** Користувач авторизований, користувач належить до групи «адміністратори», чи груп, що наслідують групу «адміністратори»

***Результат:*** Перенесення користувача з групи «модератори» в групу «користувачі»

***Основний сценарій:***
1. Адміністратор вибирає модератора, клацає на кнопку «видалити модератора»
2. Система переносить користувача з групи «модератори» до групи «користувачі»
3. Система виводить повідомлення про успішне перенесення модератора у групу «користувачі»

***Виключні ситуації:***
- Система тимчасово не доступна
    
!["Діаграма 4"](../images/dia4.png?raw=true)
    
-------------

    
***ID:*** AD.Qr1

***Назва:*** Створення запиту

***Учасники:*** Користувач, система

***Передумови:*** Користувач авторизований

***Результат:*** Створення результату і його вивід на екран користувача

***Основний сценарій:*** 
1. Користувач відправляє запит
2. Система підготовлює форму з наступними полями:
    1. Головне ключове слово та його варіації (обов’язкове)
    2. Додаткові ключові слова
    3. Період часу (обов’язкове)
    4. Регіон пошуку (обов’язкове)
    5. Ресурси пошуку (обов’язкове)
3. Користувач заповнює форму
4.  Система проводить пошук по базам даних заданих ресурсів
5. Система фільтрує дані за заповненою користувачем формою
6. Система виконує розрахунок статистики
7. Система виводить результат на екран користувача

***Виключні ситуації:***
- Система тимчасово недоступна
- Незаповнені обов’язкові поля

!["Діаграма 5"](../images/dia5.png?raw=true)
    
-------------
    

***ID:*** AD.Rv1

***Назва:*** Додавання відгуку

***Учасники:*** Користувач, система

***Передумови:*** Користувач авторизований

***Результат:*** Створення і заповнення строки у БД відгуків

***Основний сценарій:***
1. Користувач відправляє запит на додавання відгуку про сервіс
2. Система підготовлює форму з наступними полями:
    1. Оцінка 1-10 (обов’язкове)
    2. Коментар 
    3. Фото
3. Користувач заповнює форму
4. Система зберігає данні у БД відгуків
5. Система виводить повідомлення про успішне додавання відгуку

***Виключні ситуації:*** 
- Система тимчасово не доступна

- Незаповнені обов’язкові поля

!["Діаграма 6"](../images/dia6.png?raw=true)

!["Адміністратор"](../images/Адміністратор.png?raw=true)

!["Модератор"](../images/Модератор.png?raw=true)

!["Користвувач"](../images/Користувач.png?raw=true)

-------------

## Короткий огляд продукту

Данна система має можливість брати зображення з інтернет ресурсів та аналізувати статистику їх публікацій за різними критеріями. Система не націлена на конкретну категорії людей.

------------

## Функціональність

- Система повинна обробляти та виводити статистичні данні, у відповідності до запиту користувача
- Система повинна надавати зразки даних, над якими проводився аналіз
- Система повинна запропонувати користувачу зберегти данні у файл, за вказаним користувачем форматом

-----------

## Практичність

- Веб-сайт повинен бути оптимізованим для роботи не тільки із комп'ютера, а також із мобільних пристроїв.

-----------

## Надійність

- Система повинна бути добре захищена від різних зловмисних атак, мета яких є заволодіти інформацією.

- Система повинна обслуговувати велику кількість користувачів і витримувати велике навантаження.

- Система повинна виконувати резервне копіювання баз данних 

-----------

## Продуктивність

- Для більш продуктивної роботи системи, вона повинна бути розміщена, на кращих DNS-серверах 

----------

## Експлуатаційна придатність

- Система повинна підтримуватись усіма ОС платформи та повинна бути оптимізована під усі інтернет браузери
