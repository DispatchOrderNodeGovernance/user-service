# user-service

Dựa trên mô tả của bạn, dưới đây là bản phác thảo cơ bản của các API cho "User Service" (Dịch vụ Người Dùng), bao gồm các chức năng quản lý thông tin cho cả khách hàng và tài xế. Các API này sẽ hỗ trợ các hoạt động như đăng ký, đăng nhập, cập nhật thông tin cá nhân, và quản lý điểm thưởng.

### 1. Đăng ký (Registration)

#### POST /users/register
Cho phép người dùng đăng ký một tài khoản mới.

**Request Body:**
```json
{
  "username": "string",
  "password": "string",
  "email": "string",
  "phone": "string",
  "role": "customer | driver"  // loại tài khoản: khách hàng hoặc tài xế
}
```

**Response:**
```json
{
  "success": true,
  "message": "User registered successfully.",
  "userId": "string"
}
```

### 2. Đăng nhập (Login)

#### POST /users/login
Cho phép người dùng đăng nhập vào hệ thống.

**Request Body:**
```json
{
  "username": "string",
  "password": "string"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Login successful.",
  "token": "string"  // Token được sử dụng cho xác thực các yêu cầu sau này
}
```

### 3. Cập nhật thông tin cá nhân (Update Profile)

#### PUT /users/{userId}/profile
Cho phép người dùng cập nhật thông tin cá nhân của họ.

**Request Body:**
```json
{
  "email": "string",
  "phone": "string",
  "name": "string",
  "address": "string"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Profile updated successfully."
}
```

### 4. Quản lý điểm thưởng (Manage Rewards)

#### GET /users/{userId}/rewards
Truy vấn điểm thưởng hiện có của người dùng.

**Response:**
```json
{
  "success": true,
  "points": 100  // số điểm thưởng hiện có
}
```

#### POST /users/{userId}/rewards/earn
Cộng điểm thưởng cho người dùng (thường do hoàn thành hành trình hoặc đạt mục tiêu nhất định).

**Request Body:**
```json
{
  "points": 10
}
```

**Response:**
```json
{
  "success": true,
  "message": "Rewards added successfully."
}
```

#### POST /users/{userId}/rewards/redeem
Dùng điểm thưởng để đổi lấy dịch vụ hoặc sản phẩm.

**Request Body:**
```json
{
  "points": 20
}
```

**Response:**
```json
{
  "success": true,
  "message": "Rewards redeemed successfully."
}
```

Các API trên cần được bảo mật và quản lý phù hợp, đảm bảo tuân thủ các quy định về bảo mật dữ liệu cá nhân. Bạn có thể mở rộng hoặc điều chỉnh các API này tùy theo nhu cầu cụ thể của dự án và yêu cầu từ phía người dùng cuối.
