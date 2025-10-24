### Запрос 1
```sql
  SELECT email, COUNT(*) AS dublicate_number
  FROM Staff
  GROUP BY email
  HAVING COUNT(*) > 1;
```


### Запрос 2
```sql
  SELECT name, birthday, 
  FLOOR(DATEDIFF(CURDATE(), STR_TO_DATE(birthday, '%d.%m.%Y')) / 365) as age
  FROM Staff;
```
### Запрос 3
```sql
  SELECT Jobtitles.name, salary
  FROM Jobtitles INNER JOIN Staff ON Jobtitles.jobtitle_id = Staff.jobtitle_id
  WHERE salary = (
      SELECT DISTINCT salary
      FROM Staff
      ORDER BY salary DESC
      LIMIT 1 OFFSET 1
  );
```
