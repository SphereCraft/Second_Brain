14/08/2024 0657

Status #idea

Tags:

# DNS

**DNS – Domain name system**

**What is a DNS**

it converts web addresses like [www.google.com](http://www.google.com/) to numerical IP addresses. It allows users to find specific data using easy to remember address instead of trying to remember complex number addresses.

**DNS query process**

When a user enters a web address, a DNS query is initiated, next a DNS recursive resolver then moves to a root [[server]]. The query is moved to a Top-Level domain (TLD) [[server]] (eg .com, .net, .io). Then to the authoritative [[server]] which will send the corresponding IP address back to the resolver, which then delivers it to the user

Amazon [[route 53]]

Your public IP address is assigned by your internet service provider (ISP) and is used for communicating with websites and services online.

****Windows:****

1. ****Open Command Prompt:****
    
    - Press `Windows key + R`, type `cmd`, and press `Enter`.
        
2. ****Use**** `**ipconfig**`****:****
    
    - In the Command Prompt, type `ipconfig` and press `Enter`.
        
    - Look for the `IPv4 Address` under your network adapter. This is your private IP address.
        

****Linux/macOS:****

1. ****Open Terminal:****
    
    - On Linux, you can usually find the Terminal in your applications menu.
        
    - On macOS, open Spotlight search (`Cmd + Space`), type `Terminal`, and press `Enter`.
        
2. ****Use**** `**curl**` ****to fetch your public IP:****
    
    - Type `curl ifconfig.me` and press `Enter`.
        
    - The response is your public IP address. This command works by sending a request to `ifconfig.me`, a web service that returns the public IP address of the incoming request
        
3. ****Private IP:****
    
    - Type ipconfig getifaddr en0
        

Cloud operation system manage how everything works together like CPU’s, mkemory, storage and software. They also faciliate a wide range of cloud services ranging from storage, processing, analytics and machine learning

Windows [[server]] is known for its user interface, applicatiom compatibility and support structures and works in harmoney with microsoft Azure and is designed for hybrid cloud architectures for on prem infrastructure linking with Azure

Linux distros like Ubuntu, CentOS and red hat are common in cloud enviroments. They offer user friendliness, stability and commercial support. The open source nature of these distros allows for community driven development, with greater customization and flexibility and alos cost effective due to no licensing fee. They are great for there stable and efficient, especially in high demand cloud workloads. Robust security in **SELinux** and **AppArmor,** for tight security enforcement and application level security

with this knowledge you can make informed decisions regarding cloud OS selection and management, tailoring your choices to best suit your cloud-based operations and objectives.
# References
