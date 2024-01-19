

![image](https://github.com/liubovkyry/DAX/assets/118057504/7596fcc5-9aeb-4120-91a3-a885b52df19f)


![image](https://github.com/liubovkyry/DAX/assets/118057504/187ba1d2-3576-46a6-8e40-36ae9237b1ec)

Let's look at the parameters of data table.

First, we have the name of the column that we want to return, which is wrapped in double quotes because

this needs to be a string type and this name is then directly followed by the type, and this type is

the data type for the column that you just specified using the name.

So what you're doing here is you're saying, I'm going to create a column called something like Test

number or value, and then the data type of that column is either a string, a double int or currency.

There are some other options.

And this is where following the power by IntelliSense will give you the full list of options available

here for these data types.

If you're creating multiple columns or you want to create multiple columns within your table, then

you'll repeat these name and type pairs until you've exhausted the total list of column names that you

want to add in.
And once you have that, you can then enter your data points to the table.

And these data points are called and separated with curly brackets.

And in our example, we'll get into exactly how this is set up.

But just be aware that you're using curly brackets to define the whole table and then the parameters

of the columns within that table.

One last really important note here is that data table can only accept fixed data inputs.

It does not allow for any sort of table or column references or expressions or any sort of calculations,

even some very, very simple mathematical operation, like two minus one.

![image](https://github.com/liubovkyry/DAX/assets/118057504/4b295848-3e2c-4b37-bcaa-00829d79ec61)

