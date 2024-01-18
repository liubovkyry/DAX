
![image](https://github.com/liubovkyry/DAX/assets/118057504/754b0cea-4f56-4b56-910c-384f9582283f)



At the top, we  have a blank row with $49,949 worth of sales associated with that.
When encounter this type of error, the VALUES function might be useful

![image](https://github.com/liubovkyry/DAX/assets/118057504/ef123918-e128-4e2f-8dc8-dbe17f4c2bdd)

![image](https://github.com/liubovkyry/DAX/assets/118057504/b1c42a40-07d7-49e9-8e1e-2cc98eb25739)


This is the first time we've seen anything like this in a Dax function that's referred to plus a blank

row or alluding to any sort of blank row.

So I think we need to investigate a little bit further about what that actually means.

Let's talk about values versus distinct specific considering the blank row.
![image](https://github.com/liubovkyry/DAX/assets/118057504/b3cfc48e-daa8-459b-a0d5-8c50e5948b4e)
Here we have a product lookup table and in our example here we have a product table that contains three

product IDs, 12, 13 and 14.

And this lookup table is tied to our sales by store table by a one to many relationship.

They're connected on product ID, but if we look at our fact table here, our sales by store table,

you'll notice something interesting.

It actually includes product IDs, 15 and 16, our sales by store table.

Our fact table actually contains additional product IDs that aren't included in the product lookup.

So what does this mean in situations like this instead of your Dax code returning an error when there's

a missing value from the lookup table?

What's actually happening is the Dax engines add in a blank row on the product lookup table or more

broadly, the Dax engine is actually adding in a blank row for any table on the one side of a relationship

to account for these types of situations.

You'll actually see this happen in your visuals when they contain some sort of missing value.

And like we've seen, values and distinct are pretty similar functions and returns similar results for

columns and slightly different results for tables.

But now we're actually getting to their biggest difference, which is how they handle the presence of

a blank row.

In a data model, values will always show the blank row, but distinct will not.

### Quick pro tip here 

If you think you might have a missing value in your lookup table or you're not sure,

you could always use values to check.


![image](https://github.com/liubovkyry/DAX/assets/118057504/70f04099-4fa7-4d3b-8348-0937ca07bf70)

   1) First objective, we need to check if the ginger scone product actually exists in the data model.

So for that, let's head over to our data view and I want to look at the product table and filter products.

   2) Second objective we need to use counting functions plus distinct and values to create a view that shows

the blank row.

```
Count of Product ID (DISTINCT) = 
COUNTROWS(
    DISTINCT(
        'Product Lookup'[product_id]
    )
)

Count of Product ID (VALUES) = 
COUNTROWS(
    VALUES(
        'Product Lookup'[product_id]
    )
)

```

If put two measures in a matrix You will see a little bit of a different view here where we have 87 total and we now have a blank product

row at the top here. (Compared with Distinct formula)

So that's our key objective.

Number two is using those counting functions plus distinct and values to create a view that shows the

blank row.

   3) The third thing is we need to create a new visual to show the missing product ID when the blank product

is selected.
