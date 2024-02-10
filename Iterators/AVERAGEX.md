![image](https://github.com/liubovkyry/DAX/assets/118057504/169f3e56-0da5-49ce-96b1-0ecebc8ed552)

The first parameter is the table, and this can be a physical table in the model or an expression that

creates a table.

This table contains all of the rows that are going to be evaluated by the expression.

So, for example, you might choose the calendar table or the product lookup table as this input or

potentially create some sort of other table based on an expression.

Next, we have the expression that we want to evaluate, right?

That's the second parameter of the average x function and some examples of the expression that you may

want to evaluate could be something like your customer sales measure or the sum of quantity sold or

the count of the rows in a table, something like that.

![image](https://github.com/liubovkyry/DAX/assets/118057504/3f2a40ed-cef6-4c5b-b0c1-f71bdc8d87b1)


(Calendar table is at the daily level and we want to iterate our expression, the customer sales for

every day.)


![image](https://github.com/liubovkyry/DAX/assets/118057504/5a4354ff-f1e0-42f6-8a40-c4478cd7f050)





First up, we're using variables to define certain parameters for our inputs.

The first one that we're using is for last transaction date, and we're using a max function here that

is going to look at our Max transaction date based on our current filter context and our visual.



Next, we're defining the average days.

So this is the number of days that we actually want to adjust by within the period, right?

So we could update this to seven to look at the previous week, 14 for the previous two weeks, so on

and so forth for the period and visual we're using FILTER, ALL and AND to <b>define the time period of the

rolling window.</b>



And the rolling window is based on the last transaction date and the current filter context of the visual

meaning that if the point in the visual is July 28th, 2018, that's the latest date in the current

filter context, If it was September 6th, 2018, that would be the latest date in the current filter

context.

And the function is adjusting 30 days back based on that last visible transaction date.



So once we have that window defined, we can then use CALCULATE to return the average daily customer

sales for the period we've defined.

And one thing to <b>note</b> here is that you could actually turn this moving average code into a rolling total

or a rolling count by substituting something like SUMX or COUNTX for where you see AVERAGEX here

below CALCULATE.

So you could use this to calculate a moving sum or a moving count within the same period.



Lastly, we return the output of this equation to close out the measure.


### Pro tip here 


One of the things that you can actually do is you could create a <b>parameter</b> and substitute that for our

average days, that static average day value.

And this would let you create a dynamic user defined period that would automatically adjust within the

visual.


```
Moving Average (averagex) = 
VAR LastTrasDate = MAX('Calendar'[Transaction_Date])
VAR AvgDays = 30
VAR PeriodInVisual = 
FILTER(
    ALL(
        'Calendar'[Transaction_Date]
    ),
    AND(
        'Calendar'[Transaction_Date] > LastTrasDate - AvgDays,
        'Calendar'[Transaction_Date] <= LastTrasDate
    )
)
VAR OutPut = 
CALCULATE(
    AVERAGEX(
        'Calendar',
        [Customer Sales]
    ),
    PeriodInVisual
)
RETURN OutPut


```


Let's create our measure.

And I'm going to call this moving average.

Moving average X.

1) The first thing that we're going to do is we're going to define those variables that we saw, right?

So the first variable that we want to define is the last transaction date.

And this is going to equal MAX Calendar table of the transaction date from our calendar table.



2) The next variable we want to define is the average days, right?

So the number of days within the period that we want to look back and I'm going to set this to 30.


3) Next up is we need to create the time period within the visual.

So period and visual

and this is where we're going to use FILTER. With ALL. And the calendar table. Transaction date.


So what we said right there is basically we're using Filter to return a table and we want it filtered

based on certain parameters.

 - And the first thing that we're doing is we're clearing all of the filters that may exist on transaction

date.

 - The second thing that we want to do is we want to use and and allows us to create a logical expression

that if both arguments evaluate to true, then it will return true:

   So here's where we want to enter in the logical statements to basically time box this 30 day period.

So again, this is going to be based on the calendar transaction date.

AND this is if it's greater than. The last transaction date minus. The average days. 
AND the transaction date. Is less than or equal to the last transaction date.


Then we'll return True.

So what this block of code here is saying this filter parameter for filter is that let's use a specific

date as an example here.

So for our first parameter of and here we're looking to see if this evaluates to true, right?

So if July 28th, the current calendar date is greater than the last transaction date here, which is

also the max date based on the current context.

So this is basically saying July 28th is greater than July 28th, -30.

If that's true, and if July 28th is less than or equal to July 28th, then return True.

And because both of those evaluate to true, what we're doing is we're providing a filter here.

If again, if this was July 28th, we're providing a table that's filtered from June 28th to July 28th.

So that's a breakdown of exactly what's happening here within the filter parameter of this function.


4) So now we're going to create another variable for the output.

And this is where we're going to use CALCULATE.

Write the expression that we want to calculate is going to be the same average expression  to create the daily customer sales.

So we want to look at the calendar table and the expression is going to be Customer sales.

And our filter - It's going to be PeriodInVisual.



5) And then lastly, what we need to do here is RETURN the output.





 And we're going to create a line and clustered column chart that is going to look at the transaction

date, customer sales and our average sales.


![image](https://github.com/liubovkyry/DAX/assets/118057504/d4e8db37-d54c-48bb-af91-77b0f3dd7b75)


Now we have a 30 day moving average that is layered over our sales, right?

So here on June 16th, 2018, our moving average for the last 30 days, our average sales over the last

30 days was $5,709.63.

We check out another value here November 30th, 2018.

Our average sales for the last 30 days was $6,147.



So that's how you create a moving average using average and some variables. 
