![image](https://github.com/liubovkyry/DAX/assets/118057504/df712760-b9e3-4245-a654-7f3a7b958c9f)
And Keep filters is a function that does not remove an existing column or table filter from an individual

calculate statement.

What that means is that when you use keep filters as a calculate modifier, it will only evaluate the

filter selection that's also within the current filter context.

So we want to calculate some sort of measure in a filter context where we're keeping the filters that

equal some value, right?

But just keep in mind that the filter parameter or this expression within keep filters can actually

be any logical statement, physical table or table expression.

There are a couple of key things to highlight about keep filters.

First is that this function actually allows you to control which filters are specifically applied to

the calculation, meaning that if you change the initial filter context, then keep filters will update

accordingly.

Second, keep filters is a special kind of modifier where it's not actually modifying existing filters,

but rather it's adding new filter context.

So to kind of help visualize this, you can think of keep filters as performing an inner join between

the initial filter context and our reports or in our visuals and the filter context within the measure

to really drive this stuff home.
