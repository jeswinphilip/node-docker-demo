# 🚀 Node.js Docker Demo with CI/CD Pipeline

A simple Node.js application demonstrating Docker containerization and automated CI/CD pipeline using GitHub Actions.

## 📋 Features

- **Express.js** web server with RESTful API endpoints
- **Docker** containerization with multi-stage builds
- **GitHub Actions** CI/CD pipeline for automated deployment
- **Docker Hub** integration for image distribution
- **Health check** endpoint for monitoring
- **Modern UI** with responsive design

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Local Dev     │    │  GitHub Actions │    │   Docker Hub    │
│                 │    │                 │    │                 │
│  npm start      │───▶│  Build & Test   │───▶│  Push Image     │
│  docker build   │    │  Docker Build   │    │  Distribution   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ 
- Docker Desktop
- Git
- GitHub account
- Docker Hub account

### Local Development

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd node-docker-demo
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run locally**
   ```bash
   npm start
   ```

4. **Access the application**
   - Main app: http://localhost:3000
   - Health check: http://localhost:3000/health
   - API endpoint: http://localhost:3000/api/hello

### Docker Local Testing

1. **Build the Docker image**
   ```bash
   docker build -t my-node-demo .
   ```

2. **Run the container**
   ```bash
   docker run -p 3000:3000 my-node-demo
   ```

3. **Access the application**
   - http://localhost:3000

## 🔧 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Welcome message and app info |
| `/health` | GET | Application health status |
| `/api/hello` | GET | Sample API response |

## 🐳 Docker Configuration

### Dockerfile Features

- **Multi-stage build** for optimized image size
- **Non-root user** for security
- **Alpine Linux** base for minimal footprint
- **Production-only dependencies**

### Build Commands

```bash
# Build image
docker build -t your-username/node-docker-demo .

# Run container
docker run -p 3000:3000 your-username/node-docker-demo

# Run in background
docker run -d -p 3000:3000 --name node-app your-username/node-docker-demo

# View logs
docker logs node-app

# Stop container
docker stop node-app
```

## 🔄 CI/CD Pipeline

### GitHub Actions Workflow

The pipeline automatically:
1. **Triggers** on push to main/master branch
2. **Checks out** the code
3. **Logs in** to Docker Hub
4. **Builds** the Docker image
5. **Pushes** to Docker Hub with tags

### Setup Instructions

1. **Create GitHub Repository**
   ```bash
   git init
   git remote add origin https://github.com/your-username/node-docker-demo.git
   ```

2. **Add GitHub Secrets**
   - Go to your repo → Settings → Secrets and variables → Actions
   - Add `DOCKER_HUB_USERNAME`: Your Docker Hub username
   - Add `DOCKER_HUB_ACCESS_TOKEN`: Your Docker Hub access token

3. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push -u origin main
   ```

### Docker Hub Setup

1. **Create Docker Hub Account**
   - Sign up at https://hub.docker.com

2. **Generate Access Token**
   - Go to Account Settings → Security → Access Tokens
   - Create a new token with read/write permissions
   - Copy the token for GitHub secrets

## 📦 Deployment

### From Docker Hub

Once the pipeline runs successfully, you can deploy anywhere:

```bash
# Pull the latest image
docker pull your-username/node-docker-demo:latest

# Run the application
docker run -p 3000:3000 your-username/node-docker-demo:latest
```

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `PORT` | 3000 | Application port |
| `NODE_ENV` | development | Node.js environment |

## 🧪 Testing

### Manual Testing

```bash
# Test health endpoint
curl http://localhost:3000/health

# Test API endpoint
curl http://localhost:3000/api/hello

# Test main endpoint
curl http://localhost:3000/
```

### Automated Testing

```bash
# Run tests (when implemented)
npm test
```

## 📁 Project Structure

```
node-docker-demo/
├── .github/
│   └── workflows/
│       └── docker.yml          # CI/CD pipeline
├── public/
│   └── index.html              # Frontend page
├── .dockerignore               # Docker ignore file
├── Dockerfile                  # Docker configuration
├── index.js                    # Main application
├── package.json                # Dependencies
└── README.md                   # Documentation
```

## 🔍 Monitoring

### Health Check

The application includes a health check endpoint at `/health` that returns:
- Application status
- Uptime
- Timestamp

### Logs

```bash
# View application logs
docker logs <container-name>

# Follow logs in real-time
docker logs -f <container-name>
```

## 🛠️ Development

### Adding New Features

1. **Create feature branch**
   ```bash
   git checkout -b feature/new-endpoint
   ```

2. **Make changes**
   ```bash
   # Add your code changes
   ```

3. **Test locally**
   ```bash
   npm start
   docker build -t test-image .
   docker run -p 3000:3000 test-image
   ```

4. **Push and create PR**
   ```bash
   git add .
   git commit -m "Add new feature"
   git push origin feature/new-endpoint
   ```

## 🚨 Troubleshooting

### Common Issues

1. **Port already in use**
   ```bash
   # Find process using port 3000
   lsof -i :3000
   # Kill the process
   kill -9 <PID>
   ```

2. **Docker build fails**
   ```bash
   # Clean Docker cache
   docker system prune -a
   # Rebuild
   docker build --no-cache -t my-node-demo .
   ```

3. **GitHub Actions fails**
   - Check Docker Hub credentials in GitHub secrets
   - Verify repository permissions
   - Check workflow file syntax

## 📚 Learning Resources

- [Node.js Documentation](https://nodejs.org/docs/)
- [Express.js Guide](https://expressjs.com/)
- [Docker Documentation](https://docs.docker.com/)
- [GitHub Actions](https://docs.github.com/en/actions)
- [Docker Hub](https://docs.docker.com/docker-hub/)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Happy Coding! 🎉**
