05/11/2024 0705

Status #idea

Tags:

# Terraform Portfolio Project

This project could take me some time, but one i will make it happen. Gonna be a lot to learn, but excited to get going.

So will start with setting up the github. Will do a complete new start, new repository, new directory within my document folder. Doing all this due to it being a showcase to let potential employers see.
So make a new github repository in the normal way and follow the list of commands to push the first commit etc. 
Next was to get npm and nodejs installed on the pc, got an error about a corrupt file and it would fail to install. I asked on the discord and every support at npm itself. What i needed to do was update the keys on my system and then it worked.
sudo pacman -Sy archlinux-keyring
sudo pacman -key --populate archlinux
sudo pacman-key --refresh-keys
if all else fails ask chatgpt.,
Then needed to run the command npm run dev in the newly made nextjs-blog directory
Within this directory you can run several commands
npm run dev - starts the development server
npm run build - builds the app for production
npm start - runs the built app in production mode

Edit: after completing this project at least twice, i found a few errors form the brief and the videos, had to work out a few things for myself. Firstly done do git clone, this will mess thing up for you, can do it, but need to stay in main repository folder, the clone folder is mainly just a back up.

So run npm run dev and a link will be shown for a local address to view in browser. ctrl + c to kill the command in the terminal.
Next is too record a loom video explaining the next.js code and structure of the project, covering key files and folders such as pages, components and public. Then push the changes to github. This i will leave for a while as loom isn't compatible with linux, and i need a better understanding of what these folder are going to be for, nothing has been explained and they are empty, i guess it will have the web pages in them??
So this project we are just deploying a simple static web page using [[[AWS]]] services, [[Cloud Front]] and [[S3]] as [[S3]] is great for static web pages.
So need to make a new directory in the root folder for all the terraform code. From root directory mkdir terraform-js the cd into it.
In here create a new state.tf file
create a new [[S3]] bucket and dynamodb (luckily i have a dynamodb made that is lockid, so will use this)
Dynamodb is called terraform-lock-file
stat [[S3]] is called cloudtechjeff-nextjs-state
These will change later
Have now added the provider block in the main.tf and in the main.tf we need to create an s3 bucket.

'# S3 bucket'
resource "aws_s3_bucket" "next_bucket" {
	bucket = "global unique name" 
}

This should create the bucket, now need to set some ownership controls so that we are the only ones that can have control of the objects within the bucket

'# Ownership Controls'
resource "aws_s3_bucket_ownership_controls" "nextjs_bucket_ownership_controls" {
	bucket = aws_s3_bucket.nextjs.bucket.id (this is reference to the bucket we want control of)
	rule {
		object_ownership = "BucketOwnerPreferred"
		}
}
This will insure the bucket owner has control over the objects in the bucket, even if the objects are uploaded from different accounts
To allow public access to the bucket we need to disable some public block settings as default, they are automatically set to block any access

'# Public Access Block
resource "aws_s3_bucket_public_access_block' "nextjs_bucket_public_access_block"
	bucket = aws_s3_bucket.nextjs_bucket.id
	(remember, need to pass the bucket id that you want to change details of)
	
block_public_acls = false
block_public_policy = false
ignore_public_acls = false
restrict_public_buckets = false

Setting these all to false will ensure the bucket is publicly  accessible, later we will add an new layer of security to only allow us to do things
Also need to do the same for the bucket acl so the objects can  be publicly accessible

'# Bucket ACL'
resource "aws_s3_bucket_acl" "nextjs_bucket_acl"
	depends_on = [
		aws_s3_bucket_ownership_controls.bucket_ownership_controls
		aws_s3_bucket_public_access_block.nextjs_public_public_access_block
		bucket = aws_s3_bucket.nextjs_bucket.id 
		acl = "public- read"
		]
This will allow everyone to be able to read objects in the bucket, Depends_on ensures that the settings are applied before the acl is set
Finally need to set a policy to allow public access. Always need a policy/permissions.
These are all layers of the security for our S3 bucket

'# Bucket Policy'
resource "aws_s3_bucket_policy" "nextjs_bucket_policy" {
	bucket = aws_s3_bucket.nextjs_bucket.id
	policy = jsonencode({
	Version = "2012-10-17"
	Statement = [
		{
		Sid = "PublicReadGetObject"
		Effect = "Allow"
		Principal = "'star"
		Action = "s3:GetObject"
		Resource = "${aws_s3_bucket.nextjs_bucket.arn}/star"
		}
	]
})
}
Why do we have all these different  controls?
These are multi layers of security
	*ownership control* - to define ownership of the objects, ie the owner of the bucket
	*Block public access* - centralised way to control access to the objects. All the false arguments can be found in the documents files.
	*Bucket Acl* - To define access using pre defined access controls. ACL = "public-read" is the important one
	*Bucket Policy* - is to define detailed permissions
Now push to github repository (and do this more often as its a great way to see progress and to let the team know what being done)
git add .
git commit -m "message for what has been done"
git push origin main

Now we will be adding [[Cloud Front]] service. [[Cloud Front]] will use S3 bucket as its origin and provide a [[Content Delivery Network]] to provide quicker access and better performance.
Firstly we need to define an Origin Access Identity ([[OAI]]). By doing this we ensure only [[Cloud Front]] can access the [[S3]] bucket (extra layer of security mentions earlier)

'# Origin Access Identity
resource "aws_cloudfront_origin_access_identity" "origin_access_identity" {
	comment = "OAI for Nextjs portfolio site"

}
Next define the cloudfront distribution itself

'# Cloudfront Distribution
resource "aws_cloudfront_distribution" "nextjs_distribution" {
	origin {
		domain_name = aws_s3_bucket.nextjs_bucket.bucket_regional_domain_name
		origin_id = "S3-nextjs-portfolio-bucket"
		s3_origin_config {
		origin_access_identity = aws_cloudfront_origin_access_identity.origin_access_identity.cloudfront_access_identity_path
		}
		}
	enabled = true
	is_ipv6_enabled = true
	comment = "Nextjs portfolio site"
	default_root_object = "index.html"
	default_cache_behavior {
	allowed_methods = [ "GET", "HEAD", "OPTIONS" ]
	cached_methods = [ "GET", "HEAD" ]
	target_origin_id = "S3-nextjs-portfolio-bucket"

forwarded_values {
query_string = false
cookies {
forward = "none"
}
}

viewer_protocol_policy = "redirect-to-https"
min_ttl = 0
default_ttl = 3600
max_ttl = 86400
}
restrictions {
geo_restriction {
restriction_type = "none"
}
}
viewer_certificate {
cloudfront_default_certificate = true
}
}

Check spacing and syntax.
The [[Cloud Front]] distribution block is what and where we fetch the content from.

Now need to create a new S3 bucket and DynamoDB for the state file as said before, can do it all in the cli
create S3
aws s3ap, create-bucket --bucket you bucket name --region your region --create-bucket-configuration LocationConstraint=your region
Then create the dynamodb
aws dynamodb create-table --table-name your-table-name \  
--attribute-definitions AttributeName=LockID,AttributeType=S \  
--key-schema AttributeName=LockID,KeyType=HASH \  
--provisioned-throughput ReadCapacityUnits=2,WriteCapacityUnits=2
Upload next.js to the S3
aws s3 sync ./out s3://your-bucket-name
Add the names to the state file.
Into the terraform-js folder we created either in VSCode or terminal
terraform init
terraform plan
terraform apply
should now be done
terraform show
scroll up and fine the domain name, this in important, that a copy of it
now to deploy the out folder
cd .. to go back a level
should see the out folder in the ls then deploy the websire
aws s3 sync ./out s3://you bucket name

Now in a browser go to the domain name we copied and should see the next.js website.
maybe push to github, but i did get errors

terraform destroy 





# References
