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
