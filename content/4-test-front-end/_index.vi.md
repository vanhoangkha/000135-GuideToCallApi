---
title : "Kiểm Tra API Với Front-end"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---
Sau khi kiểm tra các API hoạt động đúng với Postman, chúng ta sẽ kiểm tra các API được gọi với front-end xây dựng từ bước 2.
1. Mở tệp **constant.js** trong thư mục gốc của project
- Thay giá trị cho **APP_API_URL** bằng URL của bạn:
- Lưu thay đổi

![WebApp](/images/4-test-front-end/4-test-front-end-1.png?featherlight=false&width=90pc)
![UpdateURL](/images/2-config-api-gw/2-config-api-gw-33.png?featherlight=false&width=90pc)

2. Chạy các dòng lệnh dưới đây:
```
yarn build
aws s3 cp build s3://BUCKET_NAME --recursive
```

Thay `BUCKET_NAME` bằng tên bucket bạn đã tạo ở phần 1.

3. Trở lại ứng dụng web trong phần 1. Đăng nhập bằng tài khoản bạn đã đăng ký ở workshop 2.
- Ấn **Upload**

![WebApp](/images/4-test-front-end/4-test-front-end-2.png?featherlight=false&width=90pc)

4. Ấn **Add files**
- Chọn các tệp bạn muốn tải lên
- Có thể nhập tag hoặc bỏ qua
- Ấn **Upload**

![WebApp](/images/4-test-front-end/4-test-front-end-3.png?featherlight=false&width=90pc)

5. Quay lại bảng điều của DynamoDB và ấn biểu tượng Refresh để xem kết quả.

![WebApp](/images/4-test-front-end/4-test-front-end-4.png?featherlight=false&width=90pc)

- Mở bảng điều khiển của S3 bucket, kiểm tra xem tệp đã được tải lên chưa.

![WebApp](/images/4-test-front-end/4-test-front-end-5.png?featherlight=false&width=90pc)

6. Trở lại với ứng dụng, chọn tab **My Document** ở menu phía bên trái. Bạn sẽ thấy danh sách các tệp vừa được tải lên.
- Ấn **Select** để chuyển sang chế độ xoá

![WebApp](/images/4-test-front-end/4-test-front-end-6.png?featherlight=false&width=90pc)

- Chọn tệp mà bạn muốn xoá
- Ấn **Delete**

![WebApp](/images/4-test-front-end/4-test-front-end-7.png?featherlight=false&width=90pc)

- Ấn **OK** để xác nhận xoá tệp.

![WebApp](/images/4-test-front-end/4-test-front-end-8.png?featherlight=false&width=90pc)

- Tệp đã được xoá 

![WebApp](/images/4-test-front-end/4-test-front-end-9.png?featherlight=false&width=90pc)

- Kiểm tra bảng **Documents**

![WebApp](/images/4-test-front-end/4-test-front-end-10.png?featherlight=false&width=90pc)

- Và bạn có thể ấn vào biểu tượng download để tải một tệp mà bạn muốn

![WebApp](/images/4-test-front-end/4-test-front-end-11.png?featherlight=false&width=90pc)

Chúng ta đã hoàn thành xong việc triển khai và kiểm tra hoạt động của API. Bạn nên dọn dẹp tài nguyên của bài này để sang bài tiếp theo chúng ta sẽ khởi tạo các tài nguyên với AWS Serverless Application Model (AWS SAM).