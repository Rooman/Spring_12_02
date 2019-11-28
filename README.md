#Spring_12_02

![alt tag](https://github.com/Rooman/Spring_12_02/blob/master/springDiagram.png)

<h3>Задача: перевести все приложение на спринг.</h3>
<ol>
<li>Сделать бинами все бизнес объекты</li>
<li>Все зависимости организовать в xml</li>
<li>MockDataStore должен быть бином, описаным в xml;</li>
<li>Создать два класса UserCache и AccountCache, которые должны вычитывать данные из MockDataStore при старте, чтобы избежать постоянного обращения к хранилищу.</li>
<li>Инициализация кэшей должна происходить сразу после создания бина</li>
<li>Тесты должны быть запущенны через стандартный механизм для поднятия тестового контекста спринг</li>
<li>Все зависимости (по возможности) организовать через аннотации @Service, @Repository </li>
</ol>

<h3>Подключаем JdbcTemplate</h3>
<ol>
<li>Подключаем embedded database h2</li>
<li>Создаем схему и накатывает данные с помощью заранее заготовленных скриптов. (Скрипты помещаем в test/resources)</li>
<li>Инжектим JdbcTemplate в наши Dao объекты. Реализуем методы для взаиможействия с базой (update, get, getAll для кеширования)</li>
<li>Мигрируем на MySQL. Данные для доступа находим в C:/Materials/MySQL credentials</li>
<li>С помощью MySql Workbench (отдельное приложение в системе) накатываем схему и данные на базу</li>  
<li>Выносим конфигурация для датасорса в проперти файл. В файле с контекстом используем плейсхолдеры.</li>  
</ol>

<h3>Подключаем Spring AOP</h3>
<ol>
  <li>Переделывает кеши для данных. При обращении в get*ById проверяем значение в кеше, если есть, возвращаем из кеша, если нету, пробрасываем вызов в проксируемый объект и сохраняем значение в кеше.</li>
  <li>Для контроля размера кеша используем SoftReference</li>
</ol>
