---
title : "Config API Gateway"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Update Lambda function

1. Open [AWS Lambda console](https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions).
2. Select **upload_document** function.
3. Comment on line 13 and uncomment line 12.
4. Click **Deploy**

![UpdateFunction](/images/2-config-api-gw/2-config-api-gw-1.png?featherlight=false&width=90pc)

#### Config API Gateway

1. Open [Amazon API Gateway console](https://ap-southeast-1.console.aws.amazon.com/apigateway/main/apis?region=ap-southeast-1)

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-2.png?featherlight=false&width=90pc)

2. Click **Create API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-3.png?featherlight=false&width=90pc)

3. Scroll down to **REST API** section, click **Build**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-4.png?featherlight=false&width=90pc)

4. Leave the default **REST** for the protocol.
- Select **New API** 
- Enter API name: `fcj-dms-api`
- Select Endpoint type as **Regional**
- Click **Create API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-5.png?featherlight=false&width=90pc)

5. After creating the API, click **Action | Create Resource** to create resource for API.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-6.png?featherlight=false&width=90pc)

6. Enter resource name: `docs`, then click **Create Resource**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-7.png?featherlight=false&width=90pc)

7. Select **docs** resource, then click **Action | Create Method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-8.png?featherlight=false&width=90pc)

8. Click **POST** method và and click the **✔** symbol

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-9.png?featherlight=false&width=90pc)

9. Set up the method as follows:
- Keep default Integration type as **Lambda Function**
- Check **Use Lambda Proxy integration**
- Select the region of the Lambda function you created
- Select **upload_document** function
- Finally press **Save**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-10.png?featherlight=false&width=90pc)

10. Click **OK**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-11.png?featherlight=false&width=90pc)

11. After created GET method, click **Action | Create Resource** to create next resource.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-12.png?featherlight=false&width=90pc)

12. Enter resource name: `id` and resource path as `{id}`, then click **Create Resource**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-13.png?featherlight=false&width=90pc)

13. Select **{id}** resource, then click **Action | Create Method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-14.png?featherlight=false&width=90pc)

14. Select **GET** method and click the **✔** symbol

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-15.png?featherlight=false&width=90pc)

15. Set up the method as follows:
- Keep default Integration type as **Lambda Function**
- Check **Use Lambda Proxy integration**
- Select the region of the Lambda function you created
- Select **list_documents** function
- Finally press **Save**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-16.png?featherlight=false&width=90pc)

16. Click **OK**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-17.png?featherlight=false&width=90pc)

17. Click **Action | Create Method** to create a new method

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-18.png?featherlight=false&width=90pc)

18. Select **DELETE** method and click the **✔** symbol

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-19.png?featherlight=false&width=90pc)

19. Set up the method as follows:
- Keep default Integration type as **Lambda Function**
- Check **Use Lambda Proxy integration**
- Select the region of the Lambda function you created
- Select **delete_documents** function
- Finally press **Save**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-20.png?featherlight=false&width=90pc)

20. Click **OK**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-21.png?featherlight=false&width=90pc)

21. Select **DELETE** method, then select **Method Request**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-22.png?featherlight=false&width=90pc)

22. Expand **URL Query String Parameters** section, click **Add query string** to add a new parameter 

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-23.png?featherlight=false&width=90pc)

23. Enter parameter name: `file` and click the **✔** symbol. This parameter is value of of the name of the file you want to delete.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-24.png?featherlight=false&width=90pc)

24. Select **docs** resource, then click **Actions | Enable CORS**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-25.png?featherlight=false&width=90pc)

25. Click **Enable CORS and replace existing CORS headers**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-26.png?featherlight=false&width=90pc)

26. Click **Yes, replace existing values**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-27.png?featherlight=false&width=90pc)

27. Do the same to enable CORS for **{id}** resource
- Select **{id}** resource, then click **Actions | Enable CORS**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-28.png?featherlight=false&width=90pc)

- Click **Enable CORS and replace existing CORS headers**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-29.png?featherlight=false&width=90pc)

- Click **Yes, replace existing values**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-30.png?featherlight=false&width=90pc)


28. After completing the setup, we deploy the API. Select **/docs**, then click **Actions | Deploy API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-31.png?featherlight=false&width=90pc)

29. Select **[New Stage]**
- Enter stage name: `dev`
- Click **Deploy**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-32.png?featherlight=false&width=90pc)

30. Note down the URL of the API used for the next section.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-33.png?featherlight=false&width=90pc)

31. Expand the stage, select the **POST** method and write down the URL.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-34.png?featherlight=false&width=90pc)

32. Select the **DELETE** method and write down the URL.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-35.png?featherlight=false&width=90pc)

You have finished setting up the API. Next, we will test the API working and integrate it into our application.

