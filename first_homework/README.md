#First_HOMEWORK
* создать новый проект в Google Cloud Platform, Яндекс облако или на любых ВМ, докере
  * Яндекс-облако
* далее создать инстанс виртуальной машины с дефолтными параметрами
  * ВМ чере GUI яндекса с убунтой  
* добавить свой ssh ключ в metadata ВМ
  * ssh-keygen сгенерирован командой ssh-keygen -t rsa  
* зайти удаленным ssh (первая сессия), не забывайте про ssh-add
  * не понял, про ssh-add логин сохранился при первом входе. Подключился через ssh "ip"
* поставить PostgreSQL
  * установка через sudo apt install postgresql
* зайти вторым ssh (вторая сессия)
* запустить везде psql из под пользователя postgres
* выключить auto commit
* сделать
в первой сессии новую таблицу и наполнить ее данными create table persons(id serial, first_name text, second_name text); insert into persons(first_name, second_name) values('ivan', 'ivanov'); insert into persons(first_name, second_name) values('petr', 'petrov'); commit;
* посмотреть текущий уровень изоляции: show transaction isolation level
* начать новую транзакцию в обоих сессиях с дефолтным (не меняя) уровнем изоляции
* в первой сессии добавить новую запись insert into persons(first_name, second_name) values('sergey', 'sergeev');
* сделать select * from persons во второй сессии
* видите ли вы новую запись и если да то почему?
* завершить первую транзакцию - commit;
* сделать select * from persons во второй сессии
* видите ли вы новую запись и если да то почему?
* завершите транзакцию во второй сессии
* начать новые но уже repeatable read транзации - set transaction isolation level repeatable read;
* в первой сессии добавить новую запись insert into persons(first_name, second_name) values('sveta', 'svetova');
* сделать select * from persons во второй сессии
* видите ли вы новую запись и если да то почему?
* завершить первую транзакцию - commit;
* сделать select * from persons во второй сессии
* видите ли вы новую запись и если да то почему?
* завершить вторую транзакцию
* сделать select * from persons во второй сессии
* видите ли вы новую запись и если да то почему? ДЗ сдаем в виде миниотчета в markdown в гите
