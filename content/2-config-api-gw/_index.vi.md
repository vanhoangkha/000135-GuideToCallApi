---
title : "Thiết Lập API Gateway"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Thiết lập API Gateway

1. Mở bảng điều khiển của [Amazon API Gateway](https://ap-southeast-1.console.aws.amazon.com/apigateway/main/apis?region=ap-southeast-1)

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-2.png?featherlight=false&width=90pc)

2. Ấn **Create API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-3.png?featherlight=false&width=90pc)

3. Kéo xuống mục **REST API**, ấn **Build**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-4.png?featherlight=false&width=90pc)

4. Để mặc định **New API**.
- Nhập tên cho API: `fcj-dms-api`
- Chọn kiểu Endpoint là **Regional**
- Ấn **Create API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-5.png?featherlight=false&width=90pc)

5. Sau khi tạo xong API, ấn **Create Resource** để tạo resource cho API.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-6.png?featherlight=false&width=90pc)

6. Nhập tên cho resource: `docs`, sau đó ấn **Create resource**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-7.png?featherlight=false&width=90pc)

7. Chọn resource **docs**, sau đó ấn **Create Method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-8.png?featherlight=false&width=90pc)

8. Chọn method **POST**
- Tích vào **Lambda Proxy integration**.
- Chọn vùng của Lambda function mà bạn đã tạo.
- Chọn function **upload_document**.
- Cuối cùng ấn **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-9.png?featherlight=false&width=90pc)

9. Chọn resource **/docs** và ấn **Create resource**:

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-10.png?featherlight=false&width=90pc)

10. Nhập tên cho resource: `{id}`, sau đó ấn **Create resource**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-11.png?featherlight=false&width=90pc)

11. Chọn resource **/{id}** và ấn **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-12.png?featherlight=false&width=90pc)

12. Chọn method **GET**.
- Tích vào **Lambda Proxy integration**
- Chọn vùng của Lambda function mà bạn đã tạo
- Chọn function **list_documents**
- Cuối cùng ấn **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-13.png?featherlight=false&width=90pc)

13. Chọn resource **/{id}**, sau đó ấn **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-14.png?featherlight=false&width=90pc)

14. Chọn method **DELETE**.
- Tích vào **Lambda Proxy integration**
- Chọn vùng của Lambda function mà bạn đã tạo
- Chọn function **list_documents**
- Cuối cùng ấn **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-15.png?featherlight=false&width=90pc)

15. Chọn method **DELETE**, sau đó chọn **Method request** và ấn **Edit**.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-16.png?featherlight=false&width=90pc)

16. Mở rộng **URL Query String Parameters**
- Ấn **Add query string** để thêm một parameter mới. 
- Nhập tên của parameter: `file`. Parameter này lưu giá trị tên của file mà bạn muốn xoá.
- Ấn **Save**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-17.png?featherlight=false&width=90pc)

17. Chọn resource **docs**, sau đó ấn **Enable CORS**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-18.png?featherlight=false&width=90pc)

18. Chọn method **POST** và ấn **Save**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-19.png?featherlight=false&width=90pc)

19. Làm tương tự để kích hoạt CORS cho resource **/{id}**
- Chọn resource **/{id}**, sau đó ấn **Enable CORS**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-20.png?featherlight=false&width=90pc)

20. Chọn method **DELETE** và **GET**, sau đó ấn **Save**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-21.png?featherlight=false&width=90pc)

21. Sau khi hoàn thành thiết lập, chúng ta deploy API. Chọn **/**, sau đó ấn **Deploy API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-22.png?featherlight=false&width=90pc)

22. Chọn **[New Stage]**
- Nhập tên cho stage: `dev`
- Ấn **Deploy**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-23.png?featherlight=false&width=90pc)

23. Ghi lại URL của API dùng cho phần tiếp theo.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-24.png?featherlight=false&width=90pc)


#### Cập nhật Lambda function

1. Mở bảng điều khiển của [AWS Lambda](https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions).
2. Chọn function **upload_document**.
3. Comment dòng số 13 và bỏ comment dòng số 12.
4. Ấn **Deploy**

![UpdateFunction](/images/2-config-api-gw/2-config-api-gw-1.png?featherlight=false&width=90pc)

Bạn đã hoàn thành việc thiết lập API. Tiếp theo chúng ta sẽ kiểm tra hoạt động của API và tích hợp nó vào ứng dụng của mình.

