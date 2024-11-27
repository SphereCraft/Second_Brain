11/11/2024 1935

Status #idea

Tags:

# Create GitHub Action

To create a github action, first need to create a repository - this example we call it github_actions_workflow. check the box to add the README.md file and make it public (doesn't matter). 
Clone the repo.
In VSCode create new folder for the repo, in that folder (in terminal) run
	git clone paste in the copied ssh from the repo
In the now newly made folder create another folder called .github/workflow (all workflows must be in this folder to work), and then create a file called main.yaml (all workflows are created in yaml)
First thing is to create a name for the action in the file and for it to respond when we push.

name: My Github Actions Workflow
on: [push]

jobs:
	testing_github:
		runs-on: ubuntu-latest
		steps:
			- name: Hello
				run: echo "Hello, Github Actions"
			- name: Display repo name
				run: 'this workflow is running in ${{ github.repository}}'
also add in the readme some text

	Hello my workflow

So when we commit and push this github action will run and each step will run in order.
So lets commit the changes
make sure in the correct folder (where the readme file is)
git add .
git status - everything should be red, indicating that it need to be pushed
git commit -m 'github actions workflow'
git status - everything should now be green
git push

now in the repo in github, go to the actions tab and should see the workflow job, go in to it and will see the steps we created, click each one and will see what we asked of it. This is a very simple action, but can see how it all works and the possibilities.

We are going to now create a workflow for a [[Lambda Function]]. As engineers we need to have things set up automatically to avoid and manual intervention/deployment.
So we will create a CI/CD workflow that gets triggered every time we push changes to a [[Lambda Function]].
In this example we will set up the [[Lambda Function]] in the console to speed things up

Into [[AWS]] [[IAM]] to get credentials/access keys. If you have lost the secret access key, then will need to create new, then copy new details ready for later.
In the terminal make sure the keys are set up
aws configure - add the details as required
To validate
aws s3 ls - this should list the [[S3]]'s that you already have.
aws iam list-access-keys     -  this will show keys, but not the secret key, if lost create new.
In github to create a new repository and add these keys
new repo - call it lambda-cicd
add readme file
create

settings - secrets and variables - actions
	new repository secrets
	add keys
		name AWS_ACCESS_KEY_ID
		paste the key
	add secret key
		name AWS_SECRET_ACCESS_KEY
		paste
These will allow github to access [[AWS]] without exposing our credentials. But best practice is to never add secrets or passwords in our coding repo.

Set up a [[Lambda Function]] in the console to save time

Create function
	name my-test-cicd-lambda
Runtime - Python 3.12
make sure create new role with basic is checked
create function - want to be done
Then in code 
	test - event name - test CICD
This shouldn't work, so will need to change text. Deploy, and test again
Go to the [[Git]] hub and clone the new repo, then into your text editor (yes I've stopped using VS Code to learn [[Neo-vim]], yes another learning curve, but one i feel will benefit me in the long run) to build the CI/CD workflow.
New folder in the repo
	mkdir (in terminal) lambda
	cd into it and create a file called lambda_function.py
	(touch lambda_function.py)
In this file we want to mirror the file that was in the lambda function in the console.
In the file start the coding

import json

def lambda_handler(event, context):
    return {
        'statuscode': 200,
        'body': json.dumps ('Hello from CICD github actions workflow again')
    }
Now create a file in the same folder called requirements.txt
'# this file is empty'
Best practice is to include a requirements.txt file even if its a small basic workflow. the file would normally list all the python that the lambda would require.
Now create our github actions workflow. In the root folder (ie lambda-cicd) make a new folder called .github/workflows (if doing this in the terminal would need to make 2 directories or use the -p to create both in same command, mkdir -p .github/workflows), then inside the workflows directory create a file called lambda-deply.yaml (can also use yml, but keep it consistent). so touch 'name of file'. This is where we will design our workflow

name: Deploy AWS Lambda

on:
    push:
        branches:
            - main
        paths:
            - 'lambda/**'

jobs:
    deploy-lambda:
        runs-on: ubuntu-latest
        steps:
            - uses: actions/checkout@v2

            - name: Set up Python
              uses: actions/setup-python@v2
              with:
                python-version: '3.12'

            - name: Install Dependencies
              run: |
                python -m pip install --upgrade pip
                pip install -r lambda/requirements.txt -t lambda/

            - name: Configure AWS credentials
              uses: aws-actions/configure-aws-credentials@v1
              with:
                aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID}}
                aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY}}
                aws-region: eu-west-2

            - name: Deploy lambda function
              run: |
                cd lambda
                zip -r lambda.zip .
                aws lambda update-function-code --function-name my-test-cicd-lambda --zip-file fileb://lambda.zip

So any time something is pushed in our main and anything in our lambda directory this workflow will
	create a job - set name for job
	set and specify the runner (ubuntu)
	set our python environment
	install any packages or dependencies needed
	validate our [[AWS]] credentials 
	then zip the file and deploy into our [[Lambda Function]] in [[AWS]].

git status to see if anything needs pushing to repository
cd back to root
git add .
git commit -m 'initial set up for Lambda github actions'
git push origin main

now to test. In Lambda_function.py change to "Hello from our CICD github actions workflow"
then push again.
git status
git add .
git commit -m 'updated lambda'
git push origin main

Go into the repository then actions, the way he showed us, i noticed a few mistakes, so check code for mistakes and correct/debug. he renamed the file to just lambda.py (i did the same). Push again with a new message to make the code work.
Now in the console and check the actions tab and see if the action has worked. Should see a message.
Never forget to follow best security practices, rotate access keys, never add passwords directly in the code.
Next we will do a pull workflow actions,  this will be a PR event - CICD for [[Cloudformation]] test stacks (PR - [[Pull Request]])
It will do
	runner
	configurations
	validate
	deploy test s3 bucket
	comment to say it looks good
Proceed to [[Pull Request]]






# References
