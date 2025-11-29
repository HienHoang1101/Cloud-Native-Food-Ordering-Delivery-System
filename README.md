# DEPLOYMENT GUIDE - CLOUD-NATIVE FOOD ORDERING & DELIVERY SYSTEM

This document provides comprehensive instructions for deploying the entire Cloud-Native Food Ordering & Delivery System, including all microservices and client applications.

## PREREQUISITES

1. Ensure you have the following tools installed:

   - Node.js (v14 or later)
   - npm (v6 or later)
   - Docker (v20 or later)
   - Docker Compose (v1.29 or later)
   - kubectl (for Kubernetes deployment)
   - Expo CLI (for mobile app deployment)
   - MongoDB (for local development)

2. Access to:
   - MongoDB instance (production or cloud)
   - Container registry (Docker Hub or private)
   - Domain names and SSL certificates for production
   - Cloud provider (AWS, Azure, GCP)

## 1. SYSTEM ARCHITECTURE OVERVIEW

The system consists of the following components:

1. **Auth Service**: User authentication and management
2. **Order Service**: Order processing and cart management
3. **Restaurant Service**: Restaurant and menu management
4. **Payment Service**: Payment processing
5. **Notification Service**: Email and push notifications
6. **Food Delivery Service**: Delivery tracking and management
7. **Admin Service**: Administrative functions and reporting
8. **Client Applications**:
   - Customer Mobile App (React Native)
   - Restaurant Web Dashboard (React.js)
   - Delivery Personnel App (React Native)
   - Admin Dashboard (React.js)

## 2. LOCAL DEVELOPMENT DEPLOYMENT

### Clone the Repository

```
git clone https://github.com/your-repo/Cloud-Native-Food-Ordering-Delivery-System.git
cd Cloud-Native-Food-Ordering-Delivery-System
```

### Start MongoDB (if using local instance)

```
mongod --dbpath=/data/db
```

### Set Up Environment Variables

Create a `.env` file in each microservice directory using the provided `.env.example` templates.

### Install Dependencies and Start Services

#### Auth Service

```
cd auth
npm install
npm run dev
```

#### Order Service

```
cd ../order
npm install
npm run dev
```

#### Restaurant Service

```
cd ../restaurant
npm install
npm run dev
```

#### Payment Service

```
cd ../payment-service
npm install
npm run dev
```

#### Notification Service

```
cd ../notification-service
npm install
npm run dev
```

#### Food Delivery Service

```
cd ../food-delivery-server
npm install
npm run dev
```

#### Admin Service

```
cd ../admin-service
npm install
npm run dev
```

### Client Applications

#### Customer Mobile App

```
cd ../foodapp-client
npm install
npx expo start
```

#### Restaurant Dashboard

```
cd ../food-delivery-restuarant-web
npm install
npm start
```

#### Delivery App

```
cd ../client-delivery-app
npm install
npx expo start
```

#### Admin Dashboard

```
cd ../food-delivery-admin
npm install
npm start
```

## 3. DOCKER DEPLOYMENT

### Using Docker Compose (Development)

1. Navigate to the root directory:

   ```
   cd Cloud-Native-Food-Ordering-Delivery-System
   ```

2. Build and start all services:

   ```
   docker-compose build
   docker-compose up
   ```

3. To stop all services:
   ```
   docker-compose down
   ```

### Building Individual Docker Images

For each microservice (auth, order, restaurant, etc.):

1. Navigate to the service directory:

   ```
   cd <service-directory>
   ```

2. Build the Docker image:

   ```
   docker build -t food-ordering/<service-name>:latest .
   ```

3. Run the container:
   ```
   docker run -p <port>:<port> --env-file .env food-ordering/<service-name>:latest
   ```
