# Manage Flight API Documentation (Full Version)

## 🧾 Base URL

```
https://flight-booking-airline.onrender.com/api/v1
```

---

## ✈️ Airport API Endpoints

### 1. Create Airport

**POST** `/airport-core-api/airports`

**Request Body**
```json
{
  "iataCode": "BKK753",
  "cityName": "Bangkok",
  "airportName": "Suvarnabhumi Airport",
  "country": "Thailand",
  "timezone": "Asia/Bangkok"
}
```

**Success Response**
```json
{
  "status": "success",
  "code": "AIR_1007",
  "message": "Airport created successfully",
  "data": {
    "_id": "xxxxx",
    ...
  }
}
```

---

### 2. Get All Airports

**GET** `/airport-core-api/airports`

**Success Response**
```json
{
  "status": "success",
  "code": "AIR_1004",
  "message": "Airports retrieved successfully.",
  "data": {
    "items": [...]
  }
}
```

---

### 3. Get Airport by ID

**GET** `/airport-core-api/airports/:id`

**Success Response**
```json
{
  "id": "xxxxx",
  "iataCode": "...",
  ...
}
```

---

### 4. Update Airport

**PATCH** `/airport-core-api/airports/:id`

**Request Body**
```json
{
  "iataCode": "BKK411",
  "cityName": "Bangkok",
  "airportName": "Suvarnabhumi Airport",
  "country": "Thailand",
  "timezone": "Asia/Bangkok"
}
```

**Success Response**
```json
{
  "status": "success",
  "code": "AIR_1009",
  "message": "Airport updated successfully",
  "data": { ... }
}
```

---

### 5. Delete Airport

**DELETE** `/airport-core-api/airports/:id`

**Success Response**
```json
{
  "status": "success",
  "code": "AIR_1010",
  "message": "Airport deleted successfully"
}
```

---

## 🔐 Authentication Flow (Login + OTP)

### 1. Login

**POST** `/user-core-api/auth/login`

**Request Body**
```json
{
  "email": "aphirak_2008@hotmail.com",
  "password": "Com@sci54"
}
```

**Success Response**
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

### 2. Verify OTP

**POST** `/user-core-api/auth/email-otp/verify`

**Request Body**
```json
{
  "userId": "6804a760601850de6fc4ede9",
  "otp": "123456"
}
```

**Success Response**
```json
{
  "status": "success",
  "message": "OTP verified successfully.",
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9....",
    "userId": "6804a760601850de6fc4ede9",
    "email": "aphirak_2008@hotmail.com",
    "isAdmin": true,
    "verified": true
  }
}
```

You can use this `token` in Authorization header for the Airport APIs.

---

## 🛡 Authorization Header Format

For secured endpoints (POST, PATCH, DELETE), set header:

```
Authorization: Bearer <token>
```

Example:
```bash
curl --request GET   --url https://flight-booking-airline.onrender.com/api/v1/airport-core-api/airports   --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIs...'
```
