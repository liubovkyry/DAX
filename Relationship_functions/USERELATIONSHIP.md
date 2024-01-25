![image](https://github.com/liubovkyry/DAX/assets/118057504/d8fea55e-d71e-448f-931e-5e356bfd34ea)

But you see here that or primary and or foreign are both noted in parentheses here.

And the reason for that is that the Dax engines will automatically swap these arguments if they're in

the incorrect order.

So if you put the primary key first and the foreign key second, the Dax engines will automatically

swap those for you.


Let's create a new relationship from transaction date to baked date.

![image](https://github.com/liubovkyry/DAX/assets/118057504/6413b48b-3f6a-41cb-87d3-44902cfc8076)


And what we want to do here is we actually want to evaluate the sum of quantity sold, right?

This measure is looking at the quantity sold column from our food table and for our filter parameter

here, let's use use relationship and the foreign side of the relationship is going to be the food inventory

table and it's the baked date.

![image](https://github.com/liubovkyry/DAX/assets/118057504/48dc1b85-1035-4078-b5bd-31dacd14d74d)

We see something interesting happen here?

First of all, we have a blank row here that has 478 here.

And then our values for each year are different, right?

The quantity sold here using use relationships.

So this is based on the baked date is a little bit different than the quantity sold based on the transaction

date.

Thats because We started receiving pastries for our stores before we actually opened. And Calendar table starts with the day of the first transaction.
