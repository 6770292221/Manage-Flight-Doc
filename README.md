## 🛡️ Authentication Flow (Login & OTP Verification)

### 🔐 1. Login to Receive OTP
Send a POST request to initiate the login process. This will trigger the system to send an OTP to the user’s email.

**Request**
```
POST /api/v1/user-core-api/auth/login
Content-Type: application/json
```

**Body**
```json
{
  "email": "aphirak_2008@hotmail.com",
  "password": "Com@sci54"
}
```

**Response**
```json
{
  "status": "success",
  "code": "OTP_1001",
  "message": "A one-time password (OTP) has been successfully sent to your email address.",
  "data": {
    "userId": "6804a760601850de6fc4ede9",
    "email": "aphirak_2008@hotmail.com"
  }
}
```

---

### ✅ 2. Verify OTP to Receive Bearer Token
Send the received OTP and `userId` to this endpoint to get your `token`.

**Request**
```
POST /api/v1/user-core-api/auth/email-otp/verify
Content-Type: application/json
```

**Body**
```json
{
  "userId": "6804a760601850de6fc4ede9",
  "otp": "123456"
}
```

**Response**
```json
{
  "status": "success",
  "message": "OTP verified successfully.",
  "data": {
    "token": "<YOUR_BEARER_TOKEN>",
    "userId": "6804a760601850de6fc4ede9",
    "email": "aphirak_2008@hotmail.com",
    "isAdmin": true,
    "verified": true
  }
}
```

---

### 📌 Using the Token
Once you have the `token`, include it as a Bearer Token in the **Authorization** header in subsequent requests.

**Header Example**
```
Authorization: Bearer <YOUR_BEARER_TOKEN>
```
