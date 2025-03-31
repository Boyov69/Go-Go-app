# Go-Go App Production Deployment Guide

This guide provides comprehensive instructions for deploying the Go-Go App transportation marketplace to production environments.

## Table of Contents

1. [Backend Deployment](#backend-deployment)
2. [Frontend Deployment](#frontend-deployment)
3. [Mobile App Deployment](#mobile-app-deployment)
4. [Database Setup](#database-setup)
5. [Environment Configuration](#environment-configuration)
6. [Continuous Integration/Deployment](#continuous-integrationdeployment)
7. [Monitoring and Logging](#monitoring-and-logging)
8. [Scaling Considerations](#scaling-considerations)

## Backend Deployment

### Option 1: AWS Elastic Beanstalk

AWS Elastic Beanstalk provides an easy way to deploy and scale Node.js applications.

1. **Prerequisites**:
   - AWS account
   - AWS CLI installed and configured
   - Elastic Beanstalk CLI installed

2. **Deployment Steps**:
   ```bash
   # Initialize EB application
   cd backend
   eb init go-go-app --platform node.js --region eu-central-1
   
   # Create environment
   eb create go-go-app-production
   
   # Deploy application
   eb deploy
   ```

3. **Configuration**:
   - Create a `.ebextensions` folder in your project root
   - Add configuration files for environment variables, proxy settings, etc.

### Option 2: Google Cloud Run

Google Cloud Run is a fully managed platform for containerized applications.

1. **Prerequisites**:
   - Google Cloud account
   - Google Cloud SDK installed
   - Docker installed

2. **Deployment Steps**:
   ```bash
   # Build Docker image
   cd backend
   docker build -t gcr.io/your-project/go-go-app-backend .
   
   # Push to Google Container Registry
   docker push gcr.io/your-project/go-go-app-backend
   
   # Deploy to Cloud Run
   gcloud run deploy go-go-app-backend \
     --image gcr.io/your-project/go-go-app-backend \
     --platform managed \
     --region europe-west1 \
     --allow-unauthenticated
   ```

### Option 3: Heroku

Heroku offers a simple deployment process for Node.js applications.

1. **Prerequisites**:
   - Heroku account
   - Heroku CLI installed

2. **Deployment Steps**:
   ```bash
   # Login to Heroku
   heroku login
   
   # Create Heroku app
   cd backend
   heroku create go-go-app-backend
   
   # Add MongoDB add-on
   heroku addons:create mongodb:hobby-dev
   
   # Deploy application
   git push heroku master
   
   # Scale dynos
   heroku ps:scale web=1
   ```

## Frontend Deployment

### Option 1: Vercel (Recommended for Next.js)

Vercel is optimized for Next.js applications and offers seamless deployment.

1. **Prerequisites**:
   - Vercel account
   - Vercel CLI installed

2. **Deployment Steps**:
   ```bash
   # Install Vercel CLI
   npm install -g vercel
   
   # Login to Vercel
   vercel login
   
   # Deploy application
   cd frontend
   vercel
   
   # Deploy to production
   vercel --prod
   ```

3. **Configuration**:
   - Create a `vercel.json` file in your project root
   - Configure environment variables in the Vercel dashboard

### Option 2: Netlify

Netlify provides continuous deployment and hosting for static sites.

1. **Prerequisites**:
   - Netlify account
   - Netlify CLI installed

2. **Deployment Steps**:
   ```bash
   # Install Netlify CLI
   npm install -g netlify-cli
   
   # Login to Netlify
   netlify login
   
   # Initialize site
   cd frontend
   netlify init
   
   # Deploy site
   netlify deploy --prod
   ```

3. **Configuration**:
   - Create a `netlify.toml` file in your project root
   - Configure environment variables in the Netlify dashboard

### Option 3: AWS Amplify

AWS Amplify provides hosting for web applications with continuous deployment.

1. **Prerequisites**:
   - AWS account
   - Amplify CLI installed

2. **Deployment Steps**:
   ```bash
   # Install Amplify CLI
   npm install -g @aws-amplify/cli
   
   # Configure Amplify
   amplify configure
   
   # Initialize Amplify
   cd frontend
   amplify init
   
   # Add hosting
   amplify add hosting
   
   # Deploy application
   amplify publish
   ```

## Mobile App Deployment

### Android Deployment

1. **Generate Signed APK**:
   ```bash
   cd mobile/go_go
   flutter build apk --release
   ```

2. **Google Play Store Submission**:
   - Create a Google Play Developer account
   - Create a new application in the Google Play Console
   - Upload the signed APK
   - Fill in store listing details
   - Set up pricing and distribution
   - Submit for review

### iOS Deployment

1. **Generate Signed IPA**:
   ```bash
   cd mobile/go_go
   flutter build ios --release
   ```

2. **App Store Submission**:
   - Create an Apple Developer account
   - Create an App ID in the Apple Developer Portal
   - Create a distribution certificate and provisioning profile
   - Archive the application in Xcode
   - Upload to App Store Connect
   - Fill in store listing details
   - Submit for review

## Database Setup

### MongoDB Atlas

1. **Create Cluster**:
   - Sign up for MongoDB Atlas
   - Create a new cluster
   - Configure security settings
   - Create database user
   - Whitelist IP addresses

2. **Connection**:
   - Obtain connection string
   - Add connection string to environment variables

### PostgreSQL on AWS RDS

1. **Create Instance**:
   - Sign in to AWS Console
   - Navigate to RDS
   - Create a new PostgreSQL instance
   - Configure security groups
   - Create database user

2. **Connection**:
   - Obtain connection string
   - Add connection string to environment variables

## Environment Configuration

### Backend Environment Variables

Create a `.env` file in the backend directory with the following variables:

```
# Server Configuration
PORT=8000
NODE_ENV=production

# MongoDB Connection
MONGODB_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/<database>

# PostgreSQL Connection
POSTGRES_URI=postgresql://<username>:<password>@<host>:<port>/<database>

# JWT Authentication
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRATION=24h

# Payment Processing
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret

# Google Maps API
GOOGLE_MAPS_API_KEY=your_google_maps_api_key

# Email Service
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your_smtp_username
SMTP_PASS=your_smtp_password
```

### Frontend Environment Variables

Create a `.env.local` file in the frontend directory with the following variables:

```
# API Configuration
NEXT_PUBLIC_API_URL=https://api.go-go-app.com

# Google Maps API
NEXT_PUBLIC_GOOGLE_MAPS_API_KEY=your_google_maps_api_key

# Authentication
NEXT_PUBLIC_AUTH_DOMAIN=your_auth_domain

# Analytics
NEXT_PUBLIC_GA_TRACKING_ID=your_ga_tracking_id
```

### Mobile Environment Variables

Create a `.env` file in the mobile directory with the following variables:

```
# API Configuration
API_URL=https://api.go-go-app.com

# Google Maps API
GOOGLE_MAPS_API_KEY=your_google_maps_api_key

# Authentication
AUTH_DOMAIN=your_auth_domain
```

## Continuous Integration/Deployment

### GitHub Actions

Create a `.github/workflows` directory in your project root with the following workflow files:

#### Backend CI/CD (`backend-ci-cd.yml`):

```yaml
name: Backend CI/CD

on:
  push:
    branches: [ main ]
    paths:
      - 'backend/**'

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Use Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '18'
      - name: Install dependencies
        run: cd backend && npm ci
      - name: Run tests
        run: cd backend && npm test

  deploy:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to Heroku
        uses: akhileshns/heroku-deploy@v3.12.12
        with:
          heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
          heroku_app_name: "go-go-app-backend"
          heroku_email: ${{ secrets.HEROKU_EMAIL }}
          appdir: "backend"
```

#### Frontend CI/CD (`frontend-ci-cd.yml`):

```yaml
name: Frontend CI/CD

on:
  push:
    branches: [ main ]
    paths:
      - 'frontend/**'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v20
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          working-directory: ./frontend
```

## Monitoring and Logging

### Backend Monitoring

1. **New Relic**:
   - Sign up for New Relic
   - Install New Relic agent
   - Configure monitoring settings

2. **Datadog**:
   - Sign up for Datadog
   - Install Datadog agent
   - Configure monitoring settings

### Logging

1. **ELK Stack**:
   - Set up Elasticsearch
   - Configure Logstash
   - Set up Kibana dashboard

2. **Papertrail**:
   - Sign up for Papertrail
   - Configure log forwarding
   - Set up alerts

## Scaling Considerations

### Backend Scaling

1. **Horizontal Scaling**:
   - Use load balancers
   - Implement stateless architecture
   - Use Redis for session management

2. **Vertical Scaling**:
   - Increase server resources
   - Optimize database queries
   - Implement caching

### Database Scaling

1. **MongoDB Scaling**:
   - Implement sharding
   - Set up replica sets
   - Use indexing effectively

2. **PostgreSQL Scaling**:
   - Implement connection pooling
   - Use read replicas
   - Implement partitioning

## Security Considerations

1. **API Security**:
   - Implement rate limiting
   - Use HTTPS
   - Validate all inputs

2. **Authentication**:
   - Use secure JWT implementation
   - Implement refresh tokens
   - Set secure cookie options

3. **Data Protection**:
   - Encrypt sensitive data
   - Implement proper access controls
   - Regular security audits

## Backup and Disaster Recovery

1. **Database Backups**:
   - Schedule regular backups
   - Test restoration process
   - Store backups in multiple locations

2. **Disaster Recovery Plan**:
   - Document recovery procedures
   - Set up monitoring and alerts
   - Conduct regular drills

## Conclusion

This deployment guide provides a comprehensive approach to deploying the Go-Go App transportation marketplace to production environments. By following these instructions, you can ensure a secure, scalable, and reliable deployment of your application.

For any questions or issues, please refer to the project documentation or contact the development team.
