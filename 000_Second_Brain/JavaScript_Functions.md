21/11/2024 0724

Status #idea

Tags:

# JavaScript Functions

// -----Basic Functions-----
function sayHello(){
    console.log("Hello, Cloud Engineer");
}

// -----Calling the Function-----
sayHello();

//-----Function Parameters-----
function deployToRegion(region){
    console.log("Deploy to region: " + region);
}

// -----Calling function with Parameters-----
deployToRegion("us-west-2");

// -----Exercise-----
function configureService(serviceName, tier){
    console.log ("Configuring: " + serviceName + " at tier " + tier);
}

configureService("EC2", "t2. micro");
configureService("S3", "standard");

Basic function defines the function saying Hello
Can then call the function by just copying the name of it
Can then add parameters added in the ()
But these parameters need to be defined when calling the function

then was an exercise to do the same but with 2 parameters

functionName configureService
2 parameters serviceName and tier
inside the function console.log with both parameters
call the function with different parameters.



# References
