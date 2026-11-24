VAYRON — Local Fashion Marketplace
VAYRON is a full-stack fashion marketplace demo designed to connect customers with local fashion sellers. It includes storefront pages, customer shopping flows, seller tools, and an admin approval workflow.
Features
Customer storefront
- Browse fashion collections and approved products
- Search products and filter by category
- View product details, sizes, colors, stock, and seller information
- Add items to a cart and update/remove cart items
- Save products to a wishlist
- Place orders with delivery address and payment method (demo checkout)
- View order history and individual order details
- Submit or update product reviews (1–5 stars)
Seller portal
- Seller registration and login
- Seller approval/verification workflow
- Seller dashboard with product and sales/order statistics
- Add products for admin review
- Edit and delete owned products
- View orders containing their products
- Public store profile with products and reviews
Admin panel
- Admin login
- View and approve/reject seller registrations
- Review and approve/reject product submissions
- View marketplace statistics
Tech Stack
- Frontend: HTML, CSS, vanilla JavaScript
- Backend: Node.js built-in http server
- Data storage: JSON file (db.json)
- Authentication: Token-based authentication with role checks
- Security helpers: Password hashing, input sanitization, request parsing helpers
- Dependencies: No external npm dependencies

Project Structure
vayron-full/
├── server.js              # HTTP server, API routes, and static file serving
├── db.json               # Local JSON database and seed data
├── package.json           # Project metadata and start script
├── start.bat             # Windows startup helper
├── CORRECTIONS.md          # Project corrections/change notes
├── lib/
│   ├── db.js             # JSON database read/write
│   ├── http.js           # HTTP utilities and API errors
│   ├── token.js          # Token creation/verification
│   ├── password.js       # Password hashing utilities
│   └── sanitize.js       # Input sanitization helpers
├── routes/                # API handlers
│   ├── auth.js
│   ├── products.js
│   ├── cart.js
│   ├── wishlist.js
│   ├── orders.js
│   ├── seller.js
│   ├── admin.js
│   ├── reviews.js
│   └── stores.js
└── public/                # Frontend pages and API bridge
    ├── homepage.html
    ├── men.html
    ├── women.html
    ├── login.html
    ├── detailprduct.html
    ├── cart.html
    ├── wishlist.html
    ├── orders.html
    ├── seller.dashboard.html
    ├── add.product.html
    ├── store-profile.html
    ├── admin.html
    ├── help.html
    └── api.js

API Overview
All API endpoints are served by the Node.js app on the same origin.

| Area | Method | Endpoint | Access |
|---|---|---|
| Customer signup | POST | /api/auth/customer/signup | Public |
| Customer login | POST | /api/auth/customer/login | Public |
| Seller signup | POST | /api/auth/seller/signup | Public |
| Seller login | POST | /api/auth/seller/login | Public |
| Admin login | POST | /api/auth/admin/login | Public |
| Product catalog | GET | /api/products | Public |
| Product details | GET | /api/products/:id | Public |
| Product reviews | GET | /api/products/:id/reviews | Public |
| Submit/update review | POST | /api/products/:id/reviews | Customer |
| Store profile | GET | /api/stores/:sellerId | Public |
| Seller products | GET | /api/products/seller/mine | Seller |
| Create product | POST | /api/products | Seller |
| Update product | PUT | /api/products/:id | Seller (owner) |
| Delete product | DELETE | /api/products/:id | Seller (owner) |
| Cart | GET/POST | /api/cart | Customer |
| Cart item | PUT/DELETE | /api/cart/:productId | Customer |
| Wishlist | GET | /api/wishlist | Customer |
| Wishlist toggle | POST | /api/wishlist/:productId | Customer |
| Place order | POST | /api/orders | Customer |
| Customer orders | GET | /api/orders | Customer |
| Order details | GET | /api/orders/:id | Customer |
| Seller profile | GET | /api/seller/profile | Seller |
| Seller orders | GET | /api/seller/orders | Seller |
| Seller stats | GET | /api/seller/dashboard-stats | Seller |
| Admin sellers | GET | /api/admin/sellers | Admin |
| Approve/reject seller | PUT | /api/admin/sellers/:id/approve or /reject | Admin |
| Admin products | GET | /api/admin/products | Admin |
| Approve/reject product | PUT | /api/admin/products/:id/approve or /reject | Admin |
| Admin stats | GET | /api/admin/stats | Admin |
