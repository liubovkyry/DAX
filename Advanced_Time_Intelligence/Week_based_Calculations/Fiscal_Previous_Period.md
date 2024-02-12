![image](https://github.com/liubovkyry/DAX/assets/118057504/0d22b8ff-6287-442c-93a5-e3c952a46422)

First, I'm using a variable here to define the entire measure, and we kick it off with CALCULATE.

And the expression that we're calculating in this example is customer sales, and customer sales is being calculated in a modified filter context, where we start off by clearing ALL of the filters from

our fiscal calendar table, and then we're returning a table that's filtered based on a logical expression.
