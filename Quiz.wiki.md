```SQL

SET ANSI_NULLS ON
SELECT
CASE
WHEN NULL = NULL THEN 'Hi'
WHEN NULL > 0 THEN 'Hoy'
WHEN NULL < 0 THEN 'Hey'
WHEN NULL = 0 THEN 'What?'
WHEN NULL = 1 THEN '1'
WHEN NULL != 1 THEN '2'
ELSE NULL
END
```