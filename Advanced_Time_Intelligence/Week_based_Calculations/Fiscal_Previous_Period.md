![image](https://github.com/liubovkyry/DAX/assets/118057504/0d22b8ff-6287-442c-93a5-e3c952a46422)

First, I'm using a variable here to define the entire measure, and we kick it off with CALCULATE.

And the expression that we're calculating in this example is customer sales, and customer sales is being calculated in a modified filter context, where we start off by clearing ALL of the filters from

our fiscal calendar table, and then we're returning a table that's filtered based on a logical expression.

One of the things to really pay attention to here is making sure that you update the fiscal period to either 4, 12 or 52, depending on the fiscal period that you're looking to return. So 4 for quarter, 12 for month, 52 for week.

#### Let's create our new measure.

And I'm going to call this last quarter to date sales for the 4 - 5 - 4  calendar.

 - And we're starting off with a variable here. We'll call this LastPeriod. And we start off with CALCULATE here.

And the expression that we want to evaluate is customer sales. And we're going to evaluate customer sales in a modified filter context where we're returning a table.

That we're going to remove ALL external filters, we're going to clear all external filters from the calendar table.

So this is how we're filtering the table that we want to return.

So we're going to say IF the SELECTEDVALUE. Of our fiscal quarter. Equals one, right?

So that's our logical expression.

IF the SELECTEDVALUE or the visible value right within our context equals one, then this is what we want to return.

If that's true, we want to look at this and say, all right, IF our fiscal quarter.

Equals four and the fiscal year. Equals. The selected value of fiscal year, meaning the current visible fiscal year.

Then we want to subtract one.

Remember, the whole point of this is how do you tell Power BI or the Dax engines with Dax to say,

Hey, if something equals one, I want you to shift to the previous year, right?

So we're saying that if the current visible quarter equals one, we actually want to return the previous period. So we need to look at the fourth quarter.

And if the fourth quarter is currently visible, then we want to shift back one year, right?

So if this is Q1 2018, this is saying shift back to Q4 2017.

Now our result, if false, we want to say if the fiscal year equals the current selected fiscal year using selected value.

And the fiscal quarter equals the selected value.

Write the current fiscal quarter.

Then we just want to subtract one.

So the second argument is saying if the quarter doesn't equal one, then all we want to do is within that current year, just subtract one from the quarter.

```
Last QTD Sales (4-5-4) = 
VAR LastPeriod = 
CALCULATE(
    [Customer Sales],
   FILTER(
     All(
        '4-5-4 Calendar'),
        If(
            SELECTEDVALUE('4-5-4 Calendar'[FiscalQuarter]) =1,
            '4-5-4 Calendar'[FiscalQuarter] = 4 
            && '4-5-4 Calendar'[FiscalYear] = SELECTEDVALUE('4-5-4 Calendar'[FiscalYear]) - 1,
            '4-5-4 Calendar'[FiscalYear] = SELECTEDVALUE('4-5-4 Calendar'[FiscalYear] )
            && '4-5-4 Calendar'[FiscalQuarter] = SELECTEDVALUE('4-5-4 Calendar'[FiscalQuarter]) - 1
        )
   )
)
Return LastPeriod
```

![image](https://github.com/liubovkyry/DAX/assets/118057504/35e5cd7b-1b67-4a6b-bdd7-6701d2fa9f86)

And here what's happening is because we're using SELECTEDVALUE, it can't determine a single value for 2018, 2017 or a Total row. So it's defaulting to a blank value.

