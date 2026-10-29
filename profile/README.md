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

### 2. [SGS Transportation Application](https://github.com/SGS-WebDev/sgs-webint-transportation)

The SGS bus boarding application, built using the SGS Web Application Template. Students check in to a bus run at a kiosk by scanning their RFID badge or typing their name, and staff view boarding reports in the web UI.

### 3. [SGS Portainer](https://github.com/SGS-WebDev/sgs-portainer)

This repository sets up Portainer, a Docker management tool, for easy deployment and management of Docker environments across SGS servers.

Key features:
- Streamlined Docker management
- Consistent network configuration
- Easy setup and deployment process

### 4. [SGS Nginx Proxy](https://github.com/SGS-WebDev/sgs-nginx-proxy)

The reverse proxy in front of the applications on SGS web servers. Nginx runs directly on each host and is deployed with Ansible.

Key features:
- One configuration file per site, enabled and disabled with a helper script
- Shared snippets for TLS, proxy headers, WebSocket support and security headers
- A maintenance page for any request that doesn't match a site

### 5. [SGS Blueprints](https://github.com/SGS-WebDev/sgs-blueprints)

Infrastructure-as-code repository for automated provisioning and configuration of SGS servers.
This repository contains image builder configurations and first-boot automation scripts that set up RHEL 9.6 systems from initial boot through full deployment.

Key features:
- Automated first-boot configuration for new server instances
- VMware integration with hostname-based network configuration
- GitHub deploy key management for repository access
- Ansible-based configuration management
- Status tracking and MOTD integration for deployment visibility

### 6. [SGS Fleet](https://github.com/SGS-WebDev/sgs-fleet)

Health monitoring for the servers built by SGS Blueprints.

Key features:
- Host agents reporting on containers, scheduled jobs, backups and patching
- Website and certificate checks for the web applications
- Prometheus alert rules and a daily digest

### 7. [PS Google Calendar Sync](https://github.com/SGS-WebDev/sgs-ps-gcal-sync)

Syncs PowerSchool course sections to Google Workspace resource calendars (rooms). Pulls section data from PowerSchool's Oracle database, collapses meetings into recurring entries in PostgreSQL, and reconciles Google Calendar events to match.

Key features:
- Fully Dockerized pipeline: FastAPI dashboard, Celery workers, PostgreSQL
- Batched Google Calendar reconciliation via the `BatchHttpRequest` API
- CLI-first design with a web UI convenience layer over the same command services
- Deployment profiles for dev (Docker Compose), stage, and prod (Portainer)

### 8. [SGS PowerSchool](https://github.com/SGS-WebDev/sgs-powerschool)

Version-controlled home for St. George's PowerSchool reports and SQL queries. Connects read-only to the PowerSchool SIS Oracle database, preserving reporting knowledge as runnable, documented SQL.

Key features:
- `psq.py` CLI runner with parameter substitution, CSV export, and row limits
- All 308 sqlReports backed up and ported to clean, organized `.sql` files
- Read-only by design — the database account has SELECT-only grants
- Reference documentation: connection setup, glossary, grades and work habits, reporting calendar

### 9. [SGS Data Sync](https://github.com/SGS-WebDev/sgs-datasync)

The replacement for the legacy data sync between PowerSchool, Blackbaud and SGS Applications. Every weekday morning it builds the same tables the legacy sync writes and compares the two, without changing the live data yet.

Key features:
- Self-contained Docker Compose stack
- Scheduled jobs for the nightly build, new-student intake and contacts, all report-only for now
- A recorded comparison for every run

## How It All Fits Together

1. The **SGS Applications** repository serves as the core of our web services, providing centralized functionality and integration points for other applications.

2. New web applications start from the **SGS Web Application Template**; **SGS Transportation** was built this way.

3. These applications are then deployed using Docker, managed by Portainer (set up using the **SGS Portainer** repository).

4. **SGS Nginx Proxy** acts as the reverse proxy on each server, routing traffic to these applications.

5. **SGS Blueprints** builds the servers and **SGS Fleet** monitors their health.

6. Alongside the web ecosystem, **PS Google Calendar Sync**, **SGS PowerSchool** and **SGS Data Sync** integrate with the PowerSchool SIS — keeping Google Workspace room calendars in sync with course schedules, serving as the version-controlled home for reporting SQL, and replacing the legacy data sync.

This ecosystem allows for a standardized, easily manageable development and deployment process across the SGS web development team. It provides tools for local development, containerization, orchestration, and production deployment.
