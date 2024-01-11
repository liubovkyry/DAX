
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
