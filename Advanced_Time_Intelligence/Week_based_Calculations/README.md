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
