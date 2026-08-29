# README - G.A Clothing Brand App

A modern, full-featured e-commerce application for the G.A clothing brand with advanced filtering, product reviews, admin dashboard, search functionality, wishlist system, and Stripe payment integration.

[![CI/CD Pipeline](https://github.com/ghoasshah/ga-clothing-brand-app/actions/workflows/deploy.yml/badge.svg)](https://github.com/ghoasshah/ga-clothing-brand-app/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🚀 Quick Start

### With Docker (Recommended)
```bash
# Clone repository
git clone https://github.com/ghoasshah/ga-clothing-brand-app.git
cd ga-clothing-brand-app

# Setup environment
cp .env.docker .env
# Edit .env with your configuration

# Start application
docker-compose up -d

# Access application
# Frontend: http://localhost:3000
# Backend API: http://localhost:5000
```

### Without Docker
```bash
# Backend
cd backend
npm install
npm run dev

# Frontend (in another terminal)
cd frontend
npm install
npm start
```

## 📋 Project Structure

```
ga-clothing-brand-app/
├── frontend/                 # React frontend application
│   ├── src/
│   │   ├── pages/           # Page components
│   │   ├── components/      # Reusable components
│   │   ├── redux/           # State management
│   │   └── App.js
│   ├── Dockerfile
│   └── package.json
├── backend/                  # Node.js/Express API
│   ├── routes/              # API routes
│   ├── models/              # Database models
│   ├── server.js
│   ├── Dockerfile
│   └── package.json
├── docker-compose.yml       # Multi-container configuration
├── nginx.conf              # Reverse proxy configuration
├── .github/workflows/      # CI/CD pipelines
└── docs/                   # Documentation
    ├── DEPLOYMENT.md       # Deployment guide
    ├── FEATURES.md         # Feature documentation
    ├── API.md              # API reference
    └── SETUP.md            # Setup instructions
```

## ✨ Features

### 🛍️ Shopping Features
- **Product Catalog**: Browse products with images and details
- **Advanced Filtering**: Filter by category, price, size, color, rating
- **Search**: Real-time product search with autocomplete
- **Product Reviews**: View and add 5-star reviews
- **Wishlist**: Save favorite products for later
- **Shopping Cart**: Add/remove items, quantity management
- **Checkout**: Secure multi-step checkout process

### 💳 Payment
- **Stripe Integration**: Secure payment processing
- **Order Management**: Track order status
- **Payment History**: View past transactions

### 👤 User Features
- **User Authentication**: Register and login
- **Profile Management**: Update personal information
- **Order History**: View past orders
- **Account Settings**: Manage preferences

### 🔐 Admin Features
- **Dashboard**: Comprehensive admin panel
- **Product Management**: Create, edit, delete products
- **Order Management**: Track and update order status
- **User Management**: View and manage users
- **Analytics**: Sales and traffic metrics

## 🛠️ Technology Stack

### Frontend
- React 18
- Redux for state management
- React Router for navigation
- Tailwind CSS for styling
- Axios for API communication

### Backend
- Node.js & Express.js
- MongoDB for database
- JWT for authentication
- Stripe for payments
- Mongoose for database ORM

### DevOps
- Docker & Docker Compose
- Nginx reverse proxy
- GitHub Actions CI/CD
- Let's Encrypt SSL/TLS

## 📖 Documentation

- [Setup Guide](docs/SETUP.md) - Local development setup
- [Deployment Guide](docs/DEPLOYMENT.md) - Production deployment
- [API Reference](docs/API.md) - Complete API documentation
- [Features Guide](docs/FEATURES.md) - All features explained
- [Contributing](docs/CONTRIBUTING.md) - How to contribute

## 🚀 Deployment

### Local Development
```bash
chmod +x setup.sh
./setup.sh
npm run dev
```

### Docker Deployment
```bash
docker-compose up -d
```

### Production (AWS, DigitalOcean, Heroku)
See [DEPLOYMENT.md](docs/DEPLOYMENT.md) for detailed instructions

### CI/CD Pipeline
Automatic testing and deployment on push to main branch via GitHub Actions

## 📦 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Products
- `GET /api/products` - Get all products (with filters)
- `GET /api/products/:id` - Get product details
- `POST /api/products/:id/reviews` - Add review
- `GET /api/products/:id/reviews` - Get reviews

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders/user/:userId` - Get user orders
- `GET /api/orders/:id` - Get order details

### Search
- `GET /api/search?q=query` - Search products
- `GET /api/search/suggestions?q=query` - Get suggestions

### Wishlist
- `POST /api/wishlist/:userId/:productId` - Add to wishlist
- `GET /api/wishlist/:userId` - Get wishlist
- `DELETE /api/wishlist/:userId/:productId` - Remove from wishlist

### Payment
- `POST /api/payment/create-payment-intent` - Create Stripe payment
- `POST /api/payment/confirm-payment` - Confirm payment
- `GET /api/payment/payment-status/:id` - Check payment status

## 🔧 Configuration

### Environment Variables

#### Backend
```
PORT=5000
NODE_ENV=production
MONGODB_URI=mongodb://user:pass@host:27017/db
JWT_SECRET=your_jwt_secret
STRIPE_SECRET_KEY=sk_live_your_key
```

#### Frontend
```
REACT_APP_API_URL=https://api.example.com
REACT_APP_STRIPE_PUBLIC_KEY=pk_live_your_key
```

## 📊 Monitoring

### Docker Commands
```bash
# View logs
docker-compose logs -f

# Check status
docker-compose ps

# View resource usage
docker stats

# Execute commands
docker-compose exec backend npm run migrate
```

### Health Checks
- API: `http://localhost:5000/api/products`
- Frontend: `http://localhost:3000`
- Nginx: `http://localhost/health`

## 🔐 Security

- JWT token-based authentication
- Password hashing with bcryptjs
- Stripe PCI-compliant payments
- CORS protection
- Rate limiting on API endpoints
- SSL/TLS encryption
- SQL injection prevention
- XSS protection

## 🐛 Troubleshooting

### Services Won't Start
```bash
docker-compose down -v
docker-compose up -d
docker-compose logs
```

### Database Connection Issues
```bash
# Check MongoDB status
docker-compose logs mongodb

# Verify connection string in .env
```

### API Not Responding
```bash
# Check backend logs
docker-compose logs backend

# Test health endpoint
curl http://localhost:5000/api/products
```

See [DEPLOYMENT.md](docs/DEPLOYMENT.md#troubleshooting) for more troubleshooting tips.

## 📝 Development

### Running Tests
```bash
cd backend && npm test
cd frontend && npm test
```

### Code Style
```bash
cd backend && npm run lint
cd frontend && npm run lint
```

### Building for Production
```bash
# Frontend
cd frontend && npm run build

# Backend
cd backend && npm run build
```

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](docs/CONTRIBUTING.md) for guidelines.

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -m 'Add your feature'`
4. Push to branch: `git push origin feature/your-feature`
5. Submit a Pull Request

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## 📞 Support

- 📧 Email: support@gaclothing.com
- 🐛 Issues: [GitHub Issues](https://github.com/ghoasshah/ga-clothing-brand-app/issues)
- 💬 Discussions: [GitHub Discussions](https://github.com/ghoasshah/ga-clothing-brand-app/discussions)

## 🎯 Roadmap

- [ ] Mobile app (React Native)
- [ ] Inventory management system
- [ ] Email notifications
- [ ] SMS notifications
- [ ] Analytics dashboard
- [ ] Customer support chat
- [ ] Loyalty program
- [ ] Multi-language support
- [ ] Social media integration
- [ ] AR product preview

## 👨‍💻 Author

**Ghoas Shah**
- GitHub: [@ghoasshah](https://github.com/ghoasshah)
- Email: ghoasshah@gmail.com

## ✨ Acknowledgments

- [React](https://reactjs.org)
- [Node.js](https://nodejs.org)
- [MongoDB](https://www.mongodb.com)
- [Stripe](https://stripe.com)
- [Docker](https://www.docker.com)
- [Nginx](https://nginx.org)

---

**Made with ❤️ for G.A Clothing Brand**
