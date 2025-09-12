# Meeting Intelligence Platform

Advanced Meeting Intelligence & Productivity Platform - A next-generation application that transforms how working professionals conduct, transcribe, analyze, and act upon meetings.

## Features

- **Real-time AI transcription** with <500ms latency and 50+ language support
- **Intelligent sentiment analysis** and engagement tracking during meetings
- **Automatic action item extraction** with smart assignment and due date detection
- **Seamless workflow integration** with calendars, CRM, and project management tools
- **Enterprise-grade security** with end-to-end encryption and compliance (GDPR, HIPAA, SOC 2)
- **Real-time collaboration** with multi-user editing and sharing capabilities

## Architecture

This is a microservices-based application built with:

- **Frontend**: React 18 + TypeScript + Vite + PWA
- **Backend**: Node.js + Express + TypeScript
- **Database**: PostgreSQL + Redis + Elasticsearch
- **AI/ML**: OpenAI Whisper, Hugging Face Transformers, spaCy
- **Infrastructure**: Docker + Kubernetes + GitHub Actions

## Quick Start

### Prerequisites

- Node.js 18+
- Docker and Docker Compose
- Git

### Development Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd meeting-intelligence-platform
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Start development environment**
   ```bash
   # Start all services with Docker
   npm run docker:up
   
   # Or start services individually
   npm run dev
   ```

5. **Set up test data (optional)**
   ```bash
   # Set up sample data for testing and development
   npm run test:setup-data
   ```

6. **Access the application**
   - Frontend: http://localhost:5173
   - API Gateway: http://localhost:3000
   - Individual services: http://localhost:3001-3008

### Available Scripts

#### Development
```bash
npm run dev                 # Start all services (frontend + backend) concurrently
npm run dev:frontend        # Start React PWA frontend only (port 5173)
npm run dev:backend         # Start all backend microservices concurrently
```

#### Testing
```bash
npm test                           # Run all tests across all workspaces
npm run test:unit                  # Run unit tests for all services
npm run test:integration           # Run integration tests for all services
npm run test:e2e                  # Run end-to-end tests (frontend only)
npm run test:coverage             # Generate test coverage reports for all workspaces
npm run test:system-integration   # Run comprehensive system integration tests
npm run test:system-integration:docker # Run system integration tests in Docker environment
npm run test:uat                  # Run User Acceptance Tests (UAT)
npm run test:setup-data           # Set up test data for integration and system tests
npm run validate:tests            # Validate test configuration and dependencies
```

#### Building & Deployment
```bash
npm run build              # Build all applications and packages for production
npm run deploy:staging     # Deploy to staging environment
npm run deploy:prod        # Deploy to production environment (full deployment script)
npm run deploy:production  # Deploy to production environment (alias for deploy:prod)
```

#### Docker Management
```bash
npm run docker:build                    # Build Docker images for all services
npm run docker:up                      # Start all services with Docker Compose (detached)
npm run docker:down                    # Stop and remove Docker containers
npm run docker:test                    # Start test environment with Docker Compose
npm run docker:test:down               # Stop test environment containers
npm run docker:integration-test:up     # Start integration test environment
npm run docker:integration-test:down   # Stop integration test environment (with volume cleanup)
```

#### Database Management
```bash
npm run db:migrate         # Run database migrations
npm run db:seed           # Seed development data
npm run test:setup-data   # Set up comprehensive test data for integration testing
```

#### Code Quality & Formatting
```bash
npm run lint              # Run ESLint across all workspaces
npm run lint:fix          # Fix ESLint issues automatically
npm run format            # Format code with Prettier (all file types)
npm run format:check      # Check code formatting without making changes
```

## Project Structure

```
/
├── apps/                  # Applications
│   ├── frontend/          # React PWA application
│   ├── api-gateway/       # Main API gateway service
│   ├── recording-service/ # Audio recording and storage
│   ├── transcription-service/ # Speech-to-text processing
│   ├── analysis-service/  # Sentiment and insights analysis
│   ├── action-items-service/ # Task extraction and management
│   ├── collaboration-service/ # Real-time editing features
│   ├── integration-service/   # Third-party API integrations
│   ├── notification-service/  # Email, push, and in-app notifications
│   └── analytics-service/ # Meeting insights and reporting
├── packages/              # Shared packages
│   ├── shared-types/      # Common TypeScript interfaces
│   ├── database/          # Database models and migrations
│   ├── auth/              # Authentication utilities
│   ├── validation/        # Data validation schemas
│   └── testing/           # Shared testing utilities
├── infrastructure/        # Infrastructure as code
│   ├── docker/            # Docker configurations
│   ├── kubernetes/        # K8s deployment manifests
│   └── terraform/         # Terraform configurations
└── docs/                  # Documentation
```

## Services

### Frontend (Port 5173)
- Progressive Web App built with React 18
- Real-time transcription display
- Meeting recording interface
- Collaborative editing
- Analytics dashboard

### API Gateway (Port 3000)
- Request routing and load balancing
- Authentication and authorization
- Rate limiting and security
- API versioning

### Recording Service (Port 3001)
- Audio capture and storage
- Real-time audio streaming
- Audio format conversion
- WebRTC integration

### Transcription Service (Port 3002)
- OpenAI Whisper integration
- Real-time speech-to-text
- Speaker identification
- Multi-language support

### Analysis Service (Port 3003)
- Sentiment analysis
- Meeting insights generation
- Topic detection
- Engagement scoring

### Action Items Service (Port 3004)
- NLP-based task extraction
- Assignment and tracking
- Due date detection
- Progress monitoring

### Collaboration Service (Port 3005)
- Real-time collaborative editing
- Document sharing
- Version control
- Comment threads

### Integration Service (Port 3006)
- Calendar integrations
- CRM synchronization
- Project management tools
- Communication platforms

### Notification Service (Port 3007)
- Email notifications
- Push notifications
- In-app messaging
- Reminder scheduling

### Analytics Service (Port 3008)
- Meeting productivity metrics
- Custom reporting
- Data visualization
- Business intelligence API

## Testing

The project uses a comprehensive testing strategy:

- **Unit Tests**: Individual component and function testing
- **Integration Tests**: Service-to-service communication testing
- **System Integration Tests**: Full system workflow testing across all microservices
- **End-to-End Tests**: Complete user workflow testing
- **Performance Tests**: Load and stress testing
- **Security Tests**: Authentication, authorization, and vulnerability testing

### Running Tests

```bash
# Run all tests across all workspaces
npm test

# Run specific test types
npm run test:unit                  # Unit tests for all services
npm run test:integration           # Integration tests for all services
npm run test:e2e                  # End-to-end tests (frontend workflows)

# System-level testing
npm run test:system-integration    # Comprehensive system integration tests
npm run test:system-integration:docker # System tests in isolated Docker environment
npm run test:uat                  # User Acceptance Tests (UAT)

# Test data management
npm run test:setup-data           # Set up test data for integration and system tests

# Test validation and coverage
npm run validate:tests            # Validate test configuration and dependencies
npm run test:coverage             # Coverage reports for all workspaces
```

### System Integration Testing

The platform includes comprehensive system integration tests that validate end-to-end workflows across all microservices:

```bash
# Set up test data (run this first)
npm run test:setup-data

# Run system integration tests locally
npm run test:system-integration

# Run system integration tests in Docker (isolated environment)
npm run test:system-integration:docker
```

**System Integration Test Coverage:**
- Complete meeting workflow (record → transcribe → analyze → extract action items)
- Real-time collaboration and document sharing
- Third-party integrations (Calendar, CRM, Project Management)
- Authentication and authorization across services
- Performance and scalability under load
- Security and compliance validation
- Mobile application integration
- Offline functionality and data synchronization

**Test Environment Requirements:**
- All microservices must be running
- Test databases with sample data
- Mock external services (OpenAI, third-party APIs)
- Redis for caching and real-time features
- Elasticsearch for search functionality

## Deployment

### Development
```bash
# Start all services with Docker Compose
npm run docker:up

# Or start services individually
npm run dev
```

### Staging
```bash
npm run deploy:staging
```

### Production
```bash
# Deploy to production (comprehensive deployment script)
npm run deploy:prod

# Alternative command (same as above)
npm run deploy:production
```

### Docker Management
```bash
npm run docker:build                    # Build all Docker images
npm run docker:up                      # Start containers in detached mode
npm run docker:down                    # Stop and remove containers
npm run docker:test                    # Start test environment
npm run docker:test:down               # Stop test environment
npm run docker:integration-test:up     # Start integration test environment
npm run docker:integration-test:down   # Stop integration test environment with cleanup
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support, email support@meetingplatform.com or join our Slack channel.