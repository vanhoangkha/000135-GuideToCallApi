---
title : "Test APIs By Postman"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---
In this step, we will test operation of the APIs using [Postman](https://www.postman.com/downloads/) tool.
#### Test the listing API
1. Click **+** to add a new tab
- Select **GET** method
- Replace **{id}** with `abcd1234`
- Click **Send**

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-1.png?featherlight=false&width=90pc)

2. The responses result is all the information of the user's files with the id `abcd1234`

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-2.png?featherlight=false&width=90pc)

#### Test the writing API
1. Similarly create a new tab
- Select **POST** method
- Enter URL of the writing API that recorded from the previous step
- In **Body** pattern, select **raw**
- Copy the below text block:
```
{
      "user_id": "abcd1234",
      "file": "flowers.png",
      "folder": "",
      "identityId": "123456cvbn",
      "modified": "21-03-2023",
      "size": "32KB",
      "type": "png",
      "tag": "image"
}
```
- Click **Send**

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-3.png?featherlight=false&width=90pc)

2. Wait a moment, see the responses returned

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-4.png?featherlight=false&width=90pc)

3. Open the console of **DynamoDB**, select **Explore items** and select the **Documents** table to check the results:

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-5.png?featherlight=false&width=90pc)

#### Test the deleting API
1. Add a new tab to call the delete API
- Select **DELETE** method
- Enter URL of the deleting API that recorded from the previous step, replace **{id}** with `abcd1234`
- In the **Params** section, enter `file` for the key and `flowers.png` for the value
- Click **Send**

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-6.png?featherlight=false&width=90pc)

2. Check the responses result:

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-7.png?featherlight=false&width=90pc)

3. Back to the **Documents** table, click the **Refresh** button to see the results

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-8.png?featherlight=false&width=90pc)
