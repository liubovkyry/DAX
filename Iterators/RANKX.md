![image](https://github.com/liubovkyry/DAX/assets/118057504/b857d618-22eb-495c-9343-ce1018dc66ba)


```
Rank of Customer Sales (RANKX) = 
RANKX(
    ALL(
        'Product Lookup'[product_category]
    ),
    [Customer Sales]
)
```

![image](https://github.com/liubovkyry/DAX/assets/118057504/e163c396-2b1b-4be5-9f1f-441fe3202a41)

And we have this 1 hanging out here and our Totals.

So what we can actually do is head back into this measure and we'll add an IF and HASONEVALUE.

And we want to reference the product category column, the result of true.

```
Rank of Customer Sales (RANKX) = 
IF(
    HASONEVALUE('Product Lookup'[product_category]),
        RANKX(
    ALL(
        'Product Lookup'[product_category]
    ),
    [Customer Sales]
        )
    )
```

![image](https://github.com/liubovkyry/DAX/assets/118057504/e9e1d98f-ad98-4896-9138-efc3e6fb102b)

### Let's actually take a look at how we handle ties


And the first thing that I want to do is create a new measure called Rounded customer sales.

And what I want to use is the multiple round right - MROUND. The number that I want to round is my customer sales measure.

And the multiple I want to use here is 100,000.

```
Rounded Customer Sales (RANKX) = 
MROUND(
    [Customer Sales],
    100000
)
```

![image](https://github.com/liubovkyry/DAX/assets/118057504/29a6a097-19a5-4af1-9aa4-1baee92c9b0a)

So you can see here by using MROUND,  we're rounding either up or down to the nearest 100,000.

```
Rank of Rounded Customer Sales (RANKX) = 
IF(
    HASONEVALUE('Product Lookup'[product_category]),
        RANKX(
    ALL('Product Lookup'[product_category]),
    [Rounded Customer Sales (RANKX)],
    ,DESC
    ,Dense
        )
    )
```

![image](https://github.com/liubovkyry/DAX/assets/118057504/ce3a0369-da32-456c-aa92-23543d83f51d)




![image](https://github.com/liubovkyry/DAX/assets/118057504/933947ca-93c7-4fde-94e4-26227123d4a7)


```
Top 5 products by profit (rankx) = 
VAR ProfitRank = 
IF(
    HASONEVALUE(
    'Product Lookup'[product_category]
    ),
    RANKX(
        ALL(
            'Product Lookup'[product]
        ),
        [Customer Sales] - [Cost]
    )
    )
VAR Top5products = 
IF(
    ProfitRank <= 5, 
[Profit]
)
RETURN Top5products
```


1) So our first key objective here is that we need to use variables and rank X to create a single measure for our top five products.

    So we're going to create a top five products measure.

   We need to create variables here.

 - So the first variable that I want to create is the profit rank.

That's going to be the first input to determining the top five as we first need to determine the total profit rank for all of the rows within the table.

So I'm going to use the IF and  HASONEVALUE functions first and we want to look at this at the product category, right?

I want to say if my product category has one value, that's because ultimately that's what we're going to be filtering By then.

I'm going to return the rank of the product column.

We'll do product category here.

And now I can add in my RANKX function similar to the demo we're going to use all here and we want to clear ALL the filters from Product lookup - product.

And now the expression that we want to evaluate is we're looking for profit, right?

So we could do profit or customer sales minus cost, you know, either way.

So let's do customer sales minus cost.
 
 -  The next variable that we want to create is where we want to define the top five products.

And for this we can use a pretty straightforward, logical statement.

So we can use IF and what we want to say here is If the profit rank Is less than or equal to five, then we want to return  profit.  Otherwise, nothing.


 2) Our second key objective is to create a slicer for product category to be able to analyze the top five

products across different categories.

![image](https://github.com/liubovkyry/DAX/assets/118057504/a00c419f-3c08-4ff2-8380-e616f11860fa)

