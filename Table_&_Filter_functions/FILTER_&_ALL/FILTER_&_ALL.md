


![image](https://github.com/liubovkyry/DAX/assets/118057504/70a762cc-c025-4148-99d1-05e12fd9740e)

![image](https://github.com/liubovkyry/DAX/assets/118057504/6887342a-0c5a-47f8-9725-a5808a52eea6)

Both of these functions you should be pretty familiar with and filter is a function that we've used

with some regularity, and what it does is return a table based on one or more filter expressions.

A couple of key notes here to point out is that filter is actually both a table function and an iterator

function.

And because filter is an iterator function, it's important to keep in mind the number of rows that

you want when you're using filter.

So, for example, if you call a very large number of rows from a table, you could actually impede

the measure performance because now that filter function has to scan row by row by row throughout that

virtual table that's created.

So something to keep in mind there that could really impede your measure performance.

But filters also commonly used to reduce the number of rows to scan, because Filter also accepts different

filter arguments where you can reduce the number of rows that you want to bring back from that virtual

table.

Up next, we've got all and all is a function that returns all of the rows in a table or all of the

values in a column.

And it ignores or clears any initial filters similar to filter.
