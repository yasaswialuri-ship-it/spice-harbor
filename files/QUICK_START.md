# 🚀 Spice Harbor - Quick Start Guide

## 🎯 What You Got

A **complete full-stack restaurant website** with:
- ✅ Responsive modern UI with dark/light mode
- ✅ Working shopping cart system
- ✅ Payment integration (Razorpay test mode)
- ✅ Table reservation system
- ✅ Google Maps integration
- ✅ Admin dashboard (backend ready)
- ✅ AI-generated food images tool
- ✅ Complete REST API
- ✅ Database models and seeders

---

## ⚡ Fastest Way to Get Started (1 Minute!)

### Option 1: Single File Demo (No Installation)

1. **Open** `index.html` in your browser
2. **Done!** 🎉 The website is fully functional

**Features:**
- All pages working (Home, Menu, Cart, Checkout, Reservation, etc.)
- Dark/Light mode toggle
- Shopping cart with localStorage
- Responsive design
- Payment flow (test mode)
- Form validations

---

## 🎨 Generate AI Food Images

1. **Open** `generate-images.html` in your browser
2. **Click** "Generate All Images"
3. **Download** images for your menu items
4. Use them in your website!

**What gets generated:**
- 22 food item images (all menu items)
- Restaurant interior image
- Hero banner image

---

## 🏗️ Full Stack Setup (If You Want Backend)

### Prerequisites
```bash
# Install Node.js from nodejs.org (v14 or higher)
# Install MongoDB from mongodb.com OR use MongoDB Atlas (free)
```

### Step 1: Install Backend Dependencies
```bash
cd backend
npm install
```

### Step 2: Setup Environment Variables
```bash
# Copy .env.example to .env
cp ../.env.example .env

# Edit .env and add your keys:
# - MongoDB connection string
# - Razorpay test keys (from razorpay.com)
# - Google Maps API key (from console.cloud.google.com)
```

### Step 3: Seed Database
```bash
npm run seed
```

This creates:
- All 20 menu items
- Admin user (email: admin@spiceharbor.com, password: admin123)

### Step 4: Start Backend Server
```bash
npm run dev
```

Server runs on: `http://localhost:5000`

---

## 📱 Frontend Setup (React Version)

```bash
cd frontend
npm install
npm start
```

App runs on: `http://localhost:3000`

---

## 🔑 Default Login Credentials

**Admin Dashboard:**
- Email: `admin@spiceharbor.com`
- Password: `admin123`

⚠️ **Change this in production!**

---

## 📂 Project Structure

```
spice-harbor-restaurant/
│
├── index.html              ⭐ OPEN THIS - Single file demo
├── generate-images.html    ⭐ AI Image Generator
├── README.md              📖 Full documentation
├── API_DOCUMENTATION.md   📖 API endpoints guide
│
├── backend/               🔧 Node.js + Express API
│   ├── models/           💾 Database models
│   ├── routes/           🛣️ API routes
│   ├── config/           ⚙️ Configuration files
│   └── seeders/          🌱 Database seeders
│
└── frontend/             ⚛️ React application
    └── src/
        ├── components/   🧩 Reusable components
        └── pages/        📄 Page components
```

---

## 🎯 Quick Tasks

### View the Demo Website
```bash
# Just open in browser:
index.html
```

### Generate Food Images
```bash
# Open in browser:
generate-images.html
```

### Test the API
```bash
# Start backend server:
cd backend
npm run dev

# Test health endpoint:
curl http://localhost:5000/health
```

### Access Admin Features
```bash
# In the demo (index.html):
# There's no admin panel in single file version

# In full stack version:
# Navigate to: http://localhost:3000/admin/dashboard
```

---

## 🔧 API Endpoints Quick Reference

Base URL: `http://localhost:5000/api`

**Menu:**
- `GET /menu` - All items
- `GET /menu/special` - Today's special
- `POST /menu` - Add item (admin)

**Orders:**
- `POST /orders` - Create order
- `GET /orders/:orderId` - Track order

**Reservations:**
- `POST /reservations` - Book table
- `GET /reservations` - All bookings (admin)

**Payment:**
- `POST /payment/create-order` - Create payment
- `POST /payment/verify` - Verify payment

See `API_DOCUMENTATION.md` for complete details.

---

## 🎨 Customization Guide

### Change Restaurant Name
1. Edit `index.html` - Search for "Spice Harbor"
2. Replace with your restaurant name
3. Update logo text in navbar

### Change Colors
```css
/* In index.html, find the :root variables */
:root {
    --primary: #d97706;      /* Change this */
    --secondary: #dc2626;    /* And this */
}
```

### Add Menu Items
1. Open `index.html`
2. Find `menuData` array
3. Add your items:
```javascript
{ 
  id: 21, 
  name: 'Your Dish', 
  price: 299, 
  category: 'Main Course', 
  emoji: '🍛',
  available: true 
}
```

### Change Location
1. Edit Google Maps iframe src
2. Update address in Contact page
3. Change coordinates in .env

---

## 💳 Payment Gateway Setup (Test Mode)

### Razorpay (Recommended for India)
1. Sign up at https://razorpay.com/
2. Go to Dashboard → Settings → API Keys
3. Copy **Test Key ID** and **Test Key Secret**
4. Add to `.env` file
5. Use test card: `4111 1111 1111 1111`

### Stripe (Alternative)
1. Sign up at https://stripe.com/
2. Get test API keys
3. Update payment routes to use Stripe SDK
4. Use test card: `4242 4242 4242 4242`

---

## 🗺️ Google Maps Setup

1. Go to https://console.cloud.google.com/
2. Create new project
3. Enable **Maps JavaScript API**
4. Create API key
5. Add to `.env` file
6. Update iframe in Contact page

---

## 📊 Database Options

### MongoDB Atlas (Free & Easy)
1. Sign up at https://www.mongodb.com/cloud/atlas
2. Create free cluster
3. Get connection string
4. Add to `.env` as `MONGODB_URI`

### Local MongoDB
```bash
# Install MongoDB
# macOS: brew install mongodb-community
# Ubuntu: sudo apt install mongodb
# Windows: Download from mongodb.com

# Start MongoDB
mongod
```

---

## 🚀 Deployment Guide

### Deploy Demo (index.html)
**Netlify (Free):**
1. Drag & drop `index.html` to https://app.netlify.com/drop
2. Done! ✅

**Vercel:**
```bash
npm install -g vercel
vercel
```

### Deploy Full Stack

**Frontend (Netlify/Vercel):**
```bash
cd frontend
npm run build
# Deploy the build folder
```

**Backend (Railway/Render):**
1. Push code to GitHub
2. Connect repository on Railway.app or Render.com
3. Set environment variables
4. Deploy!

**Database (MongoDB Atlas):**
- Already cloud-based
- Just update connection string

---

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Kill process on port 5000
lsof -ti:5000 | xargs kill

# Or use different port in .env
PORT=5001
```

### Database Connection Error
```bash
# Check if MongoDB is running
mongod --version

# Test connection
mongo
```

### Images Not Loading
- Make sure you ran `generate-images.html`
- Check browser console for errors
- Verify file paths

---

## 📞 Support

**Documentation:**
- README.md - Complete guide
- API_DOCUMENTATION.md - API reference

**Need Help?**
- Check the code comments
- Review example responses in API docs
- Test endpoints with the seeded data

---

## ✅ Feature Checklist

- [x] Homepage with hero section
- [x] Menu page with filtering
- [x] Shopping cart
- [x] Checkout with payment
- [x] Table reservation
- [x] Contact page
- [x] Location with maps
- [x] Dark/Light mode
- [x] Mobile responsive
- [x] Toast notifications
- [x] Form validations
- [x] Admin authentication
- [x] Order management
- [x] Menu CRUD operations

---

## 🎉 You're All Set!

**Start with:**
1. Open `index.html` to see the demo
2. Generate images with `generate-images.html`
3. Set up backend when ready
4. Customize and deploy!

**Questions?** Check the README.md for detailed information!

---

**Made with ❤️ for Spice Harbor**
