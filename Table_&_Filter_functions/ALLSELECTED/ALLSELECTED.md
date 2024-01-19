![image](https://github.com/liubovkyry/DAX/assets/118057504/4d88f867-dc7e-4df3-8437-f8875e660c2d)

All selected respects existing filter context except for row and column filters within a visual.



And oftentimes this function can be used to obtain visual totals or subtotals within a query.


One other thing here is that behind the scenes, all selected is actually a pretty complicated function

and it hides some hidden features and there's a lot going on there.


But we are going to focus on how we can use all selected to

return totals based on filter selection made within a report.

![image](https://github.com/liubovkyry/DAX/assets/118057504/83a55f3d-2695-4406-91f2-690bd962ec05)

But what's happening here is that all selected is ignoring any other row or column filter context from

within the visual.

And that's why this function is commonly used to obtain visual totals or subtotals in a query.

![image](https://github.com/liubovkyry/DAX/assets/118057504/50e863f4-ba8c-41ef-8d4b-624dc344c3f8)


But let's go ahead and add in a slicer that contains our product groups here.

When we make a selection, beverages and food, you can see that the total is now updating based on

that selection.


So this is what that portion of the all selected definition means, where it ignores any of the filters

from the initial context of the visual.

The row filter, or if you had any sort of column filter here and it takes into account external filter

context.

So in our case, the slicer is updating that filter context when we make new selections.

Additionally, the date filter when we select that will also influence this all selected total.

![image](https://github.com/liubovkyry/DAX/assets/118057504/4a9c047d-8ea4-49e7-91c9-3a08ceafa1da)

1)  So our first key objective is to create two measures one for total baked and one for total sold.

![image](https://github.com/liubovkyry/DAX/assets/118057504/5be91255-1de7-43ed-8f86-56ab5a0dc155)

![image](https://github.com/liubovkyry/DAX/assets/118057504/8f54e226-6dd4-4fc3-81d2-c2177d0e5bff)

2) So up next, key objective two is we need to create measures for percent of total baked and percent

of total sold.

That total 100% based on a slicer selection of product type.

![image](https://github.com/liubovkyry/DAX/assets/118057504/ba797aec-1d55-4943-a9b6-91552b5c607f)
![image](https://github.com/liubovkyry/DAX/assets/118057504/920ad725-925d-4796-9e18-3d59d8ca9667)

3) Our third key objective is to now build a visual to compare the percent of all baked to the percent

of Total Baked and then answer the question Which food item is baked the most for store eight?

And now we need to compare the percent of all baked to the percent of total baked.

We want to remove any filter context here so we could use one of two functions.

We could use REMOVEFILTERS or ALL.

In this case, I like using the REMOVEFILTERS.

Let's calculate modifier.

It tells you exactly what it's doing and we want to remove filters from food inventory.

![image](https://github.com/liubovkyry/DAX/assets/118057504/34c4b51d-6b5a-4044-a38b-ec40223e1d3c)

![image](https://github.com/liubovkyry/DAX/assets/118057504/3d0dac84-3896-46f9-bd92-ee9324eb3190)
