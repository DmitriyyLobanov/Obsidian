 2024-09-29 12:42

WHERE плохо работает с агрегатными данными
Запрос
```sql
SELECT
	BillingCity,
	AVG(Total)
FROM
	invoices
WHERE
	AVG(Total) > 5
GROUP BY
	BillingCity
ORDER BY
	billingCity;
```

Выдаст ошибку "Misuse of aggregate: AVG()"

Если необходима дополнительная фильтрация на основе агрегатных функций, необходимо включить вторичную фильтрацию, известную как условие HAVING.

Условие HAVING всегда следует ПОСЛЕ GROUP BY (и без него НЕ ИСПОЛЬЗУЕТСЯ)

Измененный запрос:
```sql
SELECT
	BillingCity,
	AVG(Total)
FROM
	invoices
GROUP BY
	BillingCity
HAVING
	AVG(Total) > 5
ORDER BY
	billingCity;
```

А вот пример запроса в котором есть и WHERE и HAVING
```sql
SELECT
	BillingCity,
	AVG(Total)
FROM
	invoices
WHERE
	BillingCity like 'B%'
GROUP BY
	BillingCity
HAVING
	AVG(Total) > 5
ORDER BY
	billingCity;
```


[[операторы SQL]]
#SQL 
#Learn