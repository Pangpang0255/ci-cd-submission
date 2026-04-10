# Tugas 29: Dockerfile dengan Konfigurasi Detail

## GitHub Repository URL:

```
https://github.com/Pangpang0255/ci-cd-final-project/blob/main/Dockerfile
```

## File Dockerfile Content:

```dockerfile
# Multi-stage build for Counter Service
# Stage 1: Dependencies and setup
FROM node:18-alpine as builder

LABEL maintainer="CI-CD Project Team"
LABEL description="Counter Service - CI/CD Final Project"
LABEL version="1.0.0"

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production && \
    npm cache clean --force

# Stage 2: Runtime environment
FROM node:18-alpine

# Install security updates
RUN apk update && \
    apk add --no-cache \
    curl \
    dumb-init && \
    rm -rf /var/cache/apk/*

# Set working directory
WORKDIR /app

# Create non-root user for security
RUN addgroup -g 1000 appuser && \
    adduser -D -u 1000 -G appuser appuser

# Copy node_modules and app from builder
COPY --from=builder --chown=appuser:appuser /app/node_modules ./node_modules
COPY --chown=appuser:appuser . .

# Switch to non-root user
USER appuser

# Expose port
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD curl -f http://localhost:8080/health || exit 1

# Use dumb-init as entrypoint to handle signals properly
ENTRYPOINT ["/sbin/dumb-init", "--"]

# Default command
CMD ["node", "src/app.js"]

# Build Arguments
ARG BUILD_DATE
ARG VCS_REF
ARG VERSION=1.0.0

# Labels for image metadata
LABEL org.label-schema.build-date=$BUILD_DATE
LABEL org.label-schema.vcs-ref=$VCS_REF
LABEL org.label-schema.version=$VERSION
LABEL org.label-schema.name="counter-service"
LABEL org.label-schema.description="Counter Service - CI/CD Tools and Practices Final Project"
LABEL org.label-schema.url="https://github.com/Pangpang0255/ci-cd-final-project"
LABEL org.label-schema.vcs-url="https://github.com/Pangpang0255/ci-cd-final-project"
LABEL org.opencontainers.image.title="counter-service"
LABEL org.opencontainers.image.description="Counter Service - CI/CD Final Project"
LABEL org.opencontainers.image.source="https://github.com/Pangpang0255/ci-cd-final-project"
```

## Dockerfile Build Instructions:

```bash
# Build image locally
docker build -t counter-service:1.0.0 .

# Build with build arguments
docker build \
  --build-arg BUILD_DATE=$(date -u +'%Y-%m-%dT%H:%M:%SZ') \
  --build-arg VCS_REF=$(git rev-parse --short HEAD) \
  --build-arg VERSION=1.0.0 \
  -t counter-service:1.0.0 .

# Build with tag from registry
docker build -t ghcr.io/pangpang0255/counter-service:1.0.0 .

# Run container
docker run -p 8080:8080 counter-service:1.0.0

# Run with environment variables
docker run -p 8080:8080 \
  -e NODE_ENV=production \
  -e LOG_LEVEL=info \
  counter-service:1.0.0
```

## Fitur Dockerfile:

✅ **Multi-stage Build:**

- Stage 1: Dependencies installation
- Stage 2: Optimized runtime with only production dependencies
- Reduces image size significantly

✅ **Security Best Practices:**

- Non-root user (appuser) for running container
- Minimal Alpine Linux base image
- Security updates applied (apk update)
- No unnecessary packages included

✅ **Image Optimization:**

- Alpine Linux (small footprint)
- npm ci instead of npm install (faster, more reliable)
- npm cache clean after installation
- dumb-init for proper signal handling

✅ **Health Check:**

- HTTP health check endpoint
- Configured interval, timeout, and retries
- Monitors application availability

✅ **Metadata Labels:**

- Build date, VCS reference, version
- OCI image labels
- Custom labels for image organization

✅ **Port Configuration:**

- Expose port 8080
- Environment variable support
- Default command to start application

## Build Commands Examples:

```bash
# Development build
docker build -t counter-service:dev .

# Production build with tags
docker build \
  --build-arg BUILD_DATE=$(date -u +'%Y-%m-%dT%H:%M:%SZ') \
  --build-arg VCS_REF=$(git rev-parse --short HEAD) \
  -t counter-service:1.0.0 \
  -t counter-service:latest .

# Push to registry
docker push ghcr.io/pangpang0255/counter-service:1.0.0
```
