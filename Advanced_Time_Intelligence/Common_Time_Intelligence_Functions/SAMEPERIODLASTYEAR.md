
![image](https://github.com/liubovkyry/DAX/assets/118057504/6bd425a7-4313-48b5-bd49-881b5717df9a)


In our example here we have a matrix with year and month on the rows and year to date sales.

I'm using date year to date as the function to calculate that and last year sales using same period last year and those are both on the values.

Additionally we have a date slicer that's filtering the matrix from March 24th, 2018 to April 30th, 2019.

Now let's look at a couple of values to see if we can understand exactly what's happening at the row level.

First, let's look at March 2018 and here we see a value of 25,099.

The initial filter context of the cell is where date equals March 24th through March 31st.

And that same period one year ago is March 20th 4th to March 31st, 2017.


So that's what it's computing total sales for in this case, same period last year, isn't throwing that initial filter context out the window.


It's not computing the entire period like we've seen.

It's actually filtering and returning partial results when the dates are being filtered.

In this case, it's by a slicer and it could be by a visual level filter or some other filter.



Next, let's look at the total row for 2019 here.

The initial filter context for the cell is January 1st, 2019 through April 30th, 2019.

And because of that, it's only returning 2018 year to date sales through April 30th.

So again, it's all based on what that initial filter context is within the visual.

One last important piece here is it's vitally important to understand how the initial filter context impacts the row and total level values.

If you don't, you'll likely think something is wrong with your measure or that it's being filtered in some other way.

![image](https://github.com/liubovkyry/DAX/assets/118057504/c277f3e2-e421-4695-9fe2-eedc840666fe)


```
Last YEars Sales (sameperiodlastyear) = 
CALCULATE([Customer Sales],
SAMEPERIODLASTYEAR('Calendar'[Transaction_Date]))
```

