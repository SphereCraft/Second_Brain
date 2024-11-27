18/11/2024 1531

Status #idea

Tags:

# For Loops

A for loop in programming is used to repeatedly execute a block of code for a specific number of iterations or over a sequence of items (eg lists, ranges or strings).

Why use a for loop?

iterate over sequences like lists, strings or dictionaries 
Repeat a block of code for a fixed number of times
Easy to work with when the number of iterations is known in advance

This very common in [[AWS]] when need to run the same script many times.

# For loops

'# Define IDs'
instance_ids = ["i-123456abcde", "i2458hsftewa", "i-abcde67224445"]

for instance_id in instance_ids:
    print("checking status of instance {instance_id}")
    # Code to check instance status
    print(f"instance {instance_id} status check complete")

print("All instances have been checked")

[[While Loops]] can be used with this







# References
