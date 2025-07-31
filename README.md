Okay, here's a detailed `README.md` file template for your "MarketPeak E-commerce Platform Deployment" Capstone Project. It includes placeholders for your specific details and clear instructions on where to embed screenshots.

-----

# MarketPeak E-commerce Platform Deployment

## Capstone Project Submission

**Author:** AFOLAYAN OLADIPO

**Date:** July 31, 2025

-----

## 1\. Project Overview

This capstone project demonstrates the end-to-end deployment of an e-commerce website, "MarketPeak," leveraging Git for version control, a Linux (Amazon Linux 2) environment for development and hosting, and Amazon Web Services (AWS) EC2 for cloud infrastructure. The project focuses on the operational aspects of web deployment, including server setup, web server configuration, and establishing a robust Continuous Integration/Deployment (CI/CD) workflow.

**MarketPeak** is designed as a basic online marketplace featuring:

  * Product listings
  * A shopping cart (front-end representation)
  * User authentication (front-end representation)

The project utilizes a pre-existing e-commerce website template, allowing the focus to remain on the infrastructure and deployment pipeline rather than extensive web development.

-----

## 2\. Technologies Used

  * **Version Control:** Git, GitHub
  * **Cloud Provider:** Amazon Web Services (AWS)
      * **Compute:** EC2 (Elastic Compute Cloud)
  * **Operating System:** Amazon Linux 2 (Linux)
  * **Web Server:** Apache HTTP Server (httpd)
  * **Programming/Scripting:** Bash (for shell commands)
  * **Website Template:** "Tooplate - E-commerce HTML Template"

-----

## 3\. Deployment Steps (End-to-End Walkthrough)

This section details the step-by-step process followed to deploy the MarketPeak e-commerce platform.

### 3.1. Implement Version Control with Git

#### 3.1.1. Initialize Git Repository

1.  Created a project directory named `MarketPeak_Ecommerce`.

2.  Navigated into the directory.

3.  Initialized a Git repository.

    ```bash
    mkdir MarketPeak_Ecommerce
    cd MarketPeak_Ecommerce
    git init
    ```

#### 3.1.2. Obtain and Prepare the E-Commerce Website Template

1.  Downloaded a suitable e-commerce website template from [Tooplate / other source link if specific].

2.  Extracted the contents of the downloaded template directly into the `MarketPeak_Ecommerce` project directory, ensuring main files like `index.html` were accessible.

   ![alt text](<Screenshot 2025-07-31 111500.png>)

#### 3.1.3. Stage and Commit the Template to Git

1.  Added all website files to the Git staging area.

2.  Configured Git global user name and email.

3.  Committed the initial set of changes with a descriptive message.

    ```bash
    git add .
    git config --global user.name "LIMASS2025"
    git config --global user.email "yoladipomas19@gmail.com"
    git commit -m "Initial commit with basic e-commerce site structure"
    ```
![alt text](<Screenshot 2025-07-30 164146.png>)

  ![alt text](<Screenshot 2025-07-30 164208.png>)

#### 3.1.4. Push Code to GitHub Repository

1.  Created a new, empty repository named `MarketPeak_Ecommerce` on GitHub.

2.  Linked the local Git repository to the remote GitHub repository.

3.  Pushed the local `main` branch to GitHub.

    ```bash
    git remote add origin https://github.com/LIMASS2025/MarketPeak_Ecommerce.git
    git push -u origin main
    ```

   ![alt text](<Screenshot 2025-07-30 164938.png>)

### 3.2. AWS Deployment

#### 3.2.1. Set Up an AWS EC2 Instance

1.  Logged into the AWS Management Console.

2.  Launched a new EC2 instance:

      * **AMI:** Amazon Linux 2 AMI
      * **Instance Type:** t2.micro (Free Tier eligible)
      * **Key Pair:** Created/Used an existing key pair ([Your Key Pair Name]).
      * **Security Group:** Configured a security group to allow:
          * SSH (Port 22) from my IP address.
          * HTTP (Port 80) from Anywhere (`0.0.0.0/0`).
      ![alt text](<Screenshot 2025-07-31 092035.png>)     

3.  Connected to the EC2 instance via SSH using the downloaded key pair:

    ```bash
    chmod 400 your-key.pem
    ssh -i "your-key.pem" ec2-user@YOUR_EC2_PUBLIC_IP
    ```

   
#### 3.2.2. Clone the Repository on the Linux Server (SSH Method)

This method was chosen for its security and suitability for production environments.

1.  **Generated an SSH keypair on the EC2 instance:**

    ```bash
    ssh-keygen
    ```

    (Accepted default file path and empty passphrase.)

2.  **Displayed and copied the public key:**

    ```bash
    cat ~/.ssh/id_rsa.pub
    ```

  ![alt text](<Screenshot 2025-07-31 095616.png>)

3.  **Added the SSH public key to my GitHub account:**

      * Navigated to GitHub Settings -\> SSH and GPG keys.
      * Clicked "New SSH key" and pasted the copied public key, providing a descriptive title ("MarketPeak EC2").

  ![alt text](<Screenshot 2025-07-31 100021.png>)

4.  **Cloned the repository using the SSH clone URL:**

    ```bash
    git clone git@github.com:LIMASS2025/MarketPeak_Ecommerce.git
    ```

    (Accepted host authenticity prompt if it appeared.)


#### 3.2.3. Install a Web Server on EC2

1.  Updated the package lists on the EC2 instance.

2.  Installed the Apache HTTP Server

3.  Started the apache2 service.

4.  Enabled `apt` to start automatically on system boot.

    ```bash
    sudo apt update -y
    sudo apt install apache2 -y
    sudo systemctl start apache2
    sudo systemctl enable apache2
    ```
![alt text](<Screenshot 2025-07-31 102501.png>)

#### 3.2.4. Configure httpd for Website

1.  Cleared the default contents of the Apache web root directory (`/var/www/html/`).

2.  Copied all the cloned website files from `~/MarketPeak_Ecommerce/` to `/var/www/html/`.

    ```bash
    sudo rm -rf /var/www/html/*
    sudo cp -r ~/MarketPeak_Ecommerce/* /var/www/html/
    ```

3.  Reloaded the `httpd` service to apply the configuration changes.

    ```bash
    sudo systemctl reload httpd
    ```

   ![alt text](<Screenshot 2025-07-31 103030.png>)

   ![alt text](<Screenshot 2025-07-31 103145.png>)

#### 3.2.5. Access Website from Browser

1.  Opened a web browser.

2.  Navigated to the Public IP address of the EC2 instance.

   ![alt text](<Screenshot 2025-07-31 103222.png>)
-----

## 4\. Continuous Integration and Deployment Workflow

This section outlines the established workflow for making updates and deploying them to the production server.

### Step 1: Developing New Features and Fixes (Local Machine)

1.  **Created a Development Branch:**
    ```bash
    git branch development
    git checkout development
    ```
2.  **Implemented Changes:** Made a minor text change on the homepage (`index.html`) to demonstrate a new feature/fix. (e.g., changed "Welcome to MarketPeak" to "MarketPeak: Your Ultimate Shopping Destination\!").

### Step 2: Version Control with Git (Local Machine)

1.  **Staged Changes:**
    ```bash
    git add .
    ```
2.  **Committed Changes:**
    ```bash
    git commit -m "feat: Updated homepage welcome message for MarketPeak"
    ```
3.  **Pushed Changes to GitHub:**
    ```bash
    git push origin development
    ```
![alt text](<Screenshot 2025-07-31 103854.png>)

![alt text](<Screenshot 2025-07-31 105549-1.png>)

### Step 3: Pull Requests and Merging to Main Branch (GitHub)

1.  **Created a Pull Request (PR) on GitHub:** From `development` into `main`.

2.  **Reviewed and Merged the PR:** Confirmed the changes and merged the `development` branch into `main`.

3.  **Pulled Merged Changes Locally:**

    ```bash
    git checkout main
    git pull origin main
    ```

### Step 4: Deploying Updates to the Production Server (AWS EC2)

1.  **Pulled the Latest Changes on the Server (via SSH):**

    ```bash
    ssh -i "your-key.pem" ec2-user@YOUR_EC2_PUBLIC_IP
    cd /var/www/html/
    sudo git pull origin main
    ```

 ![alt text](<Screenshot 2025-07-31 110421.png>)

2.  **Restarted the Web Server:**

    ```bash
    sudo systemctl reload httpd
    ```

### Step 5: Testing the New Changes (Browser)

1.  Accessed the Public IP address of the EC2 instance in a web browser.

2.  Verified that the updated text (e.g., "MarketPeak: Your Ultimate Shopping Destination\!") was live on the homepage.

![alt text](<Screenshot 2025-07-31 113821.png>)


## 5\. Conclusion

This project successfully demonstrates the deployment of a static e-commerce website on an AWS EC2 instance using Apache, managed effectively with Git for version control. The established CI/CD workflow, though manual, ensures that changes from a development branch can be reviewed, merged, and quickly deployed to the production server. This foundational understanding of cloud deployment and version control practices is crucial for building and maintaining robust web applications.

-----


-----