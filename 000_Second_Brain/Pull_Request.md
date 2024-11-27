17/11/2024 0941

Status #idea

Tags:

# Pull Request

Pull actions workflow, this will be a PR event - CICD for [[Cloudformation]] test stack
	runner
	configurations
	validate
	deploy test [[S3]] bucket
	comment to say it looks good
This will allow other to see that your code is good without having to check the code, this will speed up productivity.

In to editor to start building. Stay in the same repository for this. Create new folder in the root called [[Cloudformation]]. Then a file called s3-bucket.yaml

AWSTemplateFormatVersion: '2010-09-09'
Description: 'S3 bucket for our CICD PR'

Parameters:
  Environment:
    Type: String
    Default: test
    AllowedValues:
      - test
      - staging
      - production

Resources:
  MyS3Bucket:
    Type: 'AWS::S3::Bucket'
    Properties:
      BucketName: !sub '${AWS::StackName}-${Environment}-bucket'
    Tags:
      - Key: Environment
        Value: !Ref Environment
  
Outputs:
  BucketName:
    Description: 'Name of created S3 Bucket'
    Value: !Ref MyS3Bucket
    
 In the .github/workflows folder create file called
	 touch cfn-validate-pr.yaml

  
name: Validate CloudFormation on PR

on:
  pull_request:
    paths:
      - 'cloudformation/**'

permissions:
  pull-request: write
  contents: read

jobs:
  validate-cfn:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: eu-west-2

      - name: Validate CloudFormation Template
        run: |
          aws cloudformation validate-template --template-body file://cloudformation/s3-bucket.yaml

      - name: Deploy our Stack
        run: |
          stack_name="pr-test-stack-${{ github.event.pull_request.number }}"
          aws cloudformation create-stack --stack-name $stack_name --template-body file://cloudformation/s3-bucket.yaml --parameters ParameterKey=Environment,ParameterValue=test

      - name: Comment on the PR
        uses: actions/github-script@v6
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          script: |
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: `CloudFormation test stack deployed. Stack name: pr-test-stack-${{ github.event.pull_request.number }}`
            })
  cleanup-on-merge:
    runs-on: ubuntu-latest
    if: github.event.pull.request.merged = true
    steps:
      - name: configure AWS Credentials
        uses: aws-actions/configure-aws-credentals@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}         
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }} 
          aws-region: eu-west-2

      - name: Delete test stack
        run: |
          stack-name="pr-test-stack-${{github.event.pull_request.numbers}}"
          aws cloudformation delete-stack --stack-name $stack_name

Quick summary

When a pull request effecting our cloud [[S3]] bucket or is created or updated our workflow will get triggered, it will create a test stack, check then when its merged it will delete the test stack using our credentials and resources.

Will now commit the changes to github
	Make sure in correct folder
	git add .
	git commit -m 'initial setup'
	git push -u origin main
Into github to validate the push then we will initiate a pull request to trigger the code.
SO back to editor to create a new branch. Make a change to s3, then pull request
In terminal
	git checkout -b update-cfn  -  this will create a new branch called update-cfn
	git branch - this will show all branches
To make a change to the s3, just add a new tag to the resources code 
	- key: Environment
		value: GithubActionsTesting

Save and commit changes

git add .
git comment -m 'update to s3 tags'
git push

it should show a message asking to use a different command, use this and it will push to new branch. This should trigger the pull request as we made a change to the s3 bucket.
	so in github go to repository
	should set the push with compare and pull request
	add in the description
		s3 bucket with cloudformation, update tags
below it should show what the changes were.

create pull request.

It should now be running the workflow we coded. In his it shows an error, which is exactly why we have this kind of workflow. To see the error before it goes too far and becomes an issue later down the line. the error appeared to be an indentation error, so correct anything that you see until it works, or even use chatgpt to check for you.
After fixing all errors you should see it has worked, can also go into AWS console and check that the S3 and stack have been created. Then to finish up back in github and merge, this will initiate the action to delete the S3 and stack.
I had no conflicts in my code and it worked with no issues.







# Reference
