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
