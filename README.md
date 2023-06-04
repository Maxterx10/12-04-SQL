# Домашнее задание к занятию "`12.4. SQL. Часть 2.`" - `Белов Максим`


### Задание 1
```sql
SELECT CONCAT(sf.first_name, ' ', sf.last_name) AS staff_name, c.city,  
       COUNT(cr.customer_id)  
FROM store s  
JOIN staff sf ON sf.staff_id = s.manager_staff_id  
JOIN address a ON a.address_id = s.address_id  
JOIN city c ON c.city_id = a.city_id  
JOIN customer cr ON cr.store_id = s.store_id  
GROUP BY sf.staff_id, c.city_id  
HAVING COUNT(cr.customer_id) > 300;  
```
![alt text](https://github.com/Maxterx10/12-04-SQL/blob/main/12-04-1.png)

---

### Задание 2
```sql
SELECT COUNT(1) FROM film f  
WHERE \`length\` > (SELECT AVG(\`length\`) FROM film f);  
```
![alt text](https://github.com/Maxterx10/12-04-SQL/blob/main/12-04-2.png)

---

### Задание 3
```sql
SELECT MONTH(r.rental_date) AS rd, COUNT(r.rental_id)  
FROM rental r  
GROUP BY MONTH(r.rental_date)  
HAVING rd = (SELECT d1 FROM (SELECT MONTH(p.payment_date) AS d1, COUNT(p.payment_id) AS c1  
FROM payment p  
GROUP BY MONTH(p.payment_date)  
ORDER BY c1 DESC  
LIMIT 1) AS t1);  
```
![alt text](https://github.com/Maxterx10/12-04-SQL/blob/main/12-04-3.png)
