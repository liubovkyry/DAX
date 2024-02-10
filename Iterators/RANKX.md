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

