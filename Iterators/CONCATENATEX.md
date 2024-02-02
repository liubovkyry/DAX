![image](https://github.com/liubovkyry/DAX/assets/118057504/a3d1ad76-9e3c-4ad5-be16-04af3eeacd36)

![image](https://github.com/liubovkyry/DAX/assets/118057504/211dd914-3efa-4d6a-aa29-ba3ad464ebff)



![image](https://github.com/liubovkyry/DAX/assets/118057504/51fe91ed-61e0-4958-9225-5eccd39b06c6)

So here we have a slicer that contains product category and is filtered for coffee, coffee, beans

and drinking chocolate.

So based on this slicer selection, how could we dynamically display a label with this filter context?

Well, all we really need to do is create a measure that captures the individual values from the slicer

and then returns that output.

And we can do that using concatenate X.
So here we have a measure called selected product category that is showing the sales based on the selection

within the slicer.

And then we're using Concatenate X to output the selection of those values and it looks something like

this.

So here we can add this measure to a card which will then display the output of concatenate x, which

includes the filter context from our slicer.

And now we can add this around a visual so that our report consumers know exactly what the visual is

showing without needing to add the product category context directly within this matrix.

![image](https://github.com/liubovkyry/DAX/assets/118057504/85222f2a-be68-4757-8c3c-355b3de6dc87)

But we want to create a little bit more of an intuitive way for our report consumers to totally understand

that this visual is also being filtered by these three product categories.

So let's create a new measure.

![image](https://github.com/liubovkyry/DAX/assets/118057504/fb8b1f6d-f32a-4dcb-a923-8fdbf62a2967)


![image](https://github.com/liubovkyry/DAX/assets/118057504/84d2c64d-cc31-430d-8b74-5fd516142547)


So our first key objective here is to create a visual for store five that shows customer sales by store

and employee ID.

Let's add the matrix with store ID and our sales.

Let's filter this matrix.

Store ID equals five.

And now let's add in our employee ID, and this is the staff ID From our employee lookup.


2)

Number two is to create a measure to show percent of total sales for store five.

So here we'll create a new measure, and I'm going to call this percent of customer sales.

![image](https://github.com/liubovkyry/DAX/assets/118057504/a2e9dd01-caef-4f59-bc94-beca0e482f57)

3)


 Key objective number three is to use concatenate to define a measure that shows

the employee name or names selected and the percent of total sales for store five.




![image](https://github.com/liubovkyry/DAX/assets/118057504/ee55cc46-8be0-440d-88ab-9e5f1c2b904f)



And that's really what this whole third objective is about, is using Concatenate X to define a measure

that shows the employee names, plus the percentage of sales that they drove for store five.

And when we make a selection, we're clearly able to see that.

Or multiple selections.

We're able to see the employees listed out in that way, right?

But what's a little bit troubling is that when we deselect this, we have our entire list of employees

here and a lot of them don't work for store five.

So how can we handle this?


![image](https://github.com/liubovkyry/DAX/assets/118057504/83f711c6-f376-44a6-95df-9929cd018829)


Well, let's go and update the measure here and we can actually add in if has one value.



