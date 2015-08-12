# JOIN Operation 설명

## Nested Loops

Joins two tables by fetching the result from one table and querying the other table for each row from the first. SQL Server also uses the nested loops operation to retrieve table data after an index access.

## Hash Match

The hash match join loads the candidate records from one side of the join into a hash table which is then probed for each row from the other side of the join.

## Merge Join

The merge join combines two sorted lists like a zipper. Both sides of the join must be presorted.


---


http://use-the-index-luke.com/sql/explain-plan/sql-server/operations

http://blog.codinghorror.com/a-visual-explanation-of-sql-joins/