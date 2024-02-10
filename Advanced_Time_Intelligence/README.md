![image](https://github.com/liubovkyry/DAX/assets/118057504/b80df3de-900a-4c77-8a14-8e99d3bd4626)


![image](https://github.com/liubovkyry/DAX/assets/118057504/50e6ea06-a3b1-41a0-90d9-c06baaa1bff9)


One of the features in Power BI is by default, it automatically creates a hidden date table for every date or date time column that's present on the one side of the relationship in a data model.

And one thing to note here if you only import a single table like the sales by store table, a date table will be automatically generated for this because it's the only table that exists.

This would also be the case if you imported multiple tables and didn't define a relationship between them.

So, for example, let's say you import an inventory table that contains stock date, build date, order date and ship date. Power BI would actually create four hidden date tables.


### What exactly is included in these hidden date tables?

Well, all these auto generated date tables will include a contiguous date range through the end of the year that's represented in your table that you've imported.

And this is regardless of the actual date range within that table.

So if you import a table that only has dates from March 1st, 2020 through August 31st, 2020, the automatic date table will contain every date for 2020.



#### Why would power BI do something like this if it can potentially impact performance and bloat model size?

![image](https://github.com/liubovkyry/DAX/assets/118057504/69c98156-ba3e-4270-b973-ef7250a85b0e)




    
![image](https://github.com/liubovkyry/DAX/assets/118057504/f32c416a-bb0a-41ed-9edb-5787b183b6ff)


One thing to note here is these requirements that we're going to walk through will apply to the table,

whether it's imported, created in the query editor or with Dax.


First, it must contain all of the days for all of the years that are represented in your fact tables.

If the data in your fact table starts on May 1st, 2019, and runs until September 30th, 2020, then your calendar table must represent all of these dates to.

The main reason for this is because most of the time intelligence functions require a contiguous set of dates to work properly.


Second, the table must have at least one field that is set as a date or a date time data type some calendars, use a date key. That's typically an integer value.

So if you're using a calendar where the table has a primary key, that's an integer. You're going to want to set the date column as a date data type.


Third, and we've talked about this a little bit, but the date table needs to contain all the dates, but it must also not contain duplicate dates.

If duplicate dates are included, the date column would no longer be considered a unique list and by definition would no longer be a primary key.

In that case, it would most likely be considered a fact table. So make sure that your date column only contains unique values.


Fourth. If you're using a time component with the date column, the time component must be identical for all of the rows contained within that column.

So something like 12 p.m. or 12 a.m., something like that.

And if you import a calendar table that contains a date column containing both date and unique times, you need to split the time component out into a separate column.


Fifth, the <b>date table</b> and more specifically the date column should be marked as the date table within your model.

This isn't strictly required, but it's really a best practice and something that you should probably get in the habit of doing.



And again, just to reiterate this point, if time is present in your date field, you must split the time component into a different column.

This way you'll be able to keep the time component within your date table while adhering to all of the previous requirements.
