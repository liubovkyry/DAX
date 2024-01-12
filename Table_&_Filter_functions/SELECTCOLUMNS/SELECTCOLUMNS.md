

![image](https://github.com/liubovkyry/DAX/assets/118057504/6f040550-a996-4a6b-bc22-3ee7d2c7b05c)
Now select columns returns a table with selected columns from that table, plus any new columns specified

by the Dax expression and looking at the parameters of the function here.

First up, we have the table, and the table input allows us to specify any Dax expression that returns

a table, either physical like sales by store or food inventory or virtual table like a distilled version

of the employees table, like we see here with the filter for employees in a certain set of numbers.

The second expression is a parameter that is repeatable, and this is the name of the new column to

be added.

This must be written as a string and be double wrapped in quotes.

So some examples here could be something like employee name and ID or employee full name or store name

or something like that.

Last up the expression.

And this parameter is also repeatable.

It's paired with the name and it's an expression that returns a scalar value like a column reference,

integer or string.

So some examples here could be something like employee ID or the concatenation of an employee's first

name and their last name.
