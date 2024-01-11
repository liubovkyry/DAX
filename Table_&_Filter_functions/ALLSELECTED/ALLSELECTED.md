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
