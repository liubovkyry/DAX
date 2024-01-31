![image](https://github.com/liubovkyry/DAX/assets/118057504/c140f9a8-117d-4c18-aa45-af76c2b05f8e)
Treat as basically provides a way to virtually transfer filter context from one table to another, which

is essentially mimicking the behavior of a physical relationship.
So you could have something like treat as values and you're looking at a single column here.

You want to get all of the unique values from your calendar year ID column, or you could use treat

as and summarize and create a summary table that contains multiple columns and this instance using year

ID and our calendar month columns.



But in either example, you're creating a table containing one or more columns that will be mapped to

the column name.

So let's check out column name.

This is a list of columns that will be used to return all of the rows that are also present in the column

specified by the table expression.



So the column name here is going to create a list and return all of the rows that are also present in

the column name specified in the table expression.

So one big thing to note here is that the number of columns specified must match the number of columns

in the table expression and be in the exact same order.

Otherwise the virtual relationship will fail to work.

So, for example, here you would map the target sales year with your treat as values calendar year

and you would map your target sales year and target sales month to your tree, summarize calendar year

ID and calendar month.


![image](https://github.com/liubovkyry/DAX/assets/118057504/4f2f057f-e221-4072-af49-cc60cd14c559)

What I want to do here is walk through each definition of the parameter.

So first the table expression.

And I'm going to start off and we're going to define a variable here called store ID.

And I want to use table constructors to help illustrate this.

Let's create a single column table using table constructors that represents store ID, right?

And the other important part of this definition is that the table expression must be based on a physical

table within the data model, right?

We don't have to reference a physical table within the data model.

We just have to make sure that the expression is based on that table.

And that's what we've done here.

So from here I want to return.

And we're going to use treat as.

And the first expression and treat as is the table expression.

So this is the store ID table that we just created.

And this table doesn't live in our model, right?

It's a virtual table that we have just created by declaring this variable and the existing unrelated

column that we want to use to return all of the rows contained within this column is the store lookup

store ID column.

Store lookup.

Store ID.


So what we've just done is we have created a table that doesn't exist in our data model, a virtual

table that doesn't have a relationship with the store lookup table.

And we've said, hey, you're going to take these values and they're going to relate them to this column

in the store lookup table.

And the result that is returned is that all of the rows within this store lookup store ID column that

also exist within this table are returned.


![image](https://github.com/liubovkyry/DAX/assets/118057504/63901105-8c4e-4ba0-a3e6-f7f5c123179b)


![image](https://github.com/liubovkyry/DAX/assets/118057504/48c053e5-cdea-4cbe-80fc-4d89a7086ac8)


```
Bean Goal (treatas) = 
CALCULATE(
    SUM(
        'UNION Demo'[Bean/Teas Goal]
    ),
    TREATAS(
        Values(
            'Calendar'[Year_ID]
        ),
        'UNION Demo'[Year]
    ),
    TREATAS(
        Values(
            'Calendar'[Month_Name]
        ),
        'UNION Demo'[Month]
    )
)
```

So our first key objective here is based on the target sales union table.

We need to use TREATAS and create measures for the bean/tea, beverage, merchandise and food sales goals.

One of the first things that we need to understand here is that the union demo table is going to be

connected to the calendar table at the year and month level.

And at the same time, we also want to sum each of our category goals, right?

So in order to do that, we actually need to start off by using a CALCULATE statement.

So let's start off and we'll create a measure here.

And this first measure, I'll call Bean goal.


So here what we want to do is start off by calling calculate.

And what we want to calculate is the sum of our bean/tea goal from our union table for our filter arguments

here.

This is where we want to start using TREATAS.

And to do this all we need to do is start typing TREATAS and bring up this function.

And the first thing that we want to do is we want to define the table expression that is going to be

mapped to the unrelated columns.


So how do we do that?

Well, I like to use values here, and I'm going to use VALUES to reference the calendar.


We need to tie to the month and the year.

So I'm going to use the year ID column here.

And the column that is being mapped to this table expression is going to be the Union

Year column.



So here we're saying this is the table expression that is going to be mapped to an unrelated column.

And that unrelated column is the year column in our union demo table.

Okay, So from here we need to repeat this same thing for the month level.

So TREATAS VALUES.

And from our calendar table we want to take the month name.

And we want to map that to our Union Month name.

Here we've created.

Two relationships.

For the year ID and the month name, and we're tying those to our union demo table, right?

Because we have differing levels of granularity here.

```
Merchandise Goal (treatas) = 
CALCULATE(
    SUM(
        'UNION Demo'[Merchandise Goal]
    ),
    TREATAS(
        Values(
            'Calendar'[Year_ID]
        ),
        'UNION Demo'[Year]
    ),
    TREATAS(
        Values(
            'Calendar'[Month_Name]
        ),
        'UNION Demo'[Month]
    )
)
```


But there is another little challenge here for our key objective one and there was a bonus here to use

SUMMARISE with TREATAS.

So let's actually take a look at how we could do that.

So our syntax here still stays the same where we want to use TREATAS.

But instead of using VALUES here, let's use SUMMARISE.

And what we want to call first is the table expression, right?

We're using SUMMARISE.

This is our table expression.

We want to call the fields that we want to map.

So the first parameter of summarize here is the table, which is our calendar table, and then the different

columns that we want to add in are going to be the year ID.

And then the month name.

```
Merchandise Goal (treatas) = 
CALCULATE(
    SUM(
        'UNION Demo'[Merchandise Goal]
    ),
    TREATAS(
        SUMMARIZE(
            'Calendar',
            'Calendar'[Year_ID],
            'Calendar'[Month_Name]
        ),
        'UNION Demo'[Year],
        'UNION Demo'[Month]
    )
)
 ```


So now we've accomplished that exact same thing, but instead this is a much more readable format.
