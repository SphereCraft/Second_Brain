18/11/2024 1546

Status #idea

Tags:

# While Loops

These allow you to run a block of code for as long as a conditions is true.
These are useful to have something checked until a condition is met

'# while loops'

count = 0
while count < 5:
    print(f"count is : {count}")
    count +=1

So start the counter at 0 and while the counter is less than 5 it will print the current number until the condition is false.
Need to ensure the condition will be false at some point or this will create an infinite loop, which is something that we don't want.


***While Loops with EC2**

'# Simulate instance state'
import random
import time

def simulate_instance_state():
    states = ["pending", "pending", "pending", "running"]
    return random.choice(states)

instance_state = "pending"
attempts = 0

while instance_state != "running" and attempts <5:
    print(f"Attempt {attempts + 1}: instance_state is {instance_state}")
    instance_state = simulate_instance_state()
    attempts +=1
    time.sleep (1) # wait 1 seconds before next attempt 

if instance_state == "running":
    print("Instance is now running")
else:
    print("Instance did not start in time")
    
We initialise a variable and set to pending- instance_state and set a counter to 0. Having a while loop that keeps going while its not equal (!=) to running and while attempt is less than 5. If its true then the while loop will then change instance_state to be simulate and adds 1 to the attempts, waits 1 second before allowing the defined simulate_instance_state to choose a random state from the list. It will do this until either the while loops hit 5 attempts or until the condition is not equal to running, then it will run the [[if loop]] printing its running if while loop is false or did not start if runs out of attempts.






# References
