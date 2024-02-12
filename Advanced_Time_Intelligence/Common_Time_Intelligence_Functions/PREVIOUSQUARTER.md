
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
