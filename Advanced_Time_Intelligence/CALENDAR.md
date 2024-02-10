![image](https://github.com/liubovkyry/DAX/assets/118057504/564f5f9b-43bd-4518-bbc8-8925b140657f)

All right, so we're in power BI Let's head over to our data view and I want to create a new table and

we'll call this calendar demo

and we're going to start off with entering the calendar function.

And we can use anything that represents a start date or an end date.

So one thing that we could do here is because all Dates and Power BI are represented as floating point

numbers, we could very simply enter the following values that would return a list of dates.

So say we wanted to look at this for 2020.

The first day of 2020 is 43831 and the last date of 2020 is going to be 44196.

```
Calendar Demo = 
CALENDAR(
    43831,
    44196
)
```

OR

```
Calendar Demo = 
CALENDAR(
    DATE(2020,01,01),
     DATE(2020,12,31)
)
```
Both of those examples return the exact same list of dates.

OR

```
Calendar Demo = 
CALENDAR(
    DATE(YEAR(MIN('Calendar'[Transaction_Date])),1,1),
    DATE(YEAR(MAX('Calendar'[Transaction_Date])),12,31)
)
```

