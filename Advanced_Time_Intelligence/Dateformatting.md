![image](https://github.com/liubovkyry/DAX/assets/118057504/a5f0b3e1-24cb-4f82-85fb-a2fc5b32797f)


![image](https://github.com/liubovkyry/DAX/assets/118057504/3b49d998-4505-4a62-822e-b5624de71e99)

1) 

```
Weekday name = 
FORMAT(
    'Calendar'[Transaction_Date],
    "dddd"
)
```


2)

```
Weekend? = 
IF( 
    WEEKDAY(
        'Calendar'[Transaction_Date],
        2 
        )
         IN {6,7},
          "Y",
          "N")
```

3)

```
% total sales = 
VAR AlLSales = 
CALCULATE(
    [Customer Sales],
    ALL(                      --Removing ALL filters from the Sales by store table
        'Sales by Store'
    )
)
VAR Ratio = 
DIVIDE(
    [Customer Sales],
AlLSales
)
Return Ratio

```

![image](https://github.com/liubovkyry/DAX/assets/118057504/b51fd396-d748-4c9c-b4bd-e9f0f732ca8d)
