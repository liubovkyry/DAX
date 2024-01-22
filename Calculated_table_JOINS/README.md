![image](https://github.com/liubovkyry/DAX/assets/118057504/2d29232c-5b0f-4cd8-8cbe-6a794cbab9d5)

![image](https://github.com/liubovkyry/DAX/assets/118057504/cc680b68-0121-4392-a95c-ada08699cc8e)


1)   So our first objective is to use calculate Table and Intersect to understand returning customers between

our date range.

So November 18th 2018 and December 1st, 2018.

And to start off we're going to create a new table.

And let's call this table repeat customers.

So the first table I want to define is going to be for customers who purchased in week 45.
And we want to now define our returning customers.

So we're going to create another variable.

And let's call this returning customers.

And here we're going to use the intersect function.

And what we want to do is we want to specify the left and right tables to use, which are these tables

we just created.

#### And remember that when you're using intersect that the order of the tables can matter.

![image](https://github.com/liubovkyry/DAX/assets/118057504/03935733-2d50-4eb9-95a5-81dc5e581c37)


2)   Our second key objective is to add additional columns for revenue and profit, and then calculate the

totals for this entire customer group.

And what we need to do here is we're actually going to create another variable.

And similarly here in in order to accomplish this I first want to use calculate table again.

Because we want to return a table as our output.

The second piece that we want to use is Add columns.

We want to add the revenue and profit columns into our returning customers table.

Right.

So our next input here is the table that we want to define.

Or the table that we're going to add the columns to.

Our first column, let's call this revenue.

And we're going to use our customer sales measure.

As our input here.

Next we want to define profit.

And here we can also use the profit measure.

Now, the last piece here that we need to do is actually define a filter for calculate table.

And what we want to do is add in a filter for the week ID from the calendar table, where this equals

46.

And the reason that we want to do this is because if we didn't add in this filter, the output table

from this revenue and profit variable would actually show all of the revenue and all of the profit for

all of the customers that are in that returning customer set.
![image](https://github.com/liubovkyry/DAX/assets/118057504/a2a3bc0c-d772-4338-9a9c-937ca7e2b2d0)
