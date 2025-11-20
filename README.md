# Telecom Domain Management System

A comprehensive full-stack application for managing telecom operations with AI/ML capabilities for predictive analytics.

## Features

- **Customer Management**: Create, update, and manage customer information
- **Service Management**: Manage telecom services (voice, data, internet, TV, bundles)
- **Billing System**: Generate bills, track payments, and manage billing cycles
- **AI/ML Analytics**: 
  - Churn prediction using machine learning models
  - Revenue forecasting for future months
  - Customer risk analysis
- **Dashboard**: Real-time statistics and insights

## Tech Stack

### Backend
- **Python 3.8+**
- **Flask** - Web framework
- **SQLAlchemy** - ORM for database operations
- **MySQL** - Database
- **scikit-learn** - Machine learning library
- **pandas & numpy** - Data analysis

### Frontend
- **React** - UI framework
- **Axios** - HTTP client
- **React Router** - Routing

## Prerequisites

- Python 3.8 or higher
- Node.js 14 or higher
- MySQL 5.7 or higher
- npm or yarn

## Installation

### 1. Backend Setup

```bash
cd backend

# Create virtual environment (recommended)
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On Linux/Mac:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Create .env file from example
copy .env.example .env
# On Linux/Mac: cp .env.example .env

# Edit .env file with your database credentials
# DB_HOST=localhost
# DB_USER=root
# DB_PASSWORD=yourpassword
# DB_NAME=telecom_db
# SECRET_KEY=your-secret-key-here
# JWT_SECRET_KEY=your-jwt-secret-key-here

# Create MySQL database
mysql -u root -p
CREATE DATABASE telecom_db;
EXIT;

# Initialize database with sample data
python init_db.py
```

### 2. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install
```

## Running the Application

### Start Backend Server

```bash
cd backend
python app.py
```

The backend will run on `http://localhost:5000`

### Start Frontend Development Server

```bash
cd frontend
npm start
```

The frontend will run on `http://localhost:3000`

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user (protected)

### Customers
- `GET /api/customers` - Get all customers
- `GET /api/customers/:id` - Get customer by ID
- `GET /api/customers/:id/services` - Get customer services
- `POST /api/customers` - Create new customer
- `PUT /api/customers/:id` - Update customer
- `DELETE /api/customers/:id` - Delete customer

### Services
- `GET /api/services` - Get all services
- `GET /api/services/:id` - Get service by ID
- `POST /api/services` - Create new service
- `POST /api/services/assign` - Assign service to customer
- `PUT /api/services/:id` - Update service
- `DELETE /api/services/:id` - Delete service

### Billing
- `GET /api/billing` - Get all bills
- `GET /api/billing/:id` - Get bill by ID
- `GET /api/billing/customer/:customerId` - Get customer bills
- `POST /api/billing/generate` - Generate new bill
- `PUT /api/billing/:id/pay` - Mark bill as paid
- `PUT /api/billing/:id` - Update bill status

### Analytics
- `GET /api/analytics/dashboard` - Get dashboard statistics
- `POST /api/analytics/predict/churn` - Predict customer churn
- `POST /api/analytics/predict/revenue` - Predict future revenue
- `GET /api/analytics/customers/at-risk` - Get at-risk customers

## Default Credentials

After running `init_db.py`, you can login with:
- **Email**: admin@telecom.com
- **Password**: admin123

## Database Schema

The application uses the following main tables:
- `customers` - Customer information
- `services` - Available telecom services
- `customer_services` - Customer-service relationships
- `billing` - Billing records
- `bill_items` - Individual bill line items
- `users` - System users

## AI/ML Features

### Churn Prediction
Uses machine learning models to predict customer churn probability based on:
- Payment history and delays
- Service usage patterns
- Billing trends

### Revenue Forecasting
Linear regression model to predict future revenue based on historical billing data.

## Development

### Backend Structure
```
backend/
├── app.py                 # Main application file
├── requirements.txt       # Python dependencies
├── init_db.py            # Database initialization
├── database/
│   ├── __init__.py
│   └── models.py         # SQLAlchemy models
└── routes/
    ├── customers.py      # Customer routes
    ├── services.py       # Service routes
    ├── billing.py        # Billing routes
    ├── auth.py           # Authentication routes
    └── analytics.py      # Analytics & AI/ML routes
```

### Frontend Structure
```
frontend/
├── public/
│   └── index.html
└── src/
    ├── App.js            # Main app component
    ├── App.css
    ├── index.js          # Entry point
    └── index.css         # Global styles
```

## Troubleshooting

### Database Connection Issues
- Ensure MySQL is running
- Verify database credentials in `.env` file
- Check if database `telecom_db` exists

### Port Already in Use
- Backend: Change port in `app.py` (default: 5000)
- Frontend: React will prompt to use a different port

### Module Not Found Errors
- Ensure all dependencies are installed
- Activate virtual environment before running backend
- Run `npm install` in frontend directory

## License

This project is open source and available for educational purposes.

