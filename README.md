# AWS-S3-Bucket-Mt-ounOn-Amazon-EC2
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

