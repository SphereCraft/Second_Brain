20/11/2024 2149

Status #idea

Tags:

# JavaScript for loops

// -----For loops-----

let regions = ["eu-west-1", "eu-east-1", "us-west-1", "us-east-1"];

for (let i = 0; i < regions.length; i++){
    console.log ("Deploying to region: " + regions[i]);
}


// -----Exercise-----
// -----Create a for loop for using cloud services-----
// -----EC2, S3, Lambda, DynamoDB-----

let cloudsServices = ["EC2", "S3", "Lambda","DynamoDB"];

for (let i = 0; i < cloudsServices.length; i++){
    console.log ("Using " + services[i] + " cloud service");
}

for loops are used to repeat a block of code a specific amount of times, useful in cloud engineering for completing multi tasks.

let regions declares an array of 4 regions
let i = 0 runs once at the start of the loop. In arrays 0 is the first one.
2nd part is the loop condition. regions. length is the number of elements in the array.
3rd part runs at the end of each loop iteration
i++ is the same as i = i + 1

The for loop should run 4 times, 1 for each index in the array. When the conditions is false it will stop.




# References
