# goit-rdb-hw-07

## task 1
```sql
Select 
id, date, year(date) as year, month(date) as month, day(date) as day 
from orders;
```

## task 2
```sql
Select 
id, date, date_add(date, interval(1) day) as plus_day
from orders;
```

## task 3
```sql
Select 
id, date, floor(unix_timestamp(date)) as unix_timestamp
from orders;
```

## task 4
```sql
Select count(id) as count from orders
where date >= '1996-07-10 00:00:00' and date <= '1996-10-08 00:00:00';
```

```sql
Select count(id) as count from orders
where date between '1996-07-10 00:00:00' and '1996-10-08 00:00:00';
```

## task 5
```sql
Drop function if exists createJsonDate;

Delimiter //
Create function createJsonDate(id int, date date)
returns json
deterministic
no sql
begin
	declare result json;
    set result = json_object('id', id, 'date', date);
    return result;
end //
Delimiter ;

Select id, date, createJsonDate(id, date) as json_date from orders;
```
