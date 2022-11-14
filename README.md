# 12.4-SQL.--Part-2-
**Задание 1.**

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей и выведите в результат следующую информацию:

•	фамилия и имя сотрудника из этого магазина,

•	город нахождения магазина,

•	количество пользователей, закрепленных в этом магазине.
![1](https://user-images.githubusercontent.com/100844122/201645792-9b3fdcb7-9846-4f1d-b839-b8659cb990e9.png)


**код** 

select s.first_name, s.last_name, city, count(c2.fist_name)

from staff s

join address a on a.address_id = s.address_id

join city c on c.city_id = a.city_id

join customer c2 on c2.customer_id = c2.customer_id

group by c.city, s.first_name, s.last_name

having count(c2.customer_id) >300

 
 

**Задание 2.**

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

 
 ![2](https://user-images.githubusercontent.com/100844122/201645969-69f097f6-583f-46ed-a501-21683b902064.png)

select count(film_id) from film

where `length` > (select avg(`length`) from film);

 
**Задание 3.**

Получите информацию, за какой месяц была получена наибольшая сумма платежей и добавьте информацию по количеству аренд за этот месяц.

![3](https://user-images.githubusercontent.com/100844122/201646036-95b8b7c2-8b12-450d-9487-6dd8f975ec9e.png)



select month(payment_date), count(payment_id), sum(amount)

from payment

group by month(payment_date)

order by sum(amount) desc

limit 1;

