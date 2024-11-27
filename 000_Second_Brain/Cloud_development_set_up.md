15/08/2024 0645

Status #idea

Tags:

# Cloud development set up

# 🚀 WindowOS Setup

##### [Week 1 - Cloud Fundamentals](https://cloudengineeracademy.mykajabi.com/products/cloud-academy-tech-with-soleyman/categories/2154193244)

Setting up a Windows machine for cloud development involves installing tools and software that will enable you to code, build, test, and deploy applications. Below is a guide to get you started, including package managers, code editors, and other essential tools.

### 1. Setting Up a Package Manager

#### Installing Chocolatey

1. ****Open PowerShell as Administrator****:
    
    - Right-click the Start button, select "Windows PowerShell (Admin)" or "Terminal (Admin)."
        
2. ****Install Chocolatey****: Copy and paste the following command into PowerShell and press Enter `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`
    

### 2. Installing Development Tools

#### Install Visual Studio Code

- ****Using Chocolatey****:
    
    - In the same PowerShell window (as admin), run:
        
        `choco install vscode`
        

#### Install Git

- ****Via Chocolatey****:
    
    `choco install git`
    

#### Install Node.js (for JavaScript development)

- ****Via Chocolatey****:
    
    `choco install nodejs`
    

# 🚀 MacOS Setup

##### [Week 1 - Cloud Fundamentals](https://cloudengineeracademy.mykajabi.com/products/cloud-academy-tech-with-soleyman/categories/2154193244)

If you're new to macOS, it's important to know that when you download an application file, you must drag it to the Applications folder. This is especially important for text editors that you may need to write code in.

You'll also be installing a lot of things using the terminal. It may feel like you're a hacker, but there are two important points to keep in mind:

1. When using the terminal, "no news is good news." This means that you usually only receive feedback when something goes wrong. Success messages are nice, but don't expect them at the command line.

2. When installing things in the terminal, a lot of text appears. It's important to pay attention to this text because if something goes wrong, useful error messages will be displayed for you to copy and paste when seeking help. Additionally, further instructions may appear, which you'll need to follow.

Please work through these in order and make sure each step is successful before progressing to a subsequent step:

1. Xcode Command Line Tools
    
2. Home Brew Package Manager
    
3. Visual Studio Code
# References
