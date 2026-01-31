# Spice Harbor API Documentation

Base URL: `http://localhost:5000/api`

## Authentication

All admin routes require JWT token in the Authorization header:
```
Authorization: Bearer <your-jwt-token>
```

---

## Authentication Endpoints

### Register User
**POST** `/auth/register`

Request Body:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123",
  "phone": "+919876543210"
}
```

Response:
```json
{
  "success": true,
  "data": {
    "id": "user_id",
    "name": "John Doe",
    "email": "john@example.com",
    "token": "jwt_token_here"
  }
}
```

### Login User
**POST** `/auth/login`

Request Body:
```json
{
  "email": "john@example.com",
  "password": "password123"
}
```

### Admin Login
**POST** `/auth/admin-login`

Request Body:
```json
{
  "email": "admin@spiceharbor.com",
  "password": "admin123"
}
```

---

## Menu Endpoints

### Get All Menu Items
**GET** `/menu`

Query Parameters:
- `category` (optional): Filter by category
- `available` (optional): true/false
- `featured` (optional): true/false

Example: `/menu?category=Biryani&available=true`

Response:
```json
{
  "success": true,
  "count": 20,
  "data": [
    {
      "_id": "item_id",
      "name": "Chicken Dum Biryani",
      "price": 279,
      "category": "Biryani",
      "emoji": "🍚",
      "available": true,
      "featured": true,
      "veg": false,
      "spicyLevel": 3
    }
  ]
}
```

### Get Today's Special
**GET** `/menu/special`

Returns all featured menu items.

### Get Single Menu Item
**GET** `/menu/:id`

### Create Menu Item (Admin)
**POST** `/menu`

Request Body:
```json
{
  "name": "Special Fried Rice",
  "price": 199,
  "category": "Main Course",
  "emoji": "🍚",
  "veg": true,
  "spicyLevel": 2,
  "available": true,
  "featured": false
}
```

### Update Menu Item (Admin)
**PUT** `/menu/:id`

### Delete Menu Item (Admin)
**DELETE** `/menu/:id`

### Toggle Item Availability (Admin)
**PATCH** `/menu/:id/toggle-availability`

---

## Order Endpoints

### Create Order
**POST** `/orders`

Request Body:
```json
{
  "customer": {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "+919876543210",
    "address": {
      "street": "123 Main St",
      "city": "Hyderabad",
      "state": "Telangana",
      "pincode": "500081"
    }
  },
  "items": [
    {
      "menuItem": "item_id",
      "name": "Chicken Biryani",
      "price": 279,
      "quantity": 2
    }
  ],
  "subtotal": 558,
  "gst": 27.9,
  "deliveryCharge": 40,
  "total": 625.9,
  "paymentMethod": "upi",
  "orderType": "delivery"
}
```

Response:
```json
{
  "success": true,
  "data": {
    "orderId": "SH12345678",
    "customer": {...},
    "items": [...],
    "total": 625.9,
    "orderStatus": "placed",
    "createdAt": "2024-01-31T10:30:00.000Z"
  }
}
```

### Get All Orders (Admin)
**GET** `/orders`

Query Parameters:
- `status`: Filter by order status
- `email`: Filter by customer email
- `limit`: Number of results (default: 50)

### Get Single Order
**GET** `/orders/:id`

### Track Order
**GET** `/orders/tracking/:orderId`

Example: `/orders/tracking/SH12345678`

### Update Order Status (Admin)
**PUT** `/orders/:id/status`

Request Body:
```json
{
  "orderStatus": "preparing"
}
```

Status Options: `placed`, `confirmed`, `preparing`, `out-for-delivery`, `delivered`, `cancelled`

### Get Order Statistics (Admin)
**GET** `/orders/stats/summary`

Response:
```json
{
  "success": true,
  "data": {
    "totalOrders": 150,
    "todayOrders": 12,
    "totalRevenue": 45000,
    "statusBreakdown": [
      { "_id": "delivered", "count": 100 },
      { "_id": "preparing", "count": 5 }
    ]
  }
}
```

---

## Reservation Endpoints

### Create Reservation
**POST** `/reservations`

Request Body:
```json
{
  "customer": {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "+919876543210"
  },
  "date": "2024-02-15",
  "time": "19:30",
  "guests": 4,
  "specialRequests": "Window seat preferred",
  "occasion": "anniversary"
}
```

Response:
```json
{
  "success": true,
  "data": {
    "reservationId": "RSV12345678",
    "customer": {...},
    "date": "2024-02-15",
    "time": "19:30",
    "guests": 4,
    "status": "pending"
  },
  "message": "Reservation created successfully"
}
```

### Get All Reservations (Admin)
**GET** `/reservations`

Query Parameters:
- `status`: Filter by status
- `date`: Filter by date (YYYY-MM-DD)
- `limit`: Number of results (default: 100)

### Get Single Reservation
**GET** `/reservations/:id`

### Track Reservation
**GET** `/reservations/tracking/:reservationId`

### Update Reservation (Admin)
**PUT** `/reservations/:id`

### Update Reservation Status (Admin)
**PATCH** `/reservations/:id/status`

Request Body:
```json
{
  "status": "confirmed"
}
```

Status Options: `pending`, `confirmed`, `cancelled`, `completed`, `no-show`

### Cancel Reservation
**DELETE** `/reservations/:id`

### Get Reservation Statistics (Admin)
**GET** `/reservations/stats/summary`

---

## Payment Endpoints

### Create Razorpay Order
**POST** `/payment/create-order`

Request Body:
```json
{
  "amount": 625.9,
  "currency": "INR",
  "receipt": "order_receipt_123"
}
```

Response:
```json
{
  "success": true,
  "data": {
    "orderId": "order_xyz123",
    "amount": 62590,
    "currency": "INR",
    "key": "rzp_test_xxxxxxxx"
  }
}
```

### Verify Payment
**POST** `/payment/verify`

Request Body:
```json
{
  "razorpay_order_id": "order_xyz123",
  "razorpay_payment_id": "pay_abc456",
  "razorpay_signature": "signature_string"
}
```

### Test Payment (Development Only)
**POST** `/payment/test-payment`

Request Body:
```json
{
  "amount": 625.9
}
```

### Get Payment Details (Admin)
**GET** `/payment/:paymentId`

### Create Refund (Admin)
**POST** `/payment/refund`

Request Body:
```json
{
  "paymentId": "pay_abc456",
  "amount": 625.9
}
```

---

## Error Responses

All endpoints return errors in this format:

```json
{
  "success": false,
  "message": "Error description here"
}
```

Common HTTP Status Codes:
- `200` - Success
- `201` - Created
- `400` - Bad Request
- `401` - Unauthorized
- `404` - Not Found
- `500` - Server Error

---

## Rate Limiting

- No rate limiting in development
- Production: 100 requests per 15 minutes per IP

---

## Testing with Postman/Thunder Client

Import this collection to test all endpoints:

1. Set base URL as environment variable: `{{base_url}}`
2. Value: `http://localhost:5000/api`
3. Import the API endpoints
4. For authenticated routes, add token to headers

---

## Notes

- All timestamps are in ISO 8601 format
- Amounts are in INR
- Phone numbers should include country code
- Dates should be in YYYY-MM-DD format
- Times should be in HH:MM format (24-hour)
