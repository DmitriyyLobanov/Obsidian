 2024-11-05 15:32

_constraint_ или _ограничение_ — это правило, накладываемое на данные в таблице для обеспечения их корректности, целостности и согласованности. Constraints помогают гарантировать, что данные, которые вставляются, обновляются или удаляются, соответствуют определённым условиям. Вот основные типы ограничений в PostgreSQL:

1. **NOT NULL** — запрещает значение `NULL` в указанном столбце. Это значит, что каждое значение в этом столбце должно быть определено.
   
 ```SQl
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);
```

2. **UNIQUE** — обеспечивает уникальность значений в одном или нескольких столбцах. Например, в таблице сотрудников можно запретить дублирование номеров паспортов.
   
```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    passport_number VARCHAR(20) UNIQUE
);

```

3. **PRIMARY KEY** — объединяет два ограничения: `NOT NULL` и `UNIQUE`, гарантируя уникальность идентификатора строки в пределах таблицы. В PostgreSQL часто используется для автоинкрементных столбцов `id`.
   
```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);

```

4. **FOREIGN KEY** — указывает, что значение в одном столбце или наборе столбцов должно соответствовать значению первичного ключа или уникального столбца в другой таблице. Это ограничение поддерживает связь между таблицами и поддерживает целостность данных.
   
```sql
CREATE TABLE departments (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    department_id INT REFERENCES departments(id)
);

```
   
   5. **CHECK** — позволяет задать произвольные логические условия для значений столбцов. Например, ограничить возраст сотрудников значением больше 18 лет.  

```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT CHECK (age > 18)
);

```
   
   6. **EXCLUDE** — используется в PostgreSQL для более сложных условий, например, предотвращения пересечения значений диапазона в нескольких строках. Часто применяется для диапазонных типов данных, таких как `tsrange` (интервалы времени).

```sql
CREATE TABLE meetings (
    id SERIAL PRIMARY KEY,
    time_slot tsrange,
    EXCLUDE USING gist (time_slot WITH &&)
);

```
   
[[SQL]]
#Learn