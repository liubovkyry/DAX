![image](https://github.com/liubovkyry/DAX/assets/118057504/8b4218b2-f0ef-4c48-836c-45814da5992f)

![image](https://github.com/liubovkyry/DAX/assets/118057504/640519dd-fef6-4c24-b068-dd948fa9ac9c)

We know that we're going to need to do some sort of filtering to understand the customers that had signed

up for our loyalty card in January of 2017.

But we can't create some sort of virtual or calculated table first.

What we actually have to do is reference our customer lookup table first.

It physically exists within our data model.

From here we can kind of do whatever we want.

So what I'd like to do is use two functions together to be able to filter this, right?

So I want to use FILTER and then VALUES, and I want to use VALUES because I actually want to return

the same number of columns right Deduplicated from the table.

Right.

So good use of the values function here.

Close this out in the filter expression that I want to use is from the customer lookup table.

We have this customer since field and this is the date that our customer had signed up for the loyalty

card.
