# Project: Deploy Flask App to AWS EC2

## Stack:
- AWS EC2 (Ubuntu)
- Flask + Gunicorn + Nginx
- Domain pointing

## Steps:
1. Provision EC2 with SSH
2. Install dependencies and clone app
3. Setup Gunicorn systemd service
4. Setup Nginx reverse proxy
5. Add domain with Route53 or Namecheap
