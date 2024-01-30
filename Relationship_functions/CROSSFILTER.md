![image](https://github.com/liubovkyry/DAX/assets/118057504/fdb3dd39-aa2f-4679-b26f-6822efad6c1e)


Instead of setting up bidirectional filters in your data model by using cross filter, you can actually

enable two way filtering for only specific cases meaning for the duration of the calculation of the

measure that you're using it in.


![image](https://github.com/liubovkyry/DAX/assets/118057504/a8433574-06ca-417f-92c2-35da0b10755a)



![image](https://github.com/liubovkyry/DAX/assets/118057504/52278c19-2318-44ac-a3b5-f8da727086b6)



![image](https://github.com/liubovkyry/DAX/assets/118057504/cfa97cbb-74a0-40d0-9a79-731d156f7477)



1)
```
Customer who purchased = 
CALCULATE(
    COUNTROWS('Customer Lookup'),
    CROSSFILTER('Sales by Store'[customer_id],
    'Customer Lookup'[customer_id],
    both)
)
```

We'll create a new measure.

And we need to call this customers Who purchased.

And we need to COUNTROWS and CROSSFILTER with this.

But remember that we actually have to start this off with a CALCULATE statement because CROSSFILTER

has to work with an argument that has a filter expression.

So we'll start off with COUNTROWS. And here we are looking at our customers.


So we want to look at the customer table.

And then for our filter expression, this is where we're going to use CROSSFILTER and our left table is going to be the customer ID from the sales by store table.


That's our foreign key.

And then our primary key is going to be the customer lookup, customer ID and then the filter direction

we're going to set to both.

We want to make sure that those relationships traverse between the tables.

So that is key, objective number one.

Now let's move on to our second key objective, where we need to create a measure that calculates the

average order value for customers who purchased.

```
Average order value = 
DIVIDE(
    [Customer Sales],
    [Customer who purchased],
    BLANK())
```

We want to take customer sales and divide that by the customers who purchased.

And our alternate result, I'm going to use blank.

Up next, for our third key objective, we need to create a matrix that shows the previous two measures

broken down by Darren's request.

![image](https://github.com/liubovkyry/DAX/assets/118057504/c85ab023-ef2e-4d87-90d4-563d966bad8a)


