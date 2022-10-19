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






