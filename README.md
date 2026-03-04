# CI-CD-Pipeline-with-AWS-CodePipeline-

<img width="867" height="922" alt="image" src="https://github.com/user-attachments/assets/c4b7f217-5cd6-4b6a-b262-c765008c47fc" />

Project Summary
This project demonstrates how to build a fully managed Continuous Deployment (CD) pipeline on AWS using CodePipeline to automatically deploy a static web application to Amazon S3.
The objective of this lab is to design and implement a native AWS CI/CD workflow that takes source code from a repository, processes it through a deployment pipeline, and publishes the application to an S3 bucket configured for static website hosting.
The pipeline is built using:
•	AWS CodeCommit as the source code repository
•	AWS CodePipeline to orchestrate the deployment workflow
•	Amazon S3 to host and serve the static web application
This project showcases practical DevOps skills, including:
•	Setting up source control in AWS
•	Configuring automated deployment pipelines
•	Managing IAM permissions between AWS services
•	Deploying and hosting static applications in the cloud
•	Implementing continuous deployment without manual intervention
By completing this project, I demonstrate hands on experience with AWS-native CI/CD services and the ability to automate application delivery using cloud-native tooling.

Step 1: Open CodeCommit and create a Repository (add Tags for best management practice)
 

Step 2: Proceed to upload the files for the application to your CodeCommit Repo
A)	Click CODE and scroll all the way down and click Add File  - Upload File ( select the Index.html file and Mount.jpg ) 
 
Step 3: Fill in your name and email address, then click Commit Changes
                 
Step 4: Search for S3 in the Tool bar and select S3 – proceed by clicking “Create Bucket“ 
-	Ensure the bucket is within the desired Availability Zone 
-	Uncheck “Block all public access” to be able to access the website publicly (keep unkeep if the data is private) 
-	Add Tags
-	Keep Versioning disabled since the repo handles the version 
-	Click Create 

 

 

Step 4: Click the new bucket you created, select properties and scroll to the bottom of the page and you will find Static Website Hosting then click Edit 
 
 

Step 5: Enable static website hosting and select “Host a static Website” 
-	Type the name of the Application file in the “index document” field 
-	 
Step 6: Create a bucket policy
-	While in the S3, click “permissions” then Click Edit Bucket Policy 
 

 
-	Click “Policy Generator” 
-	Select “S3 Bucket Policy” from the drop down menu 
-	Use “*” for principal 
-	From the Actions drop down menu click “getobject”
-	ARN: Copy and paste the ARN from the S3 bucket you created 
NB: For the policy to be effective on all objects in the S3 bucket, while pasting the ARN at the end add “/*”
-	Click Add statement and then Generate Policy 
-	Copy the Yaml File (Generated Policy) and paste it in your S3 bucket Policy and click save changes 
 

 
 

                      Step 7: Set up the AWS Codepipeline 
-	Click “Create Pipeline”
NB: You can add encryption for additional security 
-	Choose the source Provider (AWS Codecommit) 
-	Select the repository and the branch 
-	Switch Change detection options to “AWS CodePipeline” 
-	Deploy Provider select “Amazon S3” – Select the region  - select the desired bucket  
-	Review and click Create Pipeline 
 

 

 

Step 8: Verify if the website is now running by going to S3 and scroll down to Static Website Hosting and copy the custom URL and paste in your browser 
 
