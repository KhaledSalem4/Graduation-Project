# Node.js E-Commerce API

## 📱 Project Overview

**Node.js E-Commerce API v1.0** is a robust, scalable REST API for a complete e-commerce platform. Built with Express.js and MongoDB, this API handles product management, user authentication, category management, reviews, and order processing. The application follows industry best practices with proper middleware implementation, error handling, and security measures.

---

## 🎯 Key Features

### 🔐 Authentication & Authorization
- User registration and login with JWT tokens
- Password hashing using bcrypt
- Role-based access control
- Token validation middleware
- Secure session management

### 📦 Product Management
- Complete CRUD operations for products
- Product categorization and subcategories
- Product filtering and search functionality
- Product ratings and reviews system
- Stock management
- Product image handling

### 🏪 Category Management
- Main categories and subcategories
- Category hierarchy
- Category-based product filtering
- Category metadata

### ⭐ Review & Rating System
- User reviews and ratings for products
- Review moderation
- Average rating calculation
- Review pagination

### 🛒 Shopping Features
- Shopping cart management
- Order management
- Order history
- Payment integration (Stripe support)
- Order status tracking

### 👥 User Management
- User profile management
- User authentication
- Password reset functionality
- User preferences
- Address management

---

## 🛠️ Tech Stack

### Backend Technologies
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **JWT** - Authentication tokens
- **Bcrypt** - Password hashing
- **Stripe** - Payment processing

### Middleware & Tools
- **Express Async Handler** - Async error handling
- **Express Rate Limit** - API rate limiting
- **Express Validator** - Input validation
- **Compression** - Response compression
- **CORS** - Cross-Origin Resource Sharing
- **Morgan** - HTTP request logging
- **Multer** - File upload handling
- **Sharp** - Image processing
- **Nodemailer** - Email notifications

### Development Tools
- **Nodemon** - Auto-restart on file changes
- **ESLint** - Code linting
- **Prettier** - Code formatting

---

## 📋 Project Structure

```
Graduation-Project/
├── config/              # Configuration files
│   ├── database.js      # MongoDB connection
│   └── config.env       # Environment variables
├── middlewares/         # Express middleware
│   ├── errorMiddleware.js
│   ├── authMiddleware.js
│   └── validationMiddleware.js
├── models/              # Mongoose schemas
│   ├── User.js
│   ├── Product.js
│   ├── Category.js
│   ├── SubCategory.js
│   ├── Review.js
│   └── Order.js
├── routes/              # API route definitions
│   ├── authRoute.js
│   ├── productRoute.js
│   ├── categoryRoute.js
│   ├── subCategoryRoute.js
│   ├── reviewRoute.js
│   ├── userRoute.js
│   └── index.js
├── services/            # Business logic
│   ├── productService.js
│   ├── userService.js
│   ├── orderService.js
│   └── paymentService.js
├── utils/               # Helper functions
│   ├── validators.js
│   ├── errorHandler.js
│   └── apiFeatures.js
├── server.js            # Entry point
├── package.json         # Dependencies
├── package-lock.json    # Lock file
├── .gitignore           # Git ignore rules
└── README.md            # Documentation
```

---

## 🚀 API Endpoints

### Authentication Routes (`/api/auth`)
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `POST /api/auth/forgotPassword` - Request password reset
- `PUT /api/auth/resetPassword/:token` - Reset password

### Product Routes (`/api/products`)
- `GET /api/products` - Get all products with filtering
- `GET /api/products/:id` - Get product details
- `POST /api/products` - Create new product (Admin)
- `PUT /api/products/:id` - Update product (Admin)
- `DELETE /api/products/:id` - Delete product (Admin)

### Category Routes (`/api/categories`)
- `GET /api/categories` - Get all categories
- `GET /api/categories/:id` - Get category details
- `POST /api/categories` - Create category (Admin)
- `PUT /api/categories/:id` - Update category (Admin)
- `DELETE /api/categories/:id` - Delete category (Admin)

### SubCategory Routes (`/api/subcategories`)
- `GET /api/subcategories` - Get all subcategories
- `POST /api/subcategories` - Create subcategory (Admin)
- `PUT /api/subcategories/:id` - Update subcategory (Admin)
- `DELETE /api/subcategories/:id` - Delete subcategory (Admin)

### Review Routes (`/api/reviews`)
- `GET /api/reviews` - Get all reviews
- `POST /api/reviews` - Create review
- `PUT /api/reviews/:id` - Update review
- `DELETE /api/reviews/:id` - Delete review

### User Routes (`/api/users`)
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update user profile
- `GET /api/users` - Get all users (Admin)
- `DELETE /api/users/:id` - Delete user (Admin)

---

## 🔧 Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- NPM or Yarn
- MongoDB (local or Atlas)
- Git

### Installation Steps

```bash
# Clone the repository
git clone https://github.com/KhaledSalem4/Graduation-Project.git

# Navigate to project directory
cd Graduation-Project

# Install dependencies
npm install

# Create .env file in root directory
cp config/config.env .env

# Configure environment variables
# Edit .env with your MongoDB URI and other configs

# Start development server with nodemon
npm run start:dev

# Start production server
NODE_ENV=production npm start

# The API will be available at http://localhost:3000
```

---

## ⚙️ Configuration

Create a `.env` file in the root directory with the following variables:

```env
# Server
PORT=3000
NODE_ENV=development

# Database
DB_URI=mongodb://localhost:27017/ecommerce
DB_NAME=ecommerce

# JWT
JWT_SECRET=your_jwt_secret_key_here
JWT_EXPIRE=7d
JWT_COOKIE_EXPIRE=7

# Email Configuration
SMTP_HOST=smtp.gmail.com
SMTP_PORT=465
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_app_password

# Payment Gateway (Stripe)
STRIPE_API_KEY=your_stripe_api_key
STRIPE_SECRET_KEY=your_stripe_secret_key

# Cloudinary (for image upload)
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_KEY=your_cloudinary_key
CLOUDINARY_SECRET=your_cloudinary_secret

# Admin Email
ADMIN_EMAIL=admin@ecommerce.com
```

---

## 📊 Database Models

### User Schema
- name, email, password
- phone, address
- role (user/admin)
- profilePicture
- isActive, createdAt, updatedAt

### Product Schema
- name, description, price
- category, subcategory
- images, stock
- rating, reviews
- createdAt, updatedAt

### Category Schema
- name, description
- icon, slug
- createdAt, updatedAt

### Order Schema
- user, products
- totalPrice, paymentStatus
- orderStatus, deliveryDate
- createdAt, updatedAt

### Review Schema
- product, user
- rating, comment
- createdAt, updatedAt

---

## 🔒 Security Features

- ✅ JWT-based authentication
- ✅ Password hashing with bcrypt
- ✅ CORS enabled for specific origins
- ✅ Rate limiting on API endpoints
- ✅ Input validation and sanitization
- ✅ SQL/NoSQL injection prevention
- ✅ XSS protection
- ✅ HTTPS ready
- ✅ Environment variable protection

---

## 🧪 Testing

### Manual Testing with Postman
1. Import the API collection in Postman
2. Configure environment variables
3. Run requests against localhost:3000

### API Documentation
- Full API documentation available at `/api/docs` (if Swagger is integrated)

---

## 📈 Performance Optimization

- ✅ Database indexing on frequently queried fields
- ✅ Response compression using gzip
- ✅ Pagination for large datasets
- ✅ Caching strategies
- ✅ Async/await for non-blocking operations
- ✅ Rate limiting to prevent abuse

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow existing code style
- Write meaningful commit messages
- Test your changes thoroughly
- Update documentation as needed

---

## 📝 Future Enhancements

- [ ] Admin dashboard frontend
- [ ] Advanced analytics and reporting
- [ ] Recommendation engine using ML
- [ ] Real-time notifications with WebSocket
- [ ] Multi-language support (i18n)
- [ ] Mobile app integration
- [ ] Inventory management system
- [ ] Affiliate program
- [ ] SMS notifications
- [ ] Advanced search with Elasticsearch
- [ ] Wishlist functionality
- [ ] Product comparison feature

---

## 🐛 Bug Reports

Found a bug? Please open an issue on GitHub with:
- Description of the bug
- Steps to reproduce
- Expected behavior
- Actual behavior
- Screenshots (if applicable)

---

## 📄 License

This project is open source and available under the ISC License.

---

## 👨‍💻 Author

**Khaled Salem**
- GitHub: [@KhaledSalem4](https://github.com/KhaledSalem4)
- Email: khaledmostafa4044@gmail.com
- Location: Port Said, Egypt

---

## 📞 Support

For support and questions:
- Open an issue on GitHub
- Email: khaledmostafa4044@gmail.com
- Check the documentation wiki

---

## 🙏 Acknowledgments

- Express.js team for the excellent framework
- MongoDB for the database
- Stripe for payment processing
- All open-source contributors
- Community feedback and support

---

**Last Updated:** January 5, 2026
**Version:** 1.0.0
**Status:** Active Development
