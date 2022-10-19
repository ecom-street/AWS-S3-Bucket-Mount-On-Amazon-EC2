# AWS-S3-Bucket-Mount-On-Amazon-EC2
# We will learn how to use S3 as a filesystem on EC2 Linux machine.

<img width="534" alt="s1" src="https://user-images.githubusercontent.com/115148205/196610521-48ae4218-1ffe-47de-a187-7280aced8833.PNG">


We are a preferred AWS consultant and offers the <a href="https://www.ecomstreet.com/aws-consulting-services-company/" target="_blank">best cloud AWS consulting service</a>. Our AWS-certified expert consultants conduct a thorough review and evaluation of your existing IT infrastructure and service interaction model to provide top-notch solutions.

<h3><a href="https://www.ecomstreet.com/aws-consulting-services-company/" target="_blank">Schedule your free consultation today!</a></h3> <br/>

# Let's start!

1) Create an EC2 Linux (I have used Ubuntu in this demo) instance.
Keep everything as default and add the below user data script to install awscli and s3fs utlity from advance section of wizard
<img width="613" alt="1" src="https://user-images.githubusercontent.com/115148205/196611356-6096a577-5ca3-4275-8584-3ce21971562c.PNG">

2) Create an IAM user for s3fs
<img width="662" alt="2" src="https://user-images.githubusercontent.com/115148205/196611584-424dd3bc-da37-4b7a-bb65-0ed5d54275c9.PNG">

3) Give the user a unique name and enable programmatic access

<img width="663" alt="3" src="https://user-images.githubusercontent.com/115148205/196611807-155e566f-e120-417b-97cc-f819a911f41e.PNG">

Set permission --> create a new policy

<img width="662" alt="4" src="https://user-images.githubusercontent.com/115148205/196612011-e366c48e-4dec-4746-9d9e-6a9e1b549e10.PNG">

Select the service as S3 and include below access levels
<img width="663" alt="6" src="https://user-images.githubusercontent.com/115148205/196636363-e8e12374-f9fe-448a-9c02-773f8c73f85e.PNG">

Give the policy a unique name and click Create policy
<img width="663" alt="7" src="https://user-images.githubusercontent.com/115148205/196636630-00724338-35eb-445c-8e12-ac50f347953f.PNG">

Once the policy is created, go back to the IAM tab and hit refresh so that newly created policy is included in the list
, filter by policy name and hit the enable checkbox to add the policy to our IAM user.
<img width="663" alt="8" src="https://user-images.githubusercontent.com/115148205/196636915-7e5cfd54-2ffc-4ec0-b9b3-5ec6c2acb98a.PNG">

Hit create user

<img width="660" alt="9" src="https://user-images.githubusercontent.com/115148205/196637284-036624fb-3028-4cf2-9361-1aa513ec70ad.PNG">

Once the user is created, download the credentials. We are going to use it later.
<img width="661" alt="10" src="https://user-images.githubusercontent.com/115148205/196637561-30e0c4e0-e096-4867-b59f-fe3fb274fb80.PNG">

4) Login to your Ec2 Instance
<img width="944" alt="11" src="https://user-images.githubusercontent.com/115148205/196637797-a955320b-31e4-4b91-9eae-80edf4ba8955.PNG">
<img width="938" alt="12" src="https://user-images.githubusercontent.com/115148205/196638259-120d761c-a0d7-4bca-a24a-a7c95b37b033.PNG">

Go to your home directory and run below commands to create a new directory and to generate some sample files
<img width="734" alt="5" src="https://user-images.githubusercontent.com/115148205/196638590-bc0a484e-5407-4bd7-b86c-ab6ccbbd00a2.PNG">
Next step is to create an S3 bucket.

5) Go to S3 service and create a new bucket
give it a unique name and leave reast of the settings as default.
Block public access to this bucket should be enabled by default.
<img width="926" alt="13" src="https://user-images.githubusercontent.com/115148205/196639572-3b936419-7831-4120-a663-2a16bd1baf84.PNG">

Hit create bucket.

6) Once the bucket is created, go to the ssh session and configure our AWS credentails for authentication using the IAM account that we have created.

Use the command

<img width="701" alt="14" src="https://user-images.githubusercontent.com/115148205/196639945-4880b65d-f369-44ec-a64c-971531cc42e2.PNG">

and provide the credential details that we have downloaded before

<img width="693" alt="15" src="https://user-images.githubusercontent.com/115148205/196640596-2782982f-f049-4223-95d0-ae13f4d679f5.PNG">

8) create the credential file for s3fs.

s3fs supports the standard AWS credentials file stored in ${HOME}/.aws/credentials. Alternatively, s3fs supports a custom passwd file.
The default location for the s3fs password file can be created:
using a .passwd-s3fs file in the users home directory (i.e. ${HOME}/.passwd-s3fs)

file should have the below content:

<img width="664" alt="16" src="https://user-images.githubusercontent.com/115148205/196642233-a86e8913-e97c-41e1-a2ea-13bb90bab6f1.PNG">

You can run the below command as well:

<img width="700" alt="17" src="https://user-images.githubusercontent.com/115148205/196642497-6b77fb33-769f-4db5-9d5e-83137c53cab6.PNG">

<img width="807" alt="18" src="https://user-images.githubusercontent.com/115148205/196644673-2edf4879-3bce-4b75-95a8-fab2402164c1.PNG">

9) Now you can run the command to mount S3 bucket as a filesystem.

<img width="929" alt="19" src="https://user-images.githubusercontent.com/115148205/196644993-edae05e0-255e-4404-a003-c50601709240.PNG">

<img width="943" alt="20" src="https://user-images.githubusercontent.com/115148205/196646166-4d8f4274-e0d5-47e1-8b6d-b09bbb4b8d61.PNG">

10) Once it is mounted successfully, you can verify by running the command

<img width="671" alt="21" src="https://user-images.githubusercontent.com/115148205/196646386-67134230-9a3d-4224-8d12-8045c846c44c.PNG">

<img width="945" alt="22" src="https://user-images.githubusercontent.com/115148205/196648610-bb8357f9-7817-4359-a56c-7638f475eb14.PNG">

11) Add the entry in fstab using the below command so that the changes become persistent after the server reboot as well:

<img width="612" alt="23" src="https://user-images.githubusercontent.com/115148205/196648923-3aaea67c-242b-4f28-b9fe-891d085a682a.PNG">

12) Now the moment of truth, go to your S3 bucket and hit refresh, you should see the files that were present in your file system

<img width="927" alt="26" src="https://user-images.githubusercontent.com/115148205/196651800-5a30d448-eae1-4df2-a13f-f8c1cd90d734.PNG">

<img width="944" alt="25" src="https://user-images.githubusercontent.com/115148205/196651888-65dd1a2c-b373-4036-ad5f-91f606ac94ae.PNG">

13) Let's now verify whether it's getting synced properly after a object delete/addition

Go to your S3 bucket, and upload a new file

<img width="929" alt="24" src="https://user-images.githubusercontent.com/115148205/196652223-d20a4e5d-5de7-40b4-9c93-b430b60349fb.PNG">

Go to your ssh session and do ls in the same directory

<img width="774" alt="27" src="https://user-images.githubusercontent.com/115148205/196652603-e4644a0b-a4b6-4286-b231-640d5946a889.PNG">

# The file that you just uploaded in your S3 bucket appears in your FileSystem.
Same way you can test the delete file operation. And it works both ways i.e if you perform any file operation on your filesystem, it will sync to your S3 bucket as well.





