---
title : "Test APIs With Front-end"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---
After testing that the APIs work properly with Postman, we will test the APIs that are called with the front-end built from part 2.
1. Open **constant.js** in the root folder of project
- Change value of **APP_API_URL** with your URL:
- Save file

![WebApp](/images/4-test-front-end/4-test-front-end-1.png?featherlight=false&width=90pc)
![UpdateURL](/images/2-config-api-gw/2-config-api-gw-33.png?featherlight=false&width=90pc)

2. Run the command lines under here:
```
yarn build
aws s3 cp build s3://BUCKET_NAME --recursive
```

Replace `BUCKET_NAME` with the bucket name you created in part 1.

3. Go back to the web application in part 1. Log in with the account you registered in workshop 2.
- Click **Upload**

![WebApp](/images/4-test-front-end/4-test-front-end-2.png?featherlight=false&width=90pc)

4. Click **Add files**
- Select the files you want to upload
- Can enter tag or ignore
- Click **Upload**

![WebApp](/images/4-test-front-end/4-test-front-end-3.png?featherlight=false&width=90pc)

5. Return to the DynamoDB dashboard and click the Refresh icon to see the results.

![WebApp](/images/4-test-front-end/4-test-front-end-4.png?featherlight=false&width=90pc)

- Open the console of the S3 bucket, check if the file has been uploaded.

![WebApp](/images/4-test-front-end/4-test-front-end-5.png?featherlight=false&width=90pc)

6. Return to the application, and select the **My Document** tab on the left menu. You will see a list of files that have just been uploaded.
- Click **Choose** to switch to delete mode

![WebApp](/images/4-test-front-end/4-test-front-end-6.png?featherlight=false&width=90pc)

- Select the file you want to delete
- Click **Delete**

![WebApp](/images/4-test-front-end/4-test-front-end-7.png?featherlight=false&width=90pc)

- Click **OK** to confirm deleting

![WebApp](/images/4-test-front-end/4-test-front-end-8.png?featherlight=false&width=90pc)

- File has been deleted

![WebApp](/images/4-test-front-end/4-test-front-end-9.png?featherlight=false&width=90pc)

- Check **Documents** table

![WebApp](/images/4-test-front-end/4-test-front-end-10.png?featherlight=false&width=90pc)

- And you can click the download icon to download a file you want

![WebApp](/images/4-test-front-end/4-test-front-end-11.png?featherlight=false&width=90pc)

We have completed the implementation and testing of the API. You should clean up the resources of this workshop so that in the next article we will initialize resources with the AWS Serverless Application Model (AWS SAM).
