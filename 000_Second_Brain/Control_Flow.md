18/11/2024 1405

Status #idea

Tags:

# Control Flow

'# Control Structures/Control Flow'

'# If Statements

'# if condition:
    # code to execute if condition is true
'# elif another_condition:
    # code to execute if another_condition is true
'# else:
    # code to execute if false'

In AWS and Cloud engineering these structures are crucial for managing [[API]] responses, resources and handling cloud responses. This statement allows your code to make decisions based on certain conditions. Useful if need certain things need to be done based on certain conditions are met.
If the condition is true the indented line of code directly below will be executed, if not then will move to the next line, in this example we then have an elif which allows for another condition, if that's true will do the same, if false will move on to the last line of code in this example. Can have many different elif statements if there are many conditions that need to be met.

instance_running = "broken"

if instance_running == "running":
    print("The EC2 is running")
elif instance_running == "stopped":
    print("The EC2 has stopped....")
else:
    print("The EC2 Instance is in an unexpected state")

Keep code blocks as small as possible and optimise as much a possible.








# References
