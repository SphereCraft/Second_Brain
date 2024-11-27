18/11/2024 0911

Status #idea

Tags:

# Python

Python is a high level language, known for it simplicity to read. Its like reading English.
In the Cloud world, which we will focus on, its excellent for IaC.
First must make sure you have [Install Python] on you system.

The first thing we all do is write our first program.
Create a file called hello_world.py - by adding the .py will automatically make the file a python file. Then code like this

print("Hello, World!") - i tested both quotes ie "" or '' and they both work.
any text/numbers in quotes is called a string.
To run the file, in linux, go to terminal and type
python file name
This should display Hello, World!
Keep quotes constant.
Python uses indentation to define code blocks

if True:
    print("This is indented")
    print("This is also in the if block")
    print("This is the third line in the if block")
print("This is not indented, so it's outside the if block")
print("This is a second line not indented, so it's also outside the if block")

**Comments**
These are to explain the code. This is ignored by the program and are just for reference. ie
'# This will print what I'm doing'

print("I am learning python for Cloud Engineering")

"""
some things why python is good for cloud engineering
Versatile and simplistic, Extensive Eco system,
Automation and scripting, Integration capabilities,
support for cloud-native development and 
community and support
"""
**Variables**
These are containers for storing data values. python is dynamically typed, which means you don't need to declare the type of variable, but you could as way of producing an error while coding. The type is inferred on the value that's assigned to it
So if my_name = 'Jeff' it will know its a string and if my_age = 50 it knows its an integer. They must start with a letter or underscore and are case sensitive and cannot contain python keywords like if, for, while etc.
instance_name - 'web_server' - this is a [[string]]
instance_count = 4 - this is an [[integer]]
is_running = True - this is a [[Boolean]]

Adding string together is called [[String Concatenation]]

[[Lists]] in python are very important in cloud engineering for managing resources etc







# References
