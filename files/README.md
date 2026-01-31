# 🍴 Spice Harbor - Multicuisine Restaurant Website

A complete full-stack restaurant website with cart system, payment integration (test mode), table reservation, map integration, and AI-generated food images.

## 🌟 Features

### Frontend Features
- ✅ Modern, responsive design with dark/light mode
- ✅ Smooth animations and transitions
- ✅ Hero section with floating food elements
- ✅ Dynamic menu with category filtering
- ✅ Shopping cart with quantity controls
- ✅ Today's Special section
- ✅ Table reservation system
- ✅ Contact page with Google Maps integration
- ✅ About Us page
- ✅ Floating cart button with live count
- ✅ Toast notifications
- ✅ Mobile responsive

### Backend Features (Ready to Implement)
- ✅ RESTful API architecture
- ✅ MongoDB/PostgreSQL database ready
- ✅ JWT authentication for admin
- ✅ Order management
- ✅ Reservation management
- ✅ Menu CRUD operations
- ✅ Payment gateway integration (Razorpay/Stripe test mode)

## 🚀 Quick Start

### Option 1: Single File Demo (Fastest)
1. Open `index.html` in any modern web browser
2. No installation required!
3. Fully functional demo with all features

### Option 2: Full Stack Setup

#### Prerequisites
- Node.js (v14 or higher)
- MongoDB or PostgreSQL
- Git

#### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/spice-harbor.git
cd spice-harbor

# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install
```

#### Environment Setup

Create `.env` file in the backend directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/spiceharbor
# OR for PostgreSQL
DATABASE_URL=postgresql://user:password@localhost:5432/spiceharbor

# JWT Secret
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production

# Payment Gateway (Test Mode)
RAZORPAY_KEY_ID=rzp_test_xxxxxxxxxxxxxxxx
RAZORPAY_KEY_SECRET=your_razorpay_secret_key

# Google Maps API
GOOGLE_MAPS_API_KEY=your_google_maps_api_key

# Email Configuration (Optional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password

# Frontend URL
FRONTEND_URL=http://localhost:3000
```

#### Running the Application

**Backend:**
```bash
cd backend
npm run dev
# Server runs on http://localhost:5000
```

**Frontend:**
```bash
cd frontend
npm start
# App runs on http://localhost:3000
```

## 📁 Project Structure

```
spice-harbor-restaurant/
├── index.html                  # Single-file demo version
├── generate-images.html        # AI image generator tool
├── README.md
├── .env.example
│
├── frontend/
│   ├── public/
│   │   ├── index.html
│   │   └── images/
│   │       └── (AI-generated food images)
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx
│   │   │   ├── Footer.jsx
│   │   │   ├── FloatingCart.jsx
│   │   │   └── MenuCard.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── Menu.jsx
│   │   │   ├── TodaysSpecial.jsx
│   │   │   ├── About.jsx
│   │   │   ├── Cart.jsx
│   │   │   ├── Checkout.jsx
│   │   │   ├── Reservation.jsx
│   │   │   ├── Contact.jsx
│   │   │   ├── Location.jsx
│   │   │   ├── AdminLogin.jsx
│   │   │   └── AdminDashboard.jsx
│   │   ├── App.jsx
│   │   ├── App.css
│   │   └── index.js
│   ├── package.json
│   └── .gitignore
│
└── backend/
    ├── config/
    │   ├── database.js
    │   └── razorpay.js
    ├── models/
    │   ├── User.js
    │   ├── MenuItem.js
    │   ├── Order.js
    │   └── Reservation.js
    ├── routes/
    │   ├── auth.js
    │   ├── menu.js
    │   ├── orders.js
    │   └── reservations.js
    ├── middleware/
    │   ├── auth.js
    │   └── errorHandler.js
    ├── controllers/
    │   ├── authController.js
    │   ├── menuController.js
    │   ├── orderController.js
    │   └── reservationController.js
    ├── server.js
    ├── package.json
    └── .gitignore
```

## 🎨 AI Image Generator

1. Open `generate-images.html` in your browser
2. Click "Generate All Images"
3. Download generated images for use in your website
4. Images include:
   - All menu items (22 items)
   - Restaurant interior
   - Hero banner

## 📊 Menu Data

### Categories
- **Starters**: Veg Manchurian, Paneer 65, Chicken Lollipop, Crispy Corn
- **Main Course**: Butter Chicken, Paneer Butter Masala, Veg Kadai, Chicken Curry
- **Biryani**: Chicken Dum, Mutton, Veg, Egg
- **Fast Food**: Pizza, Burger, Pasta, Fries
- **Beverages**: Cold Coffee, Lime Soda, Mojito, Soft Drinks

## 🔐 Admin Dashboard

**Access:** `/admin/dashboard`

**Default Credentials:**
- Username: `admin@spiceharbor.com`
- Password: `admin123` (Change in production!)

**Features:**
- Add/Edit/Delete menu items
- View and manage orders
- View and manage reservations
- Update Today's Special items
- Enable/Disable menu items
- Update prices

## 💳 Payment Integration

### Razorpay Test Mode Setup
1. Sign up at https://razorpay.com/
2. Get test API keys from dashboard
3. Add keys to `.env` file
4. Test cards:
   - Card: 4111 1111 1111 1111
   - CVV: Any 3 digits
   - Expiry: Any future date

### Stripe Alternative
```bash
npm install stripe
```
Update payment controller to use Stripe SDK

## 🗺️ Google Maps Integration

1. Get API key from [Google Cloud Console](https://console.cloud.google.com/)
2. Enable Maps JavaScript API
3. Add key to `.env`
4. Location: Madhapur, Hyderabad (17.4483°N, 78.3915°E)

## 📱 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/admin-login` - Admin login

### Menu
- `GET /api/menu` - Get all menu items
- `GET /api/menu/:id` - Get specific item
- `POST /api/menu` - Add new item (Admin)
- `PUT /api/menu/:id` - Update item (Admin)
- `DELETE /api/menu/:id` - Delete item (Admin)
- `GET /api/menu/special` - Get today's special

### Orders
- `POST /api/orders` - Create new order
- `GET /api/orders` - Get all orders (Admin)
- `GET /api/orders/:id` - Get specific order
- `PUT /api/orders/:id` - Update order status (Admin)

### Reservations
- `POST /api/reservations` - Create reservation
- `GET /api/reservations` - Get all reservations (Admin)
- `PUT /api/reservations/:id` - Update reservation (Admin)

### Payments
- `POST /api/payment/create-order` - Create Razorpay order
- `POST /api/payment/verify` - Verify payment

## 🎯 Features Checklist

- [x] Responsive design
- [x] Dark/Light mode
- [x] Shopping cart
- [x] Menu filtering
- [x] Table reservation
- [x] Contact form
- [x] Google Maps
- [x] Payment gateway (test)
- [x] AI-generated images
- [x] Admin dashboard ready
- [x] Order management ready
- [x] Database schema ready

## 🛠️ Tech Stack

### Frontend
- React 18
- React Router
- CSS3 with animations
- Font Awesome icons
- Google Fonts (Playfair Display, Inter)

### Backend
- Node.js
- Express.js
- MongoDB/PostgreSQL
- JWT for authentication
- Razorpay/Stripe SDK

### Tools
- Canvas API for image generation
- LocalStorage for cart persistence

## 📦 Dependencies

### Frontend
```json
{
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "react-router-dom": "^6.15.0"
}
```

### Backend
```json
{
  "express": "^4.18.2",
  "mongoose": "^7.4.0",
  "jsonwebtoken": "^9.0.2",
  "bcryptjs": "^2.4.3",
  "dotenv": "^16.3.1",
  "cors": "^2.8.5",
  "razorpay": "^2.9.1"
}
```

## 🚢 Deployment

### Frontend (Netlify/Vercel)
```bash
npm run build
# Deploy the build folder
```

### Backend (Heroku/Railway/Render)
```bash
# Set environment variables on platform
# Deploy from GitHub repository
```

### Database
- MongoDB Atlas (Free tier available)
- Or PostgreSQL on Railway/Supabase

## 🔒 Security Notes

- Change default admin credentials
- Use strong JWT secrets
- Enable CORS only for your domain
- Use HTTPS in production
- Never commit `.env` files
- Sanitize user inputs
- Rate limit API endpoints

## 📈 Future Enhancements

- [ ] Real-time order tracking
- [ ] User authentication and profiles
- [ ] Order history
- [ ] Loyalty points system
- [ ] Multi-language support
- [ ] Social media integration
- [ ] SMS notifications
- [ ] Push notifications
- [ ] Analytics dashboard
- [ ] Review and rating system

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License.

## 👨‍💻 Author

**Your Name**
- Website: [spiceharbor.com](https://spiceharbor.com)
- Email: info@spiceharbor.com
- Phone: +91 9876543210

## 🙏 Acknowledgments

- Design inspiration from modern restaurant websites
- Icons by Font Awesome
- Fonts by Google Fonts

## 📞 Support

For support, email support@spiceharbor.com or create an issue in the repository.

---

**Made with ❤️ by Spice Harbor Team**
