
![image](https://github.com/liubovkyry/DAX/assets/118057504/eb24558d-780c-4753-93d3-af2d609285b6)

![image](https://github.com/liubovkyry/DAX/assets/118057504/76788bca-a205-445b-9265-d9c6424e39b7)



![image](https://github.com/liubovkyry/DAX/assets/118057504/5bba9ba5-7d1d-4cd9-839f-d94504ae5818)

### Our first key objective is to use time intelligence functions to calculate total sales for the previous month, as well as the percent change month over month.

```
CS Last month = 
CALCULATE([Customer Sales],
PARALLELPERIOD('Calendar'[Transaction_Date],-1,MONTH))
```

Next, we need to create a month over month percent change for our customer sales.

```
CS MoM % Change = 
DIVIDE(
    [Customer Sales] - [CS Last month],
    [CS Last month],
    BLANK()
)
```

### Our second objective is to calculate year over year change in sales from April 2018 versus April 2019.

```
CS YoY % Change = 
VAR LastYear = 
CALCULATE(
    [Customer Sales],
    SAMEPERIODLASTYEAR('Calendar'[Transaction_Date]))
VAR Ratio =  
DIVIDE(
    [Customer Sales] - LastYear,
 LastYear,
  "-")
RETURN Ratio
```
