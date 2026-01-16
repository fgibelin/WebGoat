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
    && rm -rf /var/lib/apt/lists/*

# Install Maven 3.9.12
RUN wget https://dlcdn.apache.org/maven/maven-3/3.9.12/binaries/apache-maven-3.9.12-bin.tar.gz /tmp/
RUN tar xvzf /tmp/apache-maven-3.9.12-bin.tar.gz /usr/lib/
RUN ln -s /usr/lib/apache-maven-3.9.12-bin/bin/mvn /usr/bin/mvn
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
