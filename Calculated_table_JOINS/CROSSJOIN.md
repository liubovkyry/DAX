![image](https://github.com/liubovkyry/DAX/assets/118057504/ca462a12-b8fd-436c-ab8b-c6ba1527501b)

 CROSSJOIN is a function that returns a single table that contains the Cartesian product of the specified

tables.



Cartesian means it's the product of two sets, forming a set containing all ordered pairs, saying that

a little bit differently.

CROSSJOIN Returns, a table that contains all of the combinations of the input tables.

All right, let's cover a few important notes before we jump into Power BI.

First up, you can't have the same columns present in any of the tables that you want to combine.  With

CROSSJOIN all of the column names must be different in all of the table arguments.

So if you repeat a column name in between tables, you'll receive an error.

Second, the number of rows returned in the result table will always equal the product of the rows in

all tables.

And third, the number of columns returned in the output table will equal the sum of the columns in

all tables.
