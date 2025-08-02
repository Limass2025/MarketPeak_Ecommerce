Introduction to Cloud Computing - Security & Identity Management (IAM)

This document outlines the steps taken to implement Identity and Access Management (IAM) within AWS for a hypothetical fintech startup, Zappy e-Bank. The project focuses on setting up secure access for different roles (Backend Developer and Data Analyst) by utilizing IAM users, groups, and policies, along with Multi-Factor Authentication (MFA).

---

## Project Overview: Zappy e-Bank IAM Setup

Zappy e-Bank, a fintech startup, requires robust security and controlled access to its AWS resources. This project demonstrates how AWS IAM facilitates this by:
* **Creating and managing IAM users and groups:** To securely control access to AWS services and resources.
* **Implementing IAM roles and policies:** To set granular permissions for AWS services and users.
* **Enhancing security with Multi-Factor Authentication (MFA):** Adding an extra layer of protection to user accounts.

The scenario involves setting up access for a backend developer, John (requiring EC2 access), and a data analyst, Mary (requiring S3 access). The approach emphasizes efficiency through group-based permissions.

---

## Step-by-Step Implementation with Screenshots

### 1. Create Policy for the Development Team

The first step is to create a custom IAM policy that grants the necessary permissions for backend developers.

* **Action:** Navigate to the IAM console and click on "Policies." Then, click "Create policy."
![alt text](<Screenshot 2025-08-01 085217.png>)

* **Action:** Choose the "JSON" tab to define the policy. Enter the policy document that grants EC2 access.

  ![alt text](<Screenshot 2025-08-01 085331.png>)
* **Action:** Review the policy, provide a name , and an optional description. Then, click "Create policy."

![alt text](<Screenshot 2025-08-01 085742.png>)
* **Observation:** After creating the policy, search for "developer" in the policies search bar. Observe the presence of both AWS managed and customer managed policies, highlighting the distinction.

   ![alt text](<Screenshot 2025-08-01 090029.png>)

---

### 2. Create Policy for the Data Analyst Team

Similarly, a custom IAM policy is created for data analysts, granting S3 access.

* **Action:** Repeat the process from Step 1. In the policy creation, search for "$3" (S3) instead of EC2 to define the S3 access policy. Name the policy 
![alt text](<Screenshot 2025-08-01 104653.png>)

![alt text](<Screenshot 2025-08-01 104927.png>)

* **Action:** Review and create the policy, naming it  with an appropriate description.

    ![alt text](<Screenshot 2025-08-01 105018.png>)
---

### 3. Create Group for the Development Team

To efficiently manage permissions for multiple developers, an IAM group is created 

* **Action:** In the IAM console, select "User groups" from the navigation pane, then click "Create group" in the top right.

   ![alt text](<Screenshot 2025-08-01 105046.png>)

* **Action:** Provide the group name (e.g., `Developer-Team`). Attach the `Developer-Policy` created earlier.
![alt text](<Screenshot 2025-08-01 105238.png>)

![alt text](<Screenshot 2025-08-01 105351.png>)
---

### 4. Create Group for the Data Analyst Team

An IAM group is created for data analysts, and the `Analyst-Policy` is attached.

* **Action:** Repeat the process from Step 3. Name the group `Analyst-Team` and attach the `Analyst-Policy`.

    ![alt text](<Screenshot 2025-08-01 105523.png>)

![alt text](<Screenshot 2025-08-01 105539.png>)
---

### 5. Create IAM User for John (Backend Developer)

A new IAM user, John, is created and added to the `Developer-Team` group.

* **Action:** In the IAM console, select "Users" from the navigation pane, then click "Create user."

 ![alt text](<Screenshot 2025-08-01 105616.png>)

* **Action:** Provide the user name "John." Ensure "Provide user access to the AWS Management Console" is selected. Choose "I want to create an IAM user" and set an initial password.

   ![alt text](<Screenshot 2025-08-01 105809.png>)
* **Action:** On the "Set permissions" page, select "Add user to group" and choose the `Developer-Team` group.
![alt text](<Screenshot 2025-08-01 105947.png>)
   
* **Action:** Review the user details and click "Create user." Make note of the login URL and initial password.

![alt text](<Screenshot 2025-08-01 110150.png>)
---

### 6. Create IAM User for Mary (Data Analyst)

A new IAM user, Mary, is created and added to the `Analyst-Team` group.

* **Action:** Repeat the process from Step 5 for Mary. Add her to the `Analyst-Team` group.

   ![alt text](<Screenshot 2025-08-01 110218.png>)
![alt text](<Screenshot 2025-08-01 110233.png>)

![alt text](<Screenshot 2025-08-01 110302.png>)
---

### 7. Testing and Validation - John's Access

Validate that John has the correct access to EC2 and is restricted from other services.

* **Action:** Log in to the AWS Management Console as John using the provided credentials.

 

* **Action:** Navigate to the EC2 dashboard. Verify that John can view and attempt to create an EC2 instance.

 
* **Action:** Attempt to access an unauthorized service (e.g., S3). Observe the "Access Denied" message.


### 8. Testing and Validation - Mary's Access

Validate that Mary has the correct access to S3 and is restricted from other services.

* **Action:** Log in to the AWS Management Console as Mary using the provided credentials.


* **Action:** Navigate to the S3 dashboard. Verify that Mary can view and attempt to create an S3 bucket.

 

* **Action:** Attempt to access an unauthorized service (e.g., EC2). Observe the "Access Denied" message.

  
---

### 9. Implement Multi-Factor Authentication (MFA) for John

Enhance John's security by enabling MFA for his account.

* **Action:** As an administrator, navigate to IAM > Users and click on "John." Under the "Security credentials" tab, locate "Multi-factor authentication (MFA)" and click "Manage."

![alt text](<Screenshot 2025-08-01 111326.png>)

* **Action:** Choose "Authenticator app" as the MFA device, then follow the on-screen instructions to set up the virtual MFA device (scan QR code, enter codes).

  ![alt text](<Screenshot 2025-08-01 111424.png>)
* **Action:** Verify the MFA setup by entering two consecutive MFA codes.

    ![alt text](<Screenshot 2025-08-01 111512.png>)
![alt text](<Screenshot 2025-08-01 111531.png>)
---

### 10. Implement Multi-Factor Authentication (MFA) for Mary

Repeat the MFA setup process for Mary.

* **Action:** As an administrator, navigate to IAM > Users and click on "Mary." Follow the same steps as for John to enable MFA for Mary's account.

![alt text](<Screenshot 2025-08-01 111607.png>)
![alt text](<Screenshot 2025-08-01 111631.png>)

![alt text](<Screenshot 2025-08-01 111747.png>)
---

## Project Reflection

### 1. Explain the Role of IAM in AWS

Identity and Access Management (IAM) in Amazon Web Services is a core service that enables you to **securely control access** to AWS resources. Its primary purpose is to define **who is authenticated (signed in)** and **authorized (has permissions)** to use resources within your AWS environment. IAM contributes to security by allowing for the principle of **least privilege**, ensuring users and services only have the permissions necessary to perform their specific tasks. This prevents unauthorized access and reduces the risk of security breaches. Efficient management is achieved by centralizing access control, making it easier to onboard, offboard, and manage permissions for a growing number of users and applications.

### 2. Differentiate Between IAM Users and Groups

* **IAM Users:** An **IAM user** represents an individual person or application that interacts with AWS. Each user has unique security credentials (e.g., username and password for console access, access keys for programmatic access). You would create an IAM user for a specific individual who needs to log into the AWS Management Console or make programmatic calls to AWS services. For example, creating a user "John" for our backend developer.

* **IAM Groups:** An **IAM group** is a collection of IAM users. You can attach a policy to an IAM group, and all users within that group automatically inherit the permissions defined by that policy. This simplifies permission management, especially for larger organizations or teams with similar access needs. You would organize users into groups when multiple users require the same set of permissions. For instance, creating the `Developer-Team` group for all backend developers to streamline the assignment of EC2 access, rather than attaching the same policy to each individual developer.

### 3. Describe the Process of Creating IAM Policies

The process of creating a custom IAM policy involves defining a set of permissions that specify what actions are allowed or denied on which AWS resources. The general steps are:

1.  **Navigate to the IAM Console:** Go to the IAM service in your AWS Management Console.
2.  **Select "Policies":** In the navigation pane, choose "Policies" and then click on "Create policy."
3.  **Choose a Policy Editor:** You can choose between the **Visual editor** (a guided interface for selecting services, actions, and resources) or the **JSON tab** (for directly writing the policy document in JSON format). For more complex or precise policies, the JSON tab is often preferred.
4.  **Define Permissions:**
    * **Effect:** Specify whether the policy `Allow`s or `Deny`s actions.
    * **Actions:** Select the specific AWS service actions (e.g., `ec2:RunInstances`, `s3:GetObject`).
    * **Resources:** Define the specific AWS resources on which these actions can be performed (e.g., a particular S3 bucket, all EC2 instances). You can use ARNs (Amazon Resource Names) for granular control.
    * **Conditions (Optional):** Add conditions to restrict when a policy is in effect (e.g., only from a specific IP address, at a certain time of day).
5.  **Review and Tag:** Review the policy summary to ensure it grants the intended permissions. Add optional tags for organization.
6.  **Name and Describe:** Give the policy a descriptive name (e.g., `Developer-Policy`) and an optional description.
7.  **Create Policy:** Click "Create policy" to finalize the creation.

Once created, the policy can be attached to IAM users, groups, or roles, granting the defined permissions.

### 4. Explain the Significance of the Principle of Least Privilege

The **principle of least privilege** is a fundamental security best practice that dictates that users, programs, and processes should be granted only the minimum permissions necessary to perform their intended function, and nothing more.

In the context of IAM and AWS, its significance is paramount for several reasons:

* **Reduced Attack Surface:** By limiting permissions, you reduce the potential impact of a compromised account or credential. If a user's account is breached, an attacker can only access the resources that user was authorized to access, rather than the entire AWS environment.
* **Minimizing Human Error:** It helps prevent accidental deletion or modification of critical resources by users who don't need access to them.
* **Improved Auditability:** With granular permissions, it's easier to track who did what and when, simplifying security audits and compliance efforts.
* **Compliance Requirements:** Many regulatory frameworks and industry standards (e.g., PCI DSS, HIPAA, GDPR) mandate the implementation of least privilege.

Adhering to this principle is crucial for maintaining a strong security posture in the cloud, as demonstrated by our setup for John and Mary, where they only received access to the services relevant to their roles.

### 5. Reflect on the Scenario with John and Mary

For Zappy e-Bank's scenario, the IAM configurations for John (backend developer) and Mary (data analyst) were meticulously designed to align with their job functions and adhere to the principle of least privilege:

* **John (Backend Developer):**
    * **IAM User:** `John` was created as an individual IAM user.
    * **IAM Group:** John was added to the `Developer-Team` group.
    * **IAM Policy:** The `Developer-Policy` was created and attached to the `Developer-Team` group. This policy specifically grants permissions for **EC2 (Elastic Compute Cloud)** actions, such as `ec2:RunInstances`, `ec2:StartInstances`, `ec2:StopInstances`, and `ec2:DescribeInstances`. This aligns perfectly with John's role, as backend developers primarily interact with servers to deploy and manage applications.
    * **Principle of Least Privilege:** John's access was confined to EC2, preventing him from accessing sensitive data in S3 or other unrelated services, thereby upholding the principle of least privilege.
    * **MFA:** Multi-Factor Authentication was enabled for John's user, adding an essential layer of security to his access.

* **Mary (Data Analyst):**
    * **IAM User:** `Mary` was created as an individual IAM user.
    * **IAM Group:** Mary was added to the `Analyst-Team` group.
    * **IAM Policy:** The `Analyst-Policy` was created and attached to the `Analyst-Team` group. This policy specifically grants permissions for **S3 (Simple Storage Service)** actions, such as `s3:ListBucket`, `s3:GetObject`, `s3:PutObject`, and `s3:DeleteObject`. This directly supports Mary's role, as data analysts require access to data stored in S3 buckets for analysis.
    * **Principle of Least Privilege:** Mary's access was strictly limited to S3, preventing her from managing EC2 instances or other services outside her scope, ensuring adherence to least privilege.
    * **MFA:** Multi-Factor Authentication was also enabled for Mary's user, enhancing the security of her access to data.

This structured approach, leveraging IAM groups and role-specific policies, simplifies future team expansion for Zappy e-Bank, as new developers or data analysts can simply be added to their respective groups, inheriting the necessary permissions automatically without individual policy assignments.