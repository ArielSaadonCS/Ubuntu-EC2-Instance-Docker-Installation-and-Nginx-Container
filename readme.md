# Ubuntu EC2 + Docker + Nginx Lab

## Overview
This project demonstrates how to:
- Create an Ubuntu EC2 instance on AWS
- Connect to the instance via SSH
- Install Docker on Ubuntu
- Run an Nginx container using Docker
- Expose the service via HTTP using AWS Security Groups

---

## Architecture

A simple web architecture:

- A browser sends an HTTP request to the EC2 public IP
- The EC2 instance forwards port 80 traffic to a Docker container
- The Nginx container serves the default welcome page

---

## 1. EC2 Instance Setup

An Ubuntu EC2 instance was created with the following configuration:

- AMI: Ubuntu Server 22.04 LTS
- Instance type: Free tier eligible (e.g., t2.micro / t3.micro)
- Auto-assign public IP: Enabled
- Key pair: Generated and downloaded for SSH access

---

## 2. Security Group Configuration

The following inbound rules were configured:

| Type  | Protocol | Port | Source   | Purpose              |
|-------|----------|------|----------|----------------------|
| SSH   | TCP      | 22   | My IP    | Secure SSH access    |
| HTTP  | TCP      | 80   | 0.0.0.0/0 | Web traffic (Nginx)  |

---

## 3. SSH Connection

The instance was accessed using SSH:

```bash
ssh -i path/to/key.pem ubuntu@<EC2_PUBLIC_IP>