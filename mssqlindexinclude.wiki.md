# MSSQL에서 인덱스를 만들때 INCLUDE 구문을 쓰는 이유


> If the column is not in the WHERE/JOIN/GROUP BY/ORDER BY, but only in the column list in the SELECT clause.

> The INCLUDE clause adds the data at the lowest/leaf level, rather than in the index tree. This makes the index smaller because it's not part of the tree

> This means it isn't really useful for predicates, sorting etc as I mentioned above. However, it may be useful if you have a residual lookup in a few rows from the key column(s)

http://stackoverflow.com/a/1308012

INCLUDE구문에 있는 컬럼들은 WHERE절에 쓸 때처럼 BTree의 Index에 들어가지는 않지만 Tree의 leaf node에 위치함으로써 데이터를 가져올때 약간의 성능향상과 인덱스 자체 크기를 줄이는 역할을 한다.


---


# 참조

http://msdn.microsoft.com/en-us/library/ms190806.aspx