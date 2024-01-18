## Introduction

Calculate is a super powerful Dax function and arguably the most important Dax function.

And it's commonly used to modify filter context.
Now, some common use cases for calculate include things like simplifying measures by adding new filter
contexts that would normally use or would normally require multiple nested functions commonly used to
modify filter context to override preexisting filters using calculate modifiers like all keep filters
and remove filters and creating calculated inputs for other measures like the percent of total or percent
of category and other examples like that.

## Expanded Tables
![image](https://github.com/liubovkyry/DAX/assets/118057504/58081ba3-ed0c-4ae4-beec-21bd63216764)

![image](https://github.com/liubovkyry/DAX/assets/118057504/c4af0237-e66d-4bf4-aa1e-53a30f3abbdc)

![image](https://github.com/liubovkyry/DAX/assets/118057504/8f213e1f-9146-4cc9-81b6-ab229c1703c1)


When we talk about filters flowing downstream from the lookup table to the fact table or

filters propagating through the model, this is what we mean when that filter is applied to a column.

The entire expanded table is also filtered based on that criteria.

## Context Transition

![image](https://github.com/liubovkyry/DAX/assets/118057504/c09b9743-b937-4659-b714-15ca2381789d)

![image](https://github.com/liubovkyry/DAX/assets/118057504/02d36f97-9965-4818-acfe-fe52ddf3dd10)

As a measure, what the Dax engines are actually doing is automatically evaluating that expression

as it calculate and a sum as I'm showing below here in the code, the engine is basically saying, I

know that I need to create a filter context here to produce the right numbers.

## Evaluation Order

![image](https://github.com/liubovkyry/DAX/assets/118057504/a2cac943-9789-4c3c-912d-218f1d164082)
## CALCULATE modifiers
![image](https://github.com/liubovkyry/DAX/assets/118057504/bf17cd64-ce6c-47c9-8ed0-dc8ff77c750c)

## REMOVEFILTERS (See dedicated file)
## KEEPFILTERS (See dedicated file)
## TASK
## PROTIP
