# Ansible Deployment for Boilerplate Application

## Overview

This Ansible playbook sets up a new instance of the assigned boilerplate application using Infrastructure as Code (IaC). The setup includes cloning the repository, deploying the application, installing dependencies, configuring PostgreSQL and a messaging queue, setting up Nginx for reverse proxy, and configuring logging.

## Requirements

- Ubuntu 22.04 server with Python 3.12
- Ansible

## Setup Instructions

### 1. User and Directory Setup

1. **Create a user named `hng` with sudo privileges:**
   The playbook will handle this automatically.

2. **Clone the repository:**
   The repository will be cloned into the `/opt/stage_5b` directory and owned by the `hng` user.

### 2. Database and Dependencies

1. **Install PostgreSQL:**
   PostgreSQL will be installed, and the admin credentials will be saved in `/var/secrets/pg_pw.txt`.

2. **Install Application Dependencies:**
   All required dependencies, including databases and messaging queues, will be installed and configured.

### 3. Application and Proxy Setup

1. **Run the Application:**
   The application will be configured to run on `127.0.0.1:3000` without exposing port 3000 externally.

2. **Install and Configure Nginx:**
   Nginx version 1.26 will be installed and configured to reverse proxy requests from port 80 to the application running on port 3000.

### 4. Logging Configuration

1. **Configure Logging:**
   - Standard error logs will be saved in `/var/log/stage_5b/error.log`
   - Standard output logs will be saved in `/var/log/stage_5b/out.log`
   - Both log files will be owned by the `hng` user.

## Execution

To deploy the setup, run the following command:

```bash
ansible-playbook main.yaml -b
```

## Additional Information
Ensure that your inventory file `inventory.cfg` specifies the host as `hng`
For example,when configuring locally I used:

```bash
[hng]
localhost ansible_connection=local ansible_become=true ansible_become_method=sudo ansible_become_flags='-H -S' ansible_remote_tmp=~/ansible_tmp ansible_python_interpreter=/usr/bin/python3
```
