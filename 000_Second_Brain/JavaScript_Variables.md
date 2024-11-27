20/11/2024 1945

Status #idea

Tags:

# JavaScript Variables

// Variables, let and const

function deployResources(isProduction){
    let region = 'eu-west-1'; //Default region for development

    if(isProduction) {
        let region = 'eu-west-2'; // Region for production 
        console.log(`Deploying production resources in ${region}`);
        // Deploy production-specific resources here
    }

    console.log(`setting up monitoring in ${region}`);
    // set up monitoring here
}


deployResources(true);  // Deploy for production
deployResources(false); // Deploy for development

Const is not meant to be reassigned, it also creates a block scope too

// Variables const
const API_ENDPOINT = 'https://api.mycloud.com/v1';
console.log(API_ENDPOINT); // outputs https//api.mycloud.com/v1

// API_ENDPOINT = 'https://api.mycloud.com/v2'; // This would throw an error 

//-----Configuration Management-----
const AWS_REGION = 'eu-west-2';
const MAX_RETRIES = 3;
const DYNAMODB_TABLE = 'users';

function fetchUserData (userID){
    // use these constants in your AWS SDK calls
}

//-----Security-----
const API_KEY = process.env.API_KEY;
API_KEY = 'new_key'; // This would throw an error, preventing accidental exposure

//-----Preventing Bugs -----
const LAMBDA_TIMEOUT_NS = 3000;

function configureLambda(functionName){
    LAMBDA_TIMEOUT_NS = 5000; // Error!
        // Configure Lambda function with the timeout 
}



# References
