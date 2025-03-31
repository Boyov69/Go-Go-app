# Go-Go App

A comprehensive transportation marketplace application for Limburg, Belgium, connecting local transportation providers with passengers through a modern web and mobile platform.

## Project Overview

This project creates a Yandex-inspired transportation marketplace that allows:
- Multiple transportation providers (taxis, bus operators, independent drivers, public transportation, healthcare transportation) to register and offer services
- Users to book, track, and pay for transportation services
- Real-time ride tracking and communication
- Secure payment processing
- Provider and user ratings/reviews

## Technology Stack

### Backend
- Node.js with Express
- TypeScript
- MongoDB for document storage
- PostgreSQL for transactional data
- JWT for authentication
- WebSockets for real-time updates

### Web Frontend
- Next.js with React
- TypeScript
- Tailwind CSS for styling
- Context API for state management
- Mapbox for maps integration

### Mobile Application
- Flutter for cross-platform (iOS/Android) development
- Provider pattern for state management
- Material Design components
- Native device integration

### Infrastructure
- AWS for cloud hosting
- GitHub Actions for CI/CD
- Docker for containerization

## Repository Structure

```
go-go-app/
├── backend/                # Node.js backend API
│   ├── src/
│   │   ├── config/         # Configuration files
│   │   ├── controllers/    # Request handlers
│   │   ├── middleware/     # Express middleware
│   │   ├── models/         # Database models
│   │   ├── routes/         # API routes
│   │   ├── services/       # Business logic
│   │   └── utils/          # Utility functions
│   └── tests/              # Backend tests
├── frontend/               # Next.js web application
│   ├── public/             # Static assets
│   └── src/
│       ├── app/            # Next.js app router
│       ├── components/     # React components
│       ├── context/        # React context providers
│       ├── hooks/          # Custom React hooks
│       ├── lib/            # Utility functions
│       └── styles/         # CSS styles
├── mobile/                 # Flutter mobile application
│   └── go_go/
│       ├── lib/
│       │   ├── models/     # Data models
│       │   ├── providers/  # State management
│       │   ├── screens/    # UI screens
│       │   ├── services/   # API services
│       │   ├── utils/      # Utility functions
│       │   └── widgets/    # Reusable widgets
│       └── test/           # Mobile tests
└── docs/                   # Documentation
    ├── api/                # API documentation
    ├── architecture/       # Architecture diagrams
    └── user_guides/        # User guides
```

## Features

### Provider Features
- Company registration and verification
- Vehicle and driver management
- Real-time ride requests and tracking
- Earnings dashboard and analytics
- Schedule management
- Rating and review monitoring

### User Features
- Account creation and profile management
- Location search with suggestions
- Ride booking with fare estimation
- Multiple service types
- Real-time ride tracking
- Secure payment processing
- Rating and review system
- Ride history and receipts
- Notifications and messaging

## Getting Started

### Prerequisites
- Node.js 18+
- npm or yarn
- MongoDB
- PostgreSQL
- Flutter SDK
- Docker (optional)

### Backend Setup
```bash
cd backend
npm install
npm run dev
```

### Web Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

### Mobile Setup
```bash
cd mobile/go_go
flutter pub get
flutter run
```

## API Documentation

Comprehensive API documentation is available in the `/docs/api` directory, including:
- Authentication endpoints
- Provider management
- User booking system
- Payment processing
- Ride tracking

## Deployment

### Production Deployment Options

#### Backend Deployment
- **AWS Elastic Beanstalk**: Simplified deployment with automatic scaling
- **Google Cloud Run**: Containerized deployment with serverless scaling
- **Heroku**: Simple deployment with add-ons for databases

#### Frontend Deployment
- **Vercel**: Optimized for Next.js applications with automatic deployments
- **Netlify**: Simple deployment with continuous integration
- **AWS Amplify**: Integrated with AWS services

#### Mobile Deployment
- **Google Play Store**: For Android devices
- **Apple App Store**: For iOS devices

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Inspired by Yandex Taxi and other transportation marketplaces
- Designed specifically for the Limburg, Belgium transportation ecosystem
- Built with modern, state-of-the-art technologies for optimal performance and user experience
