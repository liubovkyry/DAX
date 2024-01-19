
![image](https://github.com/liubovkyry/DAX/assets/118057504/a9a99981-266c-4409-97e1-ed1d21ba7603)

The last two parameters here I've highlighted in red, and it's because they're not recommended to be

used, they're actually depreciated.

And the purpose of these parameters is that they were set up as a way to add additional columns to the

output of the summarized table, but they're actually not being supported or no longer being optimized

by current and future updates to the Vertipaq engine so their use isn't recommended.

If you're looking to add columns to the output of a table while you're using Summarize.

A better approach would be to use something like the Add columns function.

![image](https://github.com/liubovkyry/DAX/assets/118057504/0a902988-958f-4f18-8547-95114e00f01d)



They're being combined in a way that is showing all of the distinct or all of the unique combinations

of these two columns.


![image](https://github.com/liubovkyry/DAX/assets/118057504/3f901532-869a-465c-a253-8df5df8bb16a)


So what we're going to do here is create a new table and let's call this unsold pastries.

 We're going to start off with summarize.
And the table that we want to use is we actually want to create a calculated table.

So we're going to use FILTER.

And the base table for filter is the food lookup or the food inventory table.

And the expression that we want to evaluate is where the food quantity sold 

Does not equal the food baked or the food quantity Start of day.

![image](https://github.com/liubovkyry/DAX/assets/118057504/83543f43-22b3-4269-8dfb-305bd3730d99)





![image](https://github.com/liubovkyry/DAX/assets/118057504/912046d0-a35b-4745-a4dc-137e9e2040c5)


![image](https://github.com/liubovkyry/DAX/assets/118057504/88e7e075-7bc4-4f8d-8ab6-05671914677d)


![image](https://github.com/liubovkyry/DAX/assets/118057504/3e84c59d-ab59-407f-be5b-d1491e9bbaf2)


![image](https://github.com/liubovkyry/DAX/assets/118057504/76d2467c-da4b-49cc-a314-8f9436f37c1a)





