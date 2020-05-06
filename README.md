# aws-s3-python

# Instructions for setting up of AWS S3 for interfacing with REST API's for using it in WebAPPS.  

*  Log on to https://aws.amazon.com/free/ and create a free tier account which is generally enough for small webapps.       
*  Go to https://aws.amazon.com/console/ and enter your credentials for logging in (by default you are root user).          

![aws](/img/aws.JPG)   

* Make sure you are on the similar console as shown above.

> Note : bucket creation as follows below can also be done by code but i generally like AWS UI for this purpose and all other work can surely be done using code obviously.  

* Now, click on ```Services``` drop down menu, select ```S3``` under ```Storage``` section.     
* click on ```create bucket``` as shown below.    
![aws](/img/bucket_1.JPG)   
* Now, follow the instructions as below for creating your first bucket on s3.    
> Note1 : bucket-name should be unique identifier.
> Note2 : Regarding Blocking Public permissions : If you just have to read and write on the objects stored in s3 , then you can keep the blocking permissions On but since i am using it for rendering files on the web (like images, videos) so, i am disabling any blocking permissions as if left on, these can override any permissions on individual objects even though they are public.        

![aws](/img/first.JPG)      
 
![aws](/img/second.JPG)     

* Now, you should have your bucket showing up on your S3 console.       
* Now, click on bucket-name and then move to ```Permissions``` section and then select ```Bucket Policy```.      
* You can edit the policy by creating a new policy (at the end, it is given -```policy generator```).       
* Follow the instructions as shown below to create policy  - This is make sure that every default object uploaded to the container becomes public so that we can render the files directly on the web.           

> Note : In the policy generator section, we need ARN which you can get from your bucket-policy section, generally it's something like - 
aws:s3:::bucket-name and you just need to append "\\" at the end of arn while entering the form.           

![aws](/img/policy.jpg)        

* Now, paste the code generated by clicking on ```Add statement``` and copy the code and paste it in bucket-policy editor.    

![aws](/img/policy1.jpg)        

* Now, you have made the policy for making all the uploaded objects public.    

* Then, just a last step for getting the credentials to access the S3 API using Python library boto3.   
* Create IAM roles for getting full control over the s3 buckets.        
* Follow the steps below and get your credentials.    
* Now, again select ```Services``` drop down menu and select ```IAM``` from  ```Security, Identity, & Compliance``` section (you can also search IAM in the search bar and select it).     
* Now, select Users and click on Add user.    

![aws](/img/iam.jpg)              

* Then follow below instructions for creating your IAM roles and getting your credentials.     
![aws](/img/iam_1.JPG)              

* Now, select ```AmazonS3FullAccess``` as shown below.    

![aws](/img/iam_3.JPG)              

* Skip the ```add tags``` section and click on Next.    

* Now, review your policy and on the screen you have your API access Id and API access secret key , keep them safe by copying it or downloading as csv.         
* Now, you can interface S3 with boto3 (python module) for accessing S3 with your obtained credentials.    

🎉 Great, you have now got your AWS S3 API credentials with full access over s3.   
