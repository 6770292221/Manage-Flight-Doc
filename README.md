# ✈️ Manage Flight API Documentation

This document provides detailed information on how to use the **Manage Flight API**, including endpoints for creating, retrieving, updating, and deleting airport data using Postman.

---

## 🌐 Base URL

```
{{URI}}/api/v1/airport-core-api/airports
```

Environment Variable:
- `{{URI}}` = Base URL (e.g., `https://flight-booking-airline.onrender.com`)
- `{{token}}` = Bearer token used in Authorization header

---

## 🔐 Authentication

All endpoints require Bearer Token authentication.

In Postman:
- Go to `Authorization` tab
- Set **Auth Type** to `Bearer Token`
- Token: `{{token}}`

Postman will automatically insert the token as:

```
Authorization: Bearer {{token}}
```

---

## 📬 Endpoints

### 1. ➕ Create Airport

**POST** `/airports`

- **Headers**: `Authorization: Bearer {{token}}`
- **Body (JSON)**:
```json
{
  "iataCode": "BKK{{randomInt}}",
  "cityName": "Bangkok",
  "airportName": "Suvarnabhumi Airport",
  "country": "Thailand",
  "timezone": "Asia/Bangkok"
}
```

- **Response**:
```json
{
  "status": "success",
  "code": "AIR_1007",
  "message": "Airport created successfully",
  "data": {
    "_id": "string",
    ...
  }
}
```

---

### 2. 📖 Get All Airports

**GET** `/airports`

- **Headers**: `Authorization: Bearer {{token}}`

- **Response**:
```json
{
  "status": "success",
  "code": "AIR_1004",
  "message": "Airports retrieved successfully.",
  "data": {
    "items": [ ... ]
  }
}
```

---

### 3. 🔍 Get Airport by ID

**GET** `/airports/:id`

- **Headers**: `Authorization: Bearer {{token}}`

- **Response**:
```json
{
  "status": "success",
  "code": "AIR_1003",
  "message": "Airport retrieved successfully.",
  "data": { ... }
}
```

---

### 4. 📝 Update Airport

**PATCH** `/airports/:id`

- **Headers**: `Authorization: Bearer {{token}}`
- **Body (JSON)**:
```json
{
  "iataCode": "BKK411",
  "cityName": "Bangkok",
  "airportName": "Suvarnabhumi Airport",
  "country": "Thailand",
  "timezone": "Asia/Bangkok"
}
```

- **Response**:
```json
{
  "status": "success",
  "code": "AIR_1009",
  "message": "Airport updated successfully",
  "data": { ... }
}
```

---

### 5. ❌ Delete Airport

**DELETE** `/airports/:id`

- **Headers**: `Authorization: Bearer {{token}}`

- **Response**:
```json
{
  "status": "success",
  "code": "AIR_1010",
  "message": "Airport deleted successfully"
}
```

---

## 🚀 Running Tests with Newman

To run the collection via Newman CLI:

```bash
newman run Manage-Flight.postman_collection.json -e environment.json
```

Ensure `environment.json` contains variables for `{{URI}}` and `{{token}}`.

---

## 🧪 Common Postman Tests (Example)

```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Airport data is correct", function () {
    const res = pm.response.json();
    pm.expect(res.data.iataCode).to.match(/^BKK\d+$/);
});
```

---

## 📌 Notes

- Make sure you set `{{token}}` variable in your environment.
- Use `{{$randomInt}}` for generating random values in Postman body if needed.
- Set and retrieve dynamic data like `_id` using `pm.environment.set()`.

---

© 2025 Manage Flight API - For demo/testing purposes.
