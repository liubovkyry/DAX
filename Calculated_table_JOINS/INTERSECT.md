![image](https://github.com/liubovkyry/DAX/assets/118057504/18559593-1128-4b51-b6c3-5207aff25496)

Similar to ACCEPT, INTERSECT only accepts two tables as parameters that will be used for joining.

And similarly, the first table must be a table that physically resides within the data model.

Typically INTERSECT is used to determine something like active customers during a time period or repeat

purchases and subsequent weeks, or new employees that have started within a specific time frame.

So in our example here, we're looking at determining previous month active customers.

So in this case, the left table is using the sales table to grab the unique IDs of the customer.

And we're doing that using the values function.

And our right table is performing a similar action, but is also introducing a date threshold here where

we want to move back one month.

So as a result, we'd be looking to understand the intersection of these two tables or the records that

appear within both of them.

![image](https://github.com/liubovkyry/DAX/assets/118057504/a1568d70-89dd-49f9-9d03-f96d71618235)

It gives us an understanding of what we can do to use Intersect to combine two tables.

Well, let's take this one step further and actually add in a column to this, right?

So let's say we wanted to see the amount of customer revenue that each one of our employees had driven.


![image](https://github.com/liubovkyry/DAX/assets/118057504/f71daf40-2a91-410d-87fd-56d99668f8d2)





So we're seeing here that each table argument of Intersect must have the same number of columns.

![Uploading image.png…]()

So what we actually have to do is add in another add columns below here to our right table.
