# Manage Flight API Collection

This Postman collection contains a set of APIs for managing airports in a flight booking system. It includes the following endpoints:

## 🔐 Authorization
All requests require a **Bearer Token** authentication.

Set your token as an environment or collection variable:

```
token = your_jwt_token_here
```

In the Authorization tab, use:
- Auth Type: Bearer Token
- Token: `{{token}}`

---

## 📌 Base URL
Replace `{{URI}}` with the base domain.

Example:
```
{{URI}} = https://flight-booking-airline.onrender.com
```

---

## 📤 Endpoints

### ➕ Create Airport
- **POST** `/api/v1/airport-core-api/airports`
- **Body**:
```json
{
  "iataCode": "BKK123",
  "cityName": "Bangkok",
  "airportName": "Suvarnabhumi Airport",
  "country": "Thailand",
  "timezone": "Asia/Bangkok"
}
```

### 📝 Update Airport
- **PATCH** `/api/v1/airport-core-api/airports/:id`
- **Body**: Same format as POST

### ❌ Delete Airport
- **DELETE** `/api/v1/airport-core-api/airports/:id`

### 📥 Get All Airports
- **GET** `/api/v1/airport-core-api/airports`

### 📄 Get Airport By ID
- **GET** `/api/v1/airport-core-api/airports/:id`

---

## ✅ Example Test Script (Postman)
```javascript
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200);
});
```

---

## 🧪 Newman CLI (Optional)
Run this collection via CLI:
```
newman run Manage-Flight.postman_collection.json -e your_env.json
```
