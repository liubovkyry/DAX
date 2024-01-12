

![image](https://github.com/liubovkyry/DAX/assets/118057504/d38a34ca-544d-409e-ae9b-75aed369d7f3)

So one way that I like to think about this is that select columns lets you select only the specific

columns you want to retrieve, while Add columns lets you add additional columns to a table.

![image](https://github.com/liubovkyry/DAX/assets/118057504/c5b9253f-490b-44e9-92a5-59d9d0406dd0)

And what I'd like to actually do is let's just change out this function for Add columns.

And we'll rename the function here, add columns, demo and looking at this, the inputs are the exact

same.

![image](https://github.com/liubovkyry/DAX/assets/118057504/812a7b25-fdb2-43d4-84bf-bea0c438e33c)

So now we're actually returning the entire filter table here.

We're looking for all of the columns of the employee lookup table where staff ID equals either six,

16 or 31.

And then we're adding on these two additional columns, employee ID, which is here, which is looking

at the staff ID column and then manager name and store.

So that same use case that we used for select columns, but in this case, because we already have staff

ID here, this employee ID column is redundant.
