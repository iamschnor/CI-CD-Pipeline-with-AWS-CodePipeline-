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

<img width="548" height="430" alt="image" src="https://github.com/user-attachments/assets/21666198-9982-4a57-a5bd-cddfa84531f4" />

 

Step 2: Proceed to upload the files for the application to your CodeCommit Repo
A)	Click CODE and scroll all the way down and click Add File  - Upload File ( select the Index.html file and Mount.jpg ) 
 
 <img width="683" height="316" alt="image" src="https://github.com/user-attachments/assets/b6e44ea7-1392-44ab-b13f-83469abce251" />

Step 3: Fill in your name and email address, then click Commit Changes


<img width="679" height="311" alt="image" src="https://github.com/user-attachments/assets/e0eecb99-7e66-4b28-a438-f76f10ea0f8c" />

                 
Step 4: Search for S3 in the Tool bar and select S3 – proceed by clicking “Create Bucket“ 
-	Ensure the bucket is within the desired Availability Zone 
-	Uncheck “Block all public access” to be able to access the website publicly (keep unkeep if the data is private) 
-	Add Tags
-	Keep Versioning disabled since the repo handles the version 
-	Click Create 


<img width="975" height="256" alt="image" src="https://github.com/user-attachments/assets/b65e8a26-7222-4bb5-a8ec-5ebc8e42d7c8" />


<img width="975" height="419" alt="image" src="https://github.com/user-attachments/assets/14d65759-1127-4e41-bb8a-d4024992ec6c" />

Step 4: Click the new bucket you created, select properties and scroll to the bottom of the page and you will find Static Website Hosting then click Edit 

<img width="975" height="213" alt="image" src="https://github.com/user-attachments/assets/fe4a9c16-2703-4106-96ac-0e61be507faa" />

<img width="975" height="231" alt="image" src="https://github.com/user-attachments/assets/55585a69-b177-4370-90fa-883f36fe2876" />

<img width="975" height="231" alt="image" src="https://github.com/user-attachments/assets/a4d958ec-a311-46c0-917d-e27d10345080" />


Step 5: Enable static website hosting and select “Host a static Website” 
-	Type the name of the Application file in the “index document” field 
-	 <img width="490" height="414" alt="image" src="https://github.com/user-attachments/assets/b7d7c5aa-0a4a-40f2-b9a6-746d84fcabad" />


Step 6: Create a bucket policy
-	While in the S3, click “permissions” then Click Edit Bucket Policy 
 
<img width="975" height="144" alt="image" src="https://github.com/user-attachments/assets/8c9fb8a1-cbdb-4d85-9a80-589049aa883e" />

<img width="975" height="165" alt="image" src="https://github.com/user-attachments/assets/ddaa8976-46b0-4b67-a453-ff8904bceaeb" />

 
-	Click “Policy Generator” 
-	Select “S3 Bucket Policy” from the drop down menu 
-	Use “*” for principal 
-	From the Actions drop down menu click “getobject”
-	ARN: Copy and paste the ARN from the S3 bucket you created 
NB: For the policy to be effective on all objects in the S3 bucket, while pasting the ARN at the end add “/*”
-	Click Add statement and then Generate Policy 
-	Copy the Yaml File (Generated Policy) and paste it in your S3 bucket Policy and click save changes 
 
<img width="360" height="319" alt="image" src="https://github.com/user-attachments/assets/90251c8e-d596-4985-8daa-602f7e4661b1" />

<img width="382" height="259" alt="image" src="https://github.com/user-attachments/assets/52ef4197-70c3-422b-be14-c03ff1730a31" />

<img width="358" height="351" alt="image" src="https://github.com/user-attachments/assets/debc1a90-5eaf-40c2-82f3-203aa4317456" />

 
 

                      Step 7: Set up the AWS Codepipeline 
-	Click “Create Pipeline”
NB: You can add encryption for additional security 
-	Choose the source Provider (AWS Codecommit) 
-	Select the repository and the branch 
-	Switch Change detection options to “AWS CodePipeline” 
-	Deploy Provider select “Amazon S3” – Select the region  - select the desired bucket  
-	Review and click Create Pipeline 
 
<img width="496" height="443" alt="image" src="https://github.com/user-attachments/assets/f8a63907-bf6c-4c33-a7f0-7d65d3a6ccd9" />

 
<img width="573" height="451" alt="image" src="https://github.com/user-attachments/assets/80cae472-9101-4567-b84d-077147ca7e2b" />

 <img width="505" height="576" alt="image" src="https://github.com/user-attachments/assets/722caf5b-2c1f-4f40-87d2-0442db92d7b1" />


Step 8: Verify if the website is now running by going to S3 and scroll down to Static Website Hosting and copy the custom URL and paste in your browser 
 <img width="890" height="405" alt="image" src="https://github.com/user-attachments/assets/451cf2c2-89f3-49ea-889b-9d981a238d5e" />

