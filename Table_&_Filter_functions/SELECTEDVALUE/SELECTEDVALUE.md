
![image](https://github.com/liubovkyry/DAX/assets/118057504/27253bbf-3ada-4fa0-bd2c-1f37b351709a)


So in other words, what this function does is it only returns a single value when the column that's

being referenced can be filtered down to one unique value.

So looking at the parameters of this function, we first have the column name that we want to return

a single value from, and some examples of this may be the first name of your customers or a specific

product.

Additionally, you have the option to specify an alternate result when there is no value or more than

one value in the specified column.

If the alternate result is omitted and the column can't be filtered to one unique value, then a blank

will be returned by default.

So some examples here of alternate results could be something like using a dash or writing Na for not

applicable.

Let's take a look at a quick example here.

And here we have a matrix with product groups and product names, and the values we're looking at are

customer sales, quantity sold using selected value and retail price, using selected value and looking

at the product group rows.

So the bolded rows, you can see that there isn't a value for the quantity sold or the retail price.

See, those values are missing here.

And the reason why these blanks are showing up is because this expression doesn't evaluate to a single

unique result.

Right?

And that's why nothing is returned.

So in this case, if we look at the add on product group, we have caramel syrup, chocolate syrup,

hazelnut syrup and our sugar free vanilla syrup products below in that group, each one of those has

a unique retail price.

So that's why for each of those rows, we're actually returning values because the product can be filtered

down to a single unique value based on the filter context of the matrix before we head over to Power

BI and actually check this function out, it may be helpful to think of selected value using a slightly

different term.

![image](https://github.com/liubovkyry/DAX/assets/118057504/bec1f88a-b6ab-4e54-9025-cf0145dc8e82)

![image](https://github.com/liubovkyry/DAX/assets/118057504/bfdb8591-3da6-4728-8881-51dc5401ca84)

So what the selected values function is doing is it's saying that based on the current filter context.

So our current filter context here is for Beverages.


Well, there isn't a current retail price at the product group level for Beverages.

It can't evaluate to a unique value, so it doesn't return anything.

But when we drill down.

These all can evaluate to a single retail price.

![image](https://github.com/liubovkyry/DAX/assets/118057504/25bb580c-5518-42d6-b48e-69e4c65ba6d1)



