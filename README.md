# ShopClassic — Modern E-Commerce Store

A full-stack e-commerce web application built with **Node.js**, **Express.js**, **MongoDB**, and **EJS** templating. Clean, modern UI with a classic black/white/blue color palette. Built as a web development internship project.

---

## Folder Structure

```
ecommerce-store/
│
├── server/
│   ├── app.js                    # Main Express app entry point
│   ├── config/
│   │   ├── db.js                 # MongoDB connection config
│   │   └── seed.js               # Database seeder (sample data)
│   ├── models/
│   │   ├── User.js               # User schema (auth, roles)
│   │   ├── Product.js            # Product schema
│   │   └── Order.js              # Order schema
│   ├── controllers/
│   │   ├── authController.js     # Register, login, logout
│   │   ├── productController.js  # List, search, detail
│   │   ├── cartController.js     # Add, update, remove cart items
│   │   ├── orderController.js    # Checkout, place order, history
│   │   └── adminController.js    # Admin CRUD + order management
│   ├── routes/
│   │   ├── index.js              # Home page
│   │   ├── auth.js               # /auth routes
│   │   ├── products.js           # /products routes
│   │   ├── cart.js               # /cart routes
│   │   ├── orders.js             # /orders routes
│   │   └── admin.js              # /admin routes
│   └── middleware/
│       └── auth.js               # isLoggedIn, isAdmin, isGuest guards
│
├── public/
│   ├── css/
│   │   └── style.css             # Main stylesheet (CSS variables, responsive)
│   ├── js/
│   │   └── main.js               # Client-side JS (nav, animations, etc.)
│   ├── images/                   # Static images
│   └── uploads/                  # User-uploaded product images
│
├── views/
│   ├── partials/
│   │   ├── header.ejs            # HTML head + navbar + flash messages
│   │   ├── footer.ejs            # Footer + scripts
│   │   ├── admin-header.ejs      # Admin layout header + sidebar
│   │   └── admin-footer.ejs      # Admin layout footer
│   ├── user/
│   │   ├── home.ejs              # Homepage (hero, featured, latest)
│   │   ├── products.ejs          # Product listing + filters
│   │   ├── product-detail.ejs    # Single product detail page
│   │   ├── cart.ejs              # Shopping cart
│   │   ├── checkout.ejs          # Checkout form
│   │   ├── order-confirmation.ejs# Order success page
│   │   ├── my-orders.ejs         # User order history
│   │   ├── login.ejs             # Login form
│   │   └── register.ejs          # Registration form
│   ├── admin/
│   │   ├── dashboard.ejs         # Admin dashboard with stats
│   │   ├── products.ejs          # Product management table
│   │   ├── add-product.ejs       # Add product form
│   │   ├── edit-product.ejs      # Edit product form
│   │   └── orders.ejs            # Order management with status update
│   └── 404.ejs                   # 404 error page
│
├── .env                          # Environment variables (not committed)
├── package.json
└── README.md
```

---

## Features

### User Features
- Browse all products with search and category filtering
- Sort by price (low/high) or name
- Product detail page with related products
- User registration and login (bcrypt password hashing)
- Session-based authentication
- Add to cart, update quantity, remove items
- Secure checkout with shipping info
- Multiple payment method options
- Order confirmation with summary
- Order history page

### Admin Features
- Admin dashboard with stats (products, orders, users, revenue)
- Add, edit, delete products with image upload
- View all customer orders
- Update order status (Pending → Processing → Shipped → Delivered)
- Protected admin routes (middleware guards)

---

## Tech Stack

| Layer      | Technology                  |
|------------|-----------------------------|
| Runtime    | Node.js                     |
| Framework  | Express.js                  |
| Database   | supabase          |
| Templating | EJS                         |
| Auth       | bcryptjs + express-session  |
| Upload     | Multer                      |
| Styling    | Custom CSS (no framework)   |
| Fonts      | Playfair Display + DM Sans  |

---

## Installation

### Prerequisites
- Node.js (v16+)
- MongoDB running locally or a MongoDB Atlas URI

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/ecommerce-store.git
cd ecommerce-store
```

**2. Install dependencies**
```bash
npm install
```

**3. Set up environment variables**

Edit the `.env` file with your values:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/ecommerce_store
SESSION_SECRET=yourSecretKeyHere
ADMIN_EMAIL=admin@store.com
ADMIN_PASSWORD=Admin@123
```

**4. Seed the database with sample data**
```bash
npm run seed
```
This creates 12 sample products and the admin user.

**5. Start the server**
```bash
# Development (with auto-reload)
npm run dev

# Production
npm start
```

**6. Open in browser**
```
http://localhost:3000
```

---

## Default Credentials

| Role  | Email              | Password   |
|-------|--------------------|------------|
| Admin | admin@store.com    | Admin@123  |

---

## API Routes

| Method | Route                         | Description              | Auth     |
|--------|-------------------------------|--------------------------|----------|
| GET    | /                             | Home page                | Public   |
| GET    | /products                     | Product listing          | Public   |
| GET    | /products/:id                 | Product detail           | Public   |
| GET    | /auth/register                | Register page            | Guest    |
| POST   | /auth/register                | Handle registration      | Guest    |
| GET    | /auth/login                   | Login page               | Guest    |
| POST   | /auth/login                   | Handle login             | Public   |
| GET    | /auth/logout                  | Logout                   | User     |
| GET    | /cart                         | View cart                | User     |
| POST   | /cart/add                     | Add to cart              | User     |
| POST   | /cart/update                  | Update cart quantity     | User     |
| GET    | /cart/remove/:id              | Remove cart item         | User     |
| GET    | /orders/checkout              | Checkout page            | User     |
| POST   | /orders/place                 | Place order              | User     |
| GET    | /orders/confirmation/:id      | Order confirmation       | User     |
| GET    | /orders/my-orders             | Order history            | User     |
| GET    | /admin/dashboard              | Admin dashboard          | Admin    |
| GET    | /admin/products               | Manage products          | Admin    |
| POST   | /admin/products/add           | Add product              | Admin    |
| PUT    | /admin/products/edit/:id      | Update product           | Admin    |
| DELETE | /admin/products/delete/:id    | Delete product           | Admin    |
| GET    | /admin/orders                 | View all orders          | Admin    |
| POST   | /admin/orders/:id/status      | Update order status      | Admin    |

---

## Screenshots

> After cloning and seeding, visit `http://localhost:3000` to see:
> - Hero section with call-to-action buttons
> - Featured product cards with hover effects
> - Responsive navigation with cart badge
> - Clean checkout flow
> - Admin dashboard with stats

---

## License

MIT License. Free to use for educational and portfolio purposes.
