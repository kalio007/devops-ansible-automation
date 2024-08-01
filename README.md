# Introduction

This document outlines the steps involved in deploying a boilerplate application using Ansible. The process includes setting up the environment, installing dependencies, configuring the application, and establishing a reverse proxy.

## Prerequisites

Ubuntu 22.04 server with Python 3.12
Ansible installed

## Deployment Steps

**Clone the Repository:**

The Ansible playbook is cloned to the `/opt/stage_5b directory.`

**User Setup:**
A user named `hng` with sudo privileges is created.

**Infrastructure Setup:**
PostgreSQL is installed and configured.
Required dependencies are installed.
A messaging queue (e.g., RabbitMQ, Redis) is set up.

## Application Deployment

The boilerplate application is deployed to the server.
**Nginx Configuration:**
Nginx is installed and configured to act as a reverse proxy for the application.
Logging Setup:

Logs for the application are configured to be written to specific files.
Execution
To deploy the application, run the following command:

Bash
```ansible-playbook main.yaml -b```


## Additional Notes

The inventory file inventory.cfg should contain a host named hng.
For local testing, you can use the provided configuration in the inventory.cfg example.