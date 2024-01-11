![image](https://github.com/liubovkyry/DAX/assets/118057504/00fdc082-6a93-4c81-b563-d067e879a2cf)
It removes all report context filters in the table, except the filters applied to the specified columns

in the query.

So another way to think about this function is to say that it removes filters from a table, except

for columns that we specifically ask it not to remove filters from.

So basically all except can access other columns within the expanded version of that base table.

![image](https://github.com/liubovkyry/DAX/assets/118057504/5ac7096d-b62f-4aaf-8762-0cc06df9bfa6)

Here we have a measure and we want to evaluate customer sales in a modified filter context.

And to do that, we're using all except as a calculate modifier to remove the initial filter context

from the sales buy store table except for filters on transaction date and sales outlet ID.

And while the transaction date and sales outlet ID columns don't physically live in the sales buy store

table, we can access them because they're on the one side of the relationship and therefore they're

part of the expanded table, the expanded version of sales based on this measure.
