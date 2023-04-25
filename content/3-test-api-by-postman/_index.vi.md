---
title : "Kiểm Tra API Với Postman"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---
Trong bước này, chúng ta sẽ kiểm tra hoạt động của các API bằng công cụ [Postman](https://www.postman.com/downloads/)
#### Kiểm tra API đọc
1. Ấn vào dấu **+** để thêm 1 tab mới
- Chọn **GET** method
- Nhập URL của API đọc đã ghi lại từ bước trước
- Thay **{id}** bằng `abcd1234`
- Ấn nút **Send**

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-1.png?featherlight=false&width=90pc)

2. Kết quả trả về là toàn thông tin các tệp của người dùng có id là `abcd1234`

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-2.png?featherlight=false&width=90pc)

#### Kiểm tra API ghi
1. Tương tự tạo một tab mới
- Chọn **POST** method
- Nhập URL của API ghi đã ghi lại từ bước trước
- Trong mục **Body**, chọn **raw**
- Sao chép đoạn dưới đây:
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
- Ấn **Send**

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-3.png?featherlight=false&width=90pc)

2. Đợi một chút, xem kết quả trả về

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-4.png?featherlight=false&width=90pc)

3. Mở bảng điều khiển của **DynamoDB**, chọn **Explore items** và chọn bảng **Documents** để kiểm tra kết quả:

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-5.png?featherlight=false&width=90pc)

#### Kiểm tra API xoá
1. Thêm một tab mới để thực hiện API xoá
- Chọn **DELETE** method
- Nhập URL của API xoá dữ liệu đã ghi lại từ bước trước, thay **{id}** bằng `abcd1234`
- Trong mục **Params**, nhập `file` cho key và `flowers.png` cho value
- Ấn nút **Send**

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-6.png?featherlight=false&width=90pc)

2. Kiểm tra kết quả trả về:

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-7.png?featherlight=false&width=90pc)

3. Quay lại với bảng **Documents**, ấn nút **Refresh** để xem kết quả

![TestListAPI](/images/3-test-api-by-postman/3-test-api-by-postman-8.png?featherlight=false&width=90pc)




