---
title : "Cleanup"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---
1. Delete DynamoDB table
- Open [DynamoDB console](https://ap-southeast-1.console.aws.amazon.com/dynamodbv2/home?region=ap-southeast-1#dashboard)
- Select **Tables** on the left menu
- Select **Books** table
- Click **Delete**
- Enter **delete** and click **Delete table**
2. Delete S3 bucket
- Open [S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=ap-southeast-1)
- Select **fcjdmswebstore** bucket
- Click **Empty**
- Enter **permanently delete** and click **Empty**
- Select **fcjdmsstore...-dev** bucket
- Click **Empty**
- Enter **permanently delete** and click **Empty**s
3. Delete REST API
- Open [API Gateway console](https://ap-southeast-1.console.aws.amazon.com/apigateway/main/apis?region=ap-southeast-1#)
- Select **fcj-dms-api**
- Click **Actions** and select **Delete**
- Click **Delete**
4. Delete Lambda functions
- Open [AWS Lambda console](https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions)
- Select **list_documents** function
- Click **Actions**
- Select **Delete**
- Enter **delete** and click **Delete**
- Similar to **upload_document**, **delete_document** functions.
5. Run the following command in the project root directory:
```
amplify remove auth
amplify remove storage
amplify push
amplify delete
```