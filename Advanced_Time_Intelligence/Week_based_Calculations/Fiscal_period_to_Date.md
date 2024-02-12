![image](https://github.com/liubovkyry/DAX/assets/118057504/d0563543-3172-424a-903d-641859b403e9)

So here's an example of the Dax code pattern for quarter to date performance.

So we first start off by defining two variables max date and max period.

And max date is based on the date column within the four, five four calendar table and max period is looking at the fiscal quarter column.

One thing to point out here is when we imported the fiscal calendar table, you could see that we had all of those columns written out for fiscal year, fiscal quarter, fiscal month, fiscal week. 

They help you enable these types of calculations. This is the reason why you need to clearly and accurately define all of those types of columns within

that fiscal calendar table, because it's really the only way to reference these kinds of periods.

 - So after that, we jump into IF HASONEVALUE. And the purpose of this is to basically control for rows that may not contain a single fiscal quarter value like our total rows.
 - Next up, we have CALCULATE which is evaluating customer sales in a modified filter context where visible date and our filter context is less than or equal to the max date in the calendar table.
 - And then we're looking at the fiscal quarter year.

So now we're saying if the visible date and the initial filter context equals the max period in our fiscal quarter year, then return that table.
