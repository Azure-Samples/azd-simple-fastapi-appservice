FROM mcr.microsoft.com/devcontainers/python:3.11

ENV PYTHONUNBUFFERED 1

# Install additional OS packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    git \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Install Azure Developer CLI
RUN curl -fsSL https://aka.ms/install-azd.sh | bash