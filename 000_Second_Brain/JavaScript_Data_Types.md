20/11/2024 1942

Status #idea

Tags:

# JavaScript Data Types

// data types in javascript

let x = 5; // number
const y = 3.14; // number
var name = "Jeff" // string 
let isvalid = true // boolean

JavaScript is very important for [[Server-Less Architecture]], [[IaC]], Full stack development (all in one language), [[API]] development.

// Simple Lambda function 

exports.handler = async (event) => {
    console.log('Received event:', JSON.stringify(event, null, 2));

    const response = {
        statusCode: 200,
        body: JSON.stringify('Hello from Lambda'),
    };

    return response;
};


Deploying to the wrong region can have very bad results, costs, problems or even system failure. so having this clear and predictable scopes can help manage cloud configs. This will also help when working in teams and great for scalability.

// data types in javascript

let x = 5; // number
const y = 3.14; // number
var name = "Jeff" // string 
let isvalid = true // boolean

// 1. -----Numbers-----
const instanceCount = 5;
const cpuUtlization = 75.5;

console.log(typeof instanceCount); // outputs number
console.log(typeof cpuUtlization); // outputs number

// 2. -----Strings-----
const region = 'eu-west-1a';
const errorMessage = "Resource not found";
const logEntry = `Deployment failed in ${region}: ${errorMessage}`;

console.log(typeof region); //outputs: string 

// 3. -----Boolean-----
const isProduction = true;
const debugMode = false;

console.log(typeof isProduction); // outputs boolean

if(isProduction && !debugMode){
    console.log("Running in production mode");
}

// 4. -----Undefined-----
let configFile;
console.log(typeof configFile); // outputs Undefined 

if (configFile === undefined){
    confole.log ("configFile not loaded");
} // Load config file here

// 5. -----Null-----
const cacheResult = null;
console.log(typeof cacheResult); // Outputs object

if (cacheResult === null){
    console.log ("No data in cache,fetching from database");
    // fetch data from database
}

// 6. -----Object Literals-----
const ec2Instance = {
    instanceId: '123456789abcdefg0',
    type: 't2.micro',
    state: 'runnning',
    launchTime: new Date('2023-09-15T10:00:00Z')
}

console.log (typeof ec2Instance); // Outputs: object
console.log (ec2Instance.type); // Outputs: t2.micro

// 7. -----Arrays-----
const availabilityZones = ('eu-west-1a', 'eu-west-1b', 'eu-west-1c');
console.log (typeof availabilityZones); // Outputs: object
console.log (Array.isArray(availabilityZones)); // Outputs: true

availabilityZones.forEach(zone => {
    console.log (`Deploying to ${zone}`);
});

Understanding these core data types is fundamental. Each type has a specific used case, when used correctly can lead to better readable code.
Always use the correct type for the right situation.






# References
