### Задача 1

<br>\l для вывода списка БД
<br>\c для подключения к БД
<br>\dt для вывода списка таблиц
<br>\dt+ для вывода описания содержимого таблиц
<br>\q для выхода из psql  

### Задача 2

select attname, avg_width from pg_stats where tablename = 'orders'
<br>order by avg_width DESC limit 1;

<b>attname</b>

### Задача 3


create table orders_1 (LIKE orders);
<br>INSERT INTO orders_1 SELECT * FROM orders where price > 499;

create table orders_2 (LIKE orders);
<br> INSERT INTO orders_2 SELECT * FROM orders where price <= 499;


Чтобы избежать ручного разделения можно было изначально настроить партиционирование на таблице, указав при создании PARTITION by RANGE(price);


### Задача 4

pg_dump -U postgres  test_database > /var/lib/postgresql/backups/pgdumptesdb

для того чтобы добавить уникальности нужно в бекапе в секии CREATE TABLE к столбцу title добавить ограничение UNIQUE