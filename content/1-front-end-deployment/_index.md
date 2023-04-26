---
title : "Front-end Deployment"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
In the first step in this workshop, we will host the web application (front-end) with S3 Static website hosting:
1. Open [Amazon S3 console](https://s3.console.aws.amazon.com/s3/get-started?region=ap-southeast-2)

![S3Console](/images/1-front-end-deployment/1-front-end-deployment-1.png?featherlight=false&width=90pc)

2. Click **Create bucket**

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-2.png?featherlight=false&width=90pc)

3. Enter bucket name, such as: `fcjdmswebstore`
- Select the region closest to you

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-3.png?featherlight=false&width=90pc)

4. Uncheck block from allowing public access
- Check to **I acknowledge that the current settings might result in this bucket and the objects within becoming public**

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-4.png?featherlight=false&width=90pc)

5. Click **Create bucket** button

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-5.png?featherlight=false&width=90pc)

6. Click on created bucket

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-6.png?featherlight=false&width=90pc)

7. Click **Properties** tab

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-7.png?featherlight=false&width=90pc)

8. Scroll down to the bottom, click **Edit** in **Static web hosting** pattern

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-8.png?featherlight=false&width=90pc)

9. Select **Enable** to enable host web static on S3
- Select **Host a static website** for **Hosting type**
- Enter `index.html` for **Index document** pattern

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-9.png?featherlight=false&width=90pc)

10. Click **Save changes**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-10.png?featherlight=false&width=90pc)

- After successfully enabling, please write down the path of the web

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-11.png?featherlight=false&width=90pc)

11. After successful enable, please  take note of the path of the web:
- Select **Permissions** tab
- Click **Edit** of **Bucket policy** pattern

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-12.png?featherlight=false&width=90pc)

12. Copy the below code block to **Policy**
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*"
        }
    ]
}
```
- Replace `BUCKET_NAME` with the bucket name you created, then click **Save changes**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-13.png?featherlight=false&width=90pc)

13. Open the **src/component/Home/Upload.js** file in the application's source code directory and uncomment the code that calls the API to write data to DynamoDB.

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-16.png?featherlight=false&width=90pc)

14. Next run the following command at the root of the project you downloaded from workshop 2.
```
yarn build
aws s3 cp build s3://BUCKET_NAME --recursive
```

- Replace `BUCKET_NAME` with the bucket name you created

{{% notice note %}}
If your upload fails, configure the access key ID, secret access key, aws region and output format with `aws configure` command
{{% /notice %}}
Result after uploading:

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-14.png?featherlight=false&width=90pc)

15. Paste the web link you take notes into your web browser

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-15.png?featherlight=false&width=90pc)

You have finished hosting your website on S3. In the next section, we update the lambda functions of workshop 2.