15/08/2024 0643

Status #idea

Tags:

# Ping

### Testing Network Connectivity with `ping`

****Objective:**** Verify the ability to reach a specific domain or IP address.

1. ****Run**** `**ping**`****:****
    
    - Type `ping -c 4 example.com` on Linux/macOS or `ping example.com` on Windows.
        
    - Review the output for packet loss and round-trip times.
        

****Learning Outcome:**** `ping` helps verify connectivity to a networked device, showcasing how data packets travel to and from a destination, thus ensuring the network path is operational.

To ping in the lesson example,
Copy all the relevant IP addresses from the dashboard
Private
App1 and App2
Public for bastion

Ping from App2 to App1
Terminal, get to directory where bastion.pem is
ssh -i bastion.pem ec2-user@bastion IP
this will log into the bastion server
ssh -i bastion.pem ec2-user@App1 IP
This should log into App1
ping (App2 IP)
Should now see a response from App2


# References
