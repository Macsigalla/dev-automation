
# 3. Installation and Environment Setup

## 3.1 Introduction

This document describes the software requirements and installation procedures needed to set up the End-to-End DevOps Platform.

## 3.2 Prerequisites

The following tools are required:

| Tool | Purpose |
|---|---|
| Git | Source code management |
| Java 17 | Java application development |
| Maven | Application build |
| Jenkins | CI/CD automation |
| SonarQube | Code quality analysis |
| Nexus | Artifact management |
| Docker | Containerization |
| AWS CLI | AWS resource management |

Tool versions should be verified against the versions used in the actual project.

## 3.3 Install Git

On macOS:

```bash
brew install git
```

Verify installation:

```bash
git --version
```

## 3.4 Install Java

Install OpenJDK 17:

```bash
brew install openjdk@17
```

Verify:

```bash
java -version
```

## 3.5 Install Maven

```bash
brew install maven
```

Verify:

```bash
mvn -version
```

## 3.6 Install Docker

Install Docker Desktop for macOS from:

https://www.docker.com/products/docker-desktop/

Verify:

```bash
docker --version
docker ps
```

## 3.7 Install AWS CLI

Install AWS CLI using Homebrew:

```bash
brew install awscli
```

Verify:

```bash
aws --version
```

## 3.8 Configure AWS Credentials

Configure AWS CLI using an IAM identity with the required permissions.

```bash
aws configure
```

Verify AWS identity:

```bash
aws sts get-caller-identity
```

Do not store AWS credentials in project files or GitHub.

## 3.9 Clone the Project Repository

```bash
git clone https://github.com/USERNAME/end-to-end-devops-platform.git
```

Navigate into the project:

```bash
cd end-to-end-devops-platform
```

## 3.10 Verify Environment

Run the following commands:

```bash
git --version
java -version
mvn -version
docker --version
aws --version
```

## 3.11 Conclusion

After completing the installation and configuration steps, the development environment should be ready for application development and DevOps automation.
