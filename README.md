# SGS Web Development Organization

Welcome to the SGS Web Development organization. This organization hosts a collection of repositories that work together to create a robust web development ecosystem for St. George's School. Our repositories are designed to streamline development, deployment, and management of web applications within the SGS infrastructure.

## Core Repository

### [SGS Applications](https://github.com/SGS-WebDev/sgs-applications)

This is our core monolithic internal application, serving as the central hub for various SGS web services. It integrates with other specialized applications in our ecosystem and provides the foundation for most of our web-based operations.

Key features:
- Centralized business logic for SGS web services
- Integration points for other SGS web applications
- Standardized development and deployment processes
- Integration with SGS infrastructure (LDAP, Certificate Authentication)

## Related Repositories

### 1. [SGS Web Application Template](https://github.com/SGS-WebDev/sgs-webint-template)

This repository serves as the foundation for new web applications at SGS. It provides a pre-configured Symfony framework setup with:

- Docker-based development and deployment environment
- Integration with SGS infrastructure (LDAP, Certificate Authentication)
- React-based Kiosk application
- Standardized tooling and configuration

### 2. [SGS Check-In Application](https://github.com/SGS-WebDev/sgs-webint-check-in)

A specialized application for managing check-ins at SGS, built using the SGS Web Application Template. This application demonstrates how individual services can be built and integrated with the core SGS Applications system.

### 3. [SGS Transportation Application](https://github.com/SGS-WebDev/sgs-webint-transportation)

An application for managing transportation services at SGS, also built using the SGS Web Application Template. Another example of a specialized service integrated with the core system.

### 4. [SGS Portainer](https://github.com/SGS-WebDev/sgs-portainer)

This repository sets up Portainer, a Docker management tool, for easy deployment and management of Docker environments across SGS servers.

Key features:
- Streamlined Docker management
- Consistent network configuration
- Easy setup and deployment process

### 5. [SGS Nginx](https://github.com/SGS-WebDev/sgs-nginx)

Provides a flexible reverse proxy setup for both development and production environments.

Key features:
- Consistent proxy configuration across environments
- Facilitates testing of applications behind a reverse proxy
- Easily configurable through environment variables

### 6. [SGS Dotfiles](https://github.com/SGS-WebDev/sgs-dotfiles)

Contains configuration files and scripts for setting up consistent development environments across the team. This repository helps ensure that all developers have a standardized setup, reducing "works on my machine" issues.

### 7. [SGS Terraform](https://github.com/SGS-WebDev/sgs-terraform)

Houses Terraform configurations for managing SGS infrastructure as code, ensuring consistent and reproducible infrastructure setups. This allows for version-controlled infrastructure changes and easy replication of environments.

### 8. [SGS Vagrantfiles](https://github.com/SGS-WebDev/sgs-vagrantfiles)

Contains Vagrantfiles used with machine images built for development environments. It facilitates the creation and management of development environments using VMware vSphere.

Key features:
- Easy setup of development environments
- Consistent configuration across team members
- Integration with VMware vSphere for cloud-based development

### 9. [SGS Packer Builds](https://github.com/SGS-WebDev/sgs-packer-builds)

This repository contains Packer configurations for building and updating SGS IT's vagrant and vsphere boxes. These boxes serve as the base for the development and production environments where the web applications run.

Key features:
- Automated building of development and production environments
- Consistent base configuration across all environments
- Easy updates and maintenance of base boxes

## How It All Fits Together

1. The **SGS Applications** repository serves as the core of our web services, providing centralized functionality and integration points for other applications.

2. Developers use **SGS Dotfiles** to set up their local development environment with all necessary tools and configurations.

3. They then use the **SGS Vagrantfiles** to create a development environment using the boxes created by the **SGS Packer Builds** configurations.

4. Within this environment, they use the **SGS Web Application Template** to create new web applications or work on existing ones like **SGS Check-In** and **SGS Transportation**.

5. These applications are then deployed using Docker, managed by Portainer (set up using the **SGS Portainer** repository).

6. **SGS Nginx** acts as a reverse proxy, routing traffic to these applications in both development and production environments.

7. **SGS Terraform** is used to manage and provision the infrastructure that hosts these applications, ensuring consistency across different environments.

This ecosystem allows for a standardized, easily manageable development and deployment process across the SGS web development team. It provides tools for local development, containerization, orchestration, and production deployment, all working together seamlessly. This setup ensures consistency across environments, from a developer's local machine to the production servers, facilitating efficient development, testing, and deployment of web applications at St. George's School.
