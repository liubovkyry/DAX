![image](https://github.com/liubovkyry/DAX/assets/118057504/963ea84a-21fa-4769-9165-84197d77ed35)

Weak based calculations like previous weak sales or same week last year or same week last quarter or

month can be particularly challenging for a handful of different reasons.


1)  First, within the Dax functions, there aren't any standard time intelligence functions that would

allow you to easily add in an interval in a week period.

There's nothing exists.

The closest thing that you could try is to use the date add function with a interval of minus seven at the daily level.



2)  Another reason why it can be challenging is that weeks can start on various days like Sunday or Monday

or any day of the week. And these can differ across industries.


3)  Third, there can be partial weeks in any given month or quarter or year.

For example, a lot of calendars have a partial 53rd week throughout the year and last week start and

stop on different days each month and can be grouped differently based on different fiscal calendars.



![image](https://github.com/liubovkyry/DAX/assets/118057504/1b3b6a61-04d0-46dc-9131-1278997dc5ab)


And the whole purpose of a fiscal calendar is to normalize the number of days in a week, the number of weeks within a month, and then the number of weeks within a year.

So let's take a look at the column containing November, December and January.

And just to call this out, this January here is actually January 2021, but it's a part of the 2020 fiscal calendar.

These three months represent Q4 2020.

And within each of these months, there's a standardized number of weeks.

There's four weeks in November, four weeks in December, and then five weeks in January.

So the whole point of this is that these types of calendars are standardizing the number of months in a quarter and then the number of weeks within each month.

So if this was a 4 or 5 for calendar, there would be four weeks, five weeks and then four weeks.

Fiscal calendars can't be used with standard time intelligence functions.



![image](https://github.com/liubovkyry/DAX/assets/118057504/5f331d53-8453-47c4-a2ab-6fa408b69c1d)


1) So our first key objective is that we need to use the 4-5-4 calendar and customer sales measure to create measures for year to date and month to date sales.

   ```
   MTD Sales (4-5-4) = 
VAR MaxDate = MAX('4-5-4 Calendar'[Date])
VAR MaxPeriod = MAX('4-5-4 Calendar'[FiscalMonthYear])
VAR Output = 
IF(
    HASONEVALUE(
   '4-5-4 Calendar'[FiscalMonthYear]),
   CALCULATE(
    [Customer Sales],
    '4-5-4 Calendar'[Date] <= MaxDate,
    '4-5-4 Calendar'[FiscalMonthYear] = MaxPeriod),
    "-"
)
RETURN Output

```
YTD Sales (4-5-4) = 
VAR MaxDate = MAX('4-5-4 Calendar'[Date])
VAR MaxPeriod = MAX('4-5-4 Calendar'[FiscalYear])
VAR Output = 
IF(
    HASONEVALUE(
   '4-5-4 Calendar'[FiscalYear]),
   CALCULATE(
    [Customer Sales],
    '4-5-4 Calendar'[Date] <= MaxDate,
    '4-5-4 Calendar'[FiscalYear] = MaxPeriod),
    "-"
)
RETURN Output
```

![image](https://github.com/liubovkyry/DAX/assets/118057504/959dcc90-6dd0-4781-9361-56f37da6f3f5)

What's interesting here is the IF HASONEVALUE expression isn't working here. (Repeating Values)

And if we go back into the measure, we can see that this actually evaluates to true.

There's only one fiscal year.

When we get down to 2019 and because our calendar table actually extends all the way through the end

of the 2019 fiscal year, that's why we're seeing these repeating values.

It's not wrong. 

We can do the following:

```
YTD Sales (4-5-4) = 
VAR MaxDate = MAX('4-5-4 Calendar'[Date])
VAR MaxPeriod = MAX('4-5-4 Calendar'[FiscalYear])
VAR MaxSellDate = MAX('Sales by Store'[transaction_date])
VAR Output = 
   CALCULATE(
    [Customer Sales],
    '4-5-4 Calendar'[Date] <= MaxDate,
    '4-5-4 Calendar'[FiscalYear] = MaxPeriod,
    'Calendar'[Transaction_Date] <=MaxSellDate)
  

RETURN Output
```
![image](https://github.com/liubovkyry/DAX/assets/118057504/f69d5a8f-6114-4cee-b789-522a50eb2a65)

2) So our second key objective is to create a measure to compute week over week percent change.

   ```
   WOW % Change = 
DIVIDE(
    [Customer Sales] - [Last week sales 4-5-4 (Dateadd)],
    [Last week sales 4-5-4 (Dateadd)])

  ```

3) Our third key objective is to create a matrix or two to visualize your results.

![image](https://github.com/liubovkyry/DAX/assets/118057504/637c9c7e-5bb0-41f6-94dd-6656bca8b8c4)

