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


![image](https://github.com/liubovkyry/DAX/assets/118057504/e16358cd-d475-4ddf-968b-6cdb9d1761e4)

So both of these are lookups should have relatively small cardinality number of rows.

And you can see here that we have 348 rows and, you know, a bunch of columns between both of the tables.

So, again, just like we saw in the slides, what's happened here is the cross join function is combining

product lookup and store lookup and is creating all of the combinations between those two tables.

So in this example, it may not be very beneficial to create a table like this.

You may have other use cases where you'd like to return a table that only contains a couple of values

or a smaller number of values.

Let's look at how we can do that with CROSSJOIN.

So we'll change the table inputs here.

And remember, one of the things that you can do with CROSSJOIN is it doesn't take just physical tables.

It also takes calculated tables.
So let's use VALUES, right?

And if we remember, what VALUES does it returns a unique list of values when supplied with a column

name.

![image](https://github.com/liubovkyry/DAX/assets/118057504/6ce15bce-6382-464b-bf55-9630dc79030d)
