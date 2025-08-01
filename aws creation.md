# AWS Account Creation Project Submission Report

**Author:** AFOLAYAN OLADIPO
**Date:** 1ST AUGUST 2025
**Project Duration:** ~2 hours

---

## 1. Executive Summary

This report documents the successful completion of the AWS Account Creation project. The objective was to perform and document the tangible, hands-on steps required to create a new Amazon Web Services (AWS) account. The process included fulfilling prerequisites, navigating the online registration forms, completing all necessary verification steps, and performing critical post-creation security configurations. All project goals were met, providing a practical demonstration of the entire account setup process.

---

## 2. Project Goals and Learning Outcomes

The following goals were achieved during the execution of this project:

* **Successful AWS Account Creation:** A new AWS account was created from scratch, including all stages of the signup process.
* **Verification Completion:** The email, phone number, and billing information were successfully verified with AWS.
* **AWS Management Console Navigation:** The newly created account was used to log in to the AWS Management Console, and its key features were explored.
* **Practical Security Implementation:** Multi-Factor Authentication (MFA) was configured for the root user, and an IAM user was created to follow best practices for daily account access.

This project provided invaluable practical experience in the foundational first steps of using AWS, moving beyond a theoretical understanding to a tangible, hands-on demonstration.

---

## 3. Hands-On Process Documentation

This section details the step-by-step execution of the AWS account creation process, serving as documentation of the completed practical steps.

### Step 1: Account Prerequisites and Initial Registration

Before starting, the required prerequisites were gathered: a valid email address, a phone number, and a credit card.

1.  **Navigated to AWS:** Opened a web browser and went to `https://aws.amazon.com/`.
2.  **Initiated Signup:** Clicked the **"Create an AWS Account"** button on the homepage.
3.  **Entered Account Details:** On the signup page, the primary email address and a unique AWS account name were entered. A verification code was requested and successfully received.

![alt text](<Screenshot 2025-08-01 045738.png>)

### Step 2: Verification and Billing Information

This phase involved confirming the account identity to AWS.

1.  **Email Verification:** The verification code received via email was entered and confirmed.
2.  **Root User Password:** A strong password was created for the root user, and this password was securely stored.
3.  **Contact Information:** The account type was selected as "Personal," and personal contact information (full name, phone number, and address) was provided.
4.  **Billing Information:** A valid credit card was entered for identity verification. A temporary authorization hold was placed on the card and released shortly after.
5.  **Phone Verification:** A phone number was entered, and a verification code was requested via SMS. The code was received and entered successfully.

 ![alt text](<Screenshot 2025-08-01 045934.png>)
 ![alt text](<Screenshot 2025-08-01 045948.png>)
 ![alt text](<Screenshot 2025-08-01 050038.png>)
 ![alt text](<Screenshot 2025-08-01 050107.png>)
 ![alt text](<Screenshot 2025-08-01 050205.png>)
 ![alt text](<Screenshot 2025-08-01 050234.png>)
 ![alt text](<Screenshot 2025-08-01 050629.png>)

![alt text](<Screenshot 2025-08-01 050736.png>)
![alt text](<Screenshot 2025-08-01 051208.png>)

6.  **Support Plan:** The **"Basic Support (Free)"** plan was selected and confirmed.

### Step 3: Accessing and Navigating the AWS Management Console

After completing the signup, the account was ready for use.

1.  **Confirmation and Sign-in:** The account creation was confirmed, and the user was prompted to go to the AWS Management Console.
2.  **Login:** Using the email address for the root user and the password created in Step 1, a successful login was performed.
3.  **Console Overview:** Upon logging in, the main dashboard of the AWS Management Console was visible. The key features identified were:
    * **Services Menu:** A drop-down menu in the top-left corner, providing access to all AWS services.
    * **Search Bar:** A prominent search bar at the top of the page for quickly finding services, features, and resources.
    * **Account Dropdown:** A menu in the top-right corner showing the account name and ID, with options for billing, security credentials, and logging out.

 ![alt text](<Screenshot 2025-08-01 051222.png>)
 ![alt text](<Screenshot 2025-08-01 052600.png>)
### Step 4: Post-Creation Security Setup (Best Practices)

To ensure the account's security, two critical hands-on steps were performed immediately after logging in.

#### 4.1. Enabling Multi-Factor Authentication (MFA) for the Root User

1.  **Navigated to IAM:** From the Services menu, the **IAM (Identity and Access Management)** service was selected.
2.  **Enabled MFA:** On the IAM dashboard, a security recommendation to enable MFA for the root user was clicked.
3.  **MFA Setup:** A virtual MFA device (using a mobile authenticator app) was selected, and the QR code was scanned. The subsequent one-time passwords were used to complete the MFA setup process.

   ![alt text](<Screenshot 2025-08-01 053451.png>)
   ![alt text](<Screenshot 2025-08-01 053607.png>)
   ![alt text](<Screenshot 2025-08-01 053640.png>)


#### 4.2. Creating an IAM User for Daily Tasks

1.  **Navigated to Users:** Within the IAM console, the "Users" option in the left-hand navigation pane was selected.
2.  **Added New User:** The **"Add users"** button was clicked. A new user was created with a username and password.
3.  **Permissions:** The `AdministratorAccess` policy was attached to the new user for full access, following a best-practice for a single-user account while still separating daily activity from the root user.
4.  **Finalized Creation:** The IAM user was created, and its login URL was noted for future use.

  ![alt text](<Screenshot 2025-08-01 054721.png>)
  ![alt text](<Screenshot 2025-08-01 055518.png>)
  ![alt text](<Screenshot 2025-08-01 055841.png>)
  ![alt text](<Screenshot 2025-08-01 055953.png>)
---

## 4. Conclusion

The AWS Account Creation project was successfully executed, with all hands-on steps completed and documented. 