
![image](https://github.com/liubovkyry/DAX/assets/118057504/95807020-5f07-466f-82b9-7fea876fb7b3)

Note: The only parameter - Date, can reference a date column that exists in your model or a table expression that results in a single column table containing dates.

Either way, the date range must be contiguous. There can't be any missing, duplicated or omitted dates.

```
Last Quarter's Sales (Paralelperiod) = 
CALCULATE(
    [Customer Sales],
    PARALLELPERIOD(
        'Calendar'[Transaction_Date],
        -1,
    QUARTER
    )
)
```


```
Last Quarter's Sales (Previousquarter) = 
CALCULATE(
    [Customer Sales],
    PREVIOUSQUARTER('Calendar'[Transaction_Date]))
```

![image](https://github.com/liubovkyry/DAX/assets/118057504/37fd28c5-c87b-44ce-8298-e2fbdda2b862)


And you see,  we're returning at the row level here. The same exact repeat totals.  And then when we get to the total rows, they're very different.

What's interesting here is we actually don't have a date filter applied.

So the initial filter context here is what what's the first visible date in our table? January 1st, 2017.

There's no data available for the previous quarter there, so it doesn't return a value. That's why it's blank in this case.

![image](https://github.com/liubovkyry/DAX/assets/118057504/c09f7e66-0d9f-4819-b8f0-f5e04f8ec164)

Our results are filtered down, but we're still receiving our entire Q1 total in June and so on and so forth.

And now we have our grand total is showing up here because that initial filter context has changed here.
