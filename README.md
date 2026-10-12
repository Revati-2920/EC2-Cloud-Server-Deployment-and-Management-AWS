
# ☁️ EC2 Cloud Server Deployment and Management

Deploying and hosting a custom webpage on AWS using Amazon EC2, Amazon Linux 2023, and Apache HTTP Server.

## 📌 Project Overview

This project demonstrates how to deploy and manage a Linux-based cloud server using Amazon Web Services (AWS). An Amazon EC2 instance is configured to host a custom webpage through the Apache HTTP Server.

The project provides hands-on experience with cloud infrastructure, Linux administration, networking, SSH connectivity, security groups, and web server deployment.

## 🎯 Objectives

- Launch and configure an Amazon EC2 instance.
- Configure security groups and networking.
- Connect to a Linux server using SSH.
- Install and manage Apache HTTP Server.
- Deploy a custom HTML and CSS webpage.
- Verify website accessibility through a public IPv4 address.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| AWS EC2 | Cloud virtual server |
| Amazon Linux 2023 | Operating system |
| Apache HTTP Server | Web server |
| AWS VPC | Virtual networking |
| Security Groups | Network traffic control |
| SSH | Remote server administration |
| HTML5 | Webpage structure |
| CSS3 | Webpage styling |
| Windows CMD | SSH client terminal |

## 🏗️ Architecture

```text
             User / Web Browser
                     |
                     | HTTP (Port 80)
                     v
              Internet Gateway
                     |
                     v
                  AWS VPC
                     |
                     v
                Public Subnet
                     |
                     v
              Amazon EC2 Instance
               Amazon Linux 2023
                     |
                     v
              Apache HTTP Server
                     |
                     v
              Custom HTML Webpage
```

Administrative access:

```text
Windows CMD
    |
    | SSH (Port 22)
    v
Amazon EC2 Instance
```

## ⚙️ Implementation Steps

### 1. Launch the EC2 Instance

- Selected Amazon Linux 2023 as the Amazon Machine Image (AMI).
- Selected an appropriate EC2 instance type.
- Configured networking and public IPv4 connectivity.
- Created a key pair for SSH authentication.

### 2. Configure Security Groups

| Protocol | Port | Source | Purpose |
|---|---:|---|---|
| SSH | 22 | Administrator's public IP | Remote access |
| HTTP | 80 | `0.0.0.0/0` | Public website access |

**Security:** SSH access should be restricted to trusted IP addresses. HTTP is unencrypted; HTTPS is recommended for production applications.

### 3. Connect to EC2 Using SSH

Run the following command from Windows CMD:

```bash
ssh -i "path/to/ec2-web-server-key.pem" ec2-user@YOUR_PUBLIC_IP
```

Replace the key path and public IP with your actual values.

### 4. Update the Linux Server

```bash
sudo dnf update -y
```

### 5. Install Apache HTTP Server

```bash
sudo dnf install httpd -y
```

### 6. Start and Enable Apache

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

Verify the service status:

```bash
sudo systemctl status httpd
```

Expected state: `active (running)`.

### 7. Deploy the Webpage

The custom webpage is hosted at Apache's default document root:

```text
/var/www/html/index.html
```

The webpage uses HTML and CSS to display a custom landing page hosted on the EC2 instance.

### 8. Test the Deployment

Test the web server locally:

```bash
curl http://localhost
```

Open the following URL in a browser:

```text
http://YOUR_PUBLIC_IP
```

Replace `YOUR_PUBLIC_IP` with the public IPv4 address displayed in the EC2 console.

The webpage should load if the Apache service, routing, public IP, and security group rules are configured correctly.

## ✨ Project Highlights

- Launched a Linux-based EC2 instance.
- Established SSH connectivity from Windows CMD.
- Configured network access using security groups.
- Installed and managed Apache HTTP Server.
- Hosted a custom webpage on AWS.
- Tested the server locally and through a web browser.

## 📚 Key Learnings

- AWS EC2 and cloud infrastructure fundamentals.
- Linux package management and service administration.
- SSH authentication and remote server management.
- VPC networking, public IPv4 addresses, and security groups.
- HTTP communication and web server deployment.
- Basic cloud troubleshooting.

## 🔐 Security Best Practices

- Restrict SSH access to trusted IP addresses.
- Never upload private keys or AWS credentials to GitHub.
- Keep the operating system and packages updated.
- Review AWS resource usage and billing regularly.
- Use HTTPS for production deployments.
- Follow the principle of least privilege for AWS permissions.

## 🚀 Future Enhancements

- **AWS IAM:** Implement least-privilege access.
- **Amazon S3:** Integrate private cloud object storage.
- **VPC:** Design public and private subnet architecture.
- **Backend:** Connect the Student Management System to Flask or Node.js.
- **Database:** Add persistent student records using SQLite or PostgreSQL.
- **Docker:** Containerize the application.
- **CI/CD:** Automate deployments using GitHub Actions.
- **Terraform:** Provision infrastructure as code.
- **CloudWatch:** Monitor server health and logs.
- **HTTPS:** Configure TLS certificates.

## 💰 Cost Management

AWS charges depend on the region, instance type, storage, public IPv4 usage, and applicable account offers.

- Check pricing before launching resources.
- Stop the instance when it is not required.
- Terminate resources when the project is complete if they are no longer needed.
- Check for remaining EBS volumes, snapshots, Elastic IP addresses, and other billable resources.

Stopping an instance does not necessarily eliminate all charges.

## 📸 Project Screenshots

Add your actual project screenshots to a `screenshots/` directory and reference them below.

### EC2 Instance Running

![EC2 Instance Running](screenshots/ec2-instance-running.png)

### Security Group Configuration

![Security Group Rules](screenshots/security-group-rules.png)

### Deployed Website

![Deployed Website](screenshots/deployed-webpage.png)

## 👩‍💻 Author

**Revati Bhosale**

Computer Engineering Student | Cloud Computing & AWS Enthusiast

Building hands-on projects to strengthen my knowledge of cloud infrastructure, Linux, web deployment, and DevOps fundamentals.

---

⭐ If you find this project useful, feel free to explore the repository and share feedback.

**Build Today. Scale Tomorrow.**
