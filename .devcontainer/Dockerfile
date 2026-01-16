# Use the official devcontainer Java image as the base
FROM mcr.microsoft.com/devcontainers/java:1.1.23-bullseye

# Set environment variables
ENV JAVA_VERSION=23 \
    MAVEN_VERSION=3.9.12 \
    NODE_VERSION=20.x

# Install additional tools and dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    wget \
    git \
    build-essential \
    python3 \
    python3-pip \
    docker.io \
    maven=3.9.12 \
    && rm -rf /var/lib/apt/lists/*

# Verify Maven installation
RUN mvn -version

# Install Node.js (for potential frontend development)
RUN curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION} | bash - \
    && apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user for development
RUN useradd -m -s /bin/bash developer && \
    usermod -aG docker developer

# Set the working directory
WORKDIR /workspace

# Expose ports for WebGoat and WebWolf
EXPOSE 8080 9090

# Set the default user
USER vscode
