#  Manage Flight API Documentation

## 🧾 Base URL  
`https://flight-booking-airline.onrender.com/api/v1/flight-core-api`

---

## 📌 1. Create Flight  
**POST** `/flights`

### 🔸 Request Body (JSON)
```json
{
  "flightNumber": "FD123",
  "airlineId": "string",
  "aircraft": "Airbus A320",
  "departureAirportId": "string",
  "arrivalAirportId": "string",
  "departureTime": "2025-08-01T08:00:00Z",
  "arrivalTime": "2025-08-01T10:00:00Z",
  "basePrice": 1500,
  "seatCapacity": 180
}
```

### 🔸 Success Response
**Status Code:** `201 Created`  
```json
{
  "status": "success",
  "code": "FLIGHT_1001",
  "message": "Flight created successfully",
  "data": { ... }
}
```

---

## 📌 2. Get All Flights  
**GET** `/flights`

### 🔸 Query Params (optional)
- `page` – (default: 1)
- `limit` – (default: 10)

### 🔸 Success Response
**Status Code:** `200 OK`  
```json
{
  "status": "success",
  "code": "FLIGHT_1004",
  "message": "Flights retrieved successfully.",
  "data": {
    "items": [ ... ],
    "pagination": { ... }
  }
}
```

---

## 📌 3. Get Flight by ID  
**GET** `/flights/{id}`

### 🔸 Path Parameter
- `id` – Flight ID

### 🔸 Success Response
**Status Code:** `200 OK`  
```json
{
  "status": "success",
  "code": "FLIGHT_1003",
  "message": "Flight retrieved successfully.",
  "data": { ... }
}
```

---

## 📌 4. Update Flight  
**PUT** `/flights/{id}`

### 🔸 Path Parameter
- `id` – Flight ID

### 🔸 Request Body
เหมือนกับ `POST /flights`

### 🔸 Success Response
**Status Code:** `200 OK`  
```json
{
  "status": "success",
  "code": "FLIGHT_1009",
  "message": "Flight updated successfully",
  "data": { ... }
}
```

---

## 📌 5. Delete Flight  
**DELETE** `/flights/{id}`

### 🔸 Path Parameter
- `id` – Flight ID

### 🔸 Success Response
**Status Code:** `200 OK`  
```json
{
  "status": "success",
  "code": "FLIGHT_1010",
  "message": "Flight deleted successfully"
}
```

---

## ❌ Error Responses (ทุก endpoint อาจส่งได้)
- `400 Bad Request` – Missing or invalid input
- `404 Not Found` – Flight not found
- `500 Internal Server Error` – Unexpected error
