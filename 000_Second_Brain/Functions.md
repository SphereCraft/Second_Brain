19/11/2024 0645

Status #idea

Tags:

# Functions

In python a function is a reusable block of code to preform a specific task. Very important in cloud computing as they allow you to organise  your code into usable and manageable blocks, they make code easier to read and debug.
Basic structure of a function
	def function_name (parameter, parameter2, parameter3)
def - keyword telling python we are defining a function. Then the name that we give to that function, should be descriptive enough to understand what the function will do. Then inside () they are optional or what the function will accept. The : marks the end of the function header and the start of the body. The body is the indented line of code. Finally return result, this is optional, if not there it will return none.

Import random - This will import the random module from [[Python]]'s standard library. This will generate random numbers which we will use to generate a unique bucket name.
Should always put the imports at the top of the file

'# create a random bucket name'

import random

def generate_bucket_name(project_name):
    random_suffix = random.randint(1000, 9999)
    bucket_name = f"{project_name}-bucket-{random_suffix}"
    return bucket_name

'# Using the function to display the random bucket name'
new_bucket = generate_bucket_name("myproject")
print(f"Created new S3 Bucket name: {new_bucket}")

generate_bucket_name is the name of the function. project_name is the variable that will be used within the function.
Function body
random_suffix line will generate a random number between the 2 specified numbers. random_suffix is the variable that will store the outcome of the line.
Final line will print the outcome






# References
