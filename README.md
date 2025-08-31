# Project 2 — Azure Networking and Storage

## 📌 Summary
This project demonstrates how to deploy secure Azure networking and storage resources, enforce isolation with NSGs and subnets, enable encryption, and automate deployments with ARM templates. It highlights **network security, storage account governance, and automation** — all critical skills for an **Azure Administrator (AZ-104)**.

---

## 🏢 Scenario
A company needs to deploy a **secure storage account**, ensure **network isolation** for its resources, enforce **data encryption**, and use **ARM templates** to automate deployments.

---

## 🛠️ Steps Performed

### 1. Virtual Network & Subnets
- Created a **VNet** with two subnets:
  - **Web subnet** (10.0.1.0/27)
  - **Database subnet** (10.0.0.0/27, with Service Endpoints enabled for Microsoft.Storage)
- Confirmed **intra-VNet communication** works by default.

### 2. Network Security Group (NSG)
- Deployed an **NSG** and associated it with the **Web subnet**.
- Added inbound rules:
  - Allow HTTPS (443) traffic from the internet.
  - Block all other inbound internet traffic (overriding defaults).

### 3. Storage Account
- Created a **Storage Account** with:
  - **Replication**: Locally redundant storage (LRS).
  - **Private Endpoint**: Only accessible via Database subnet.
  - **Encryption**: Microsoft-managed keys enabled.
- Disabled public network access for security.

### 4. ARM Template Deployment
- Exported ARM templates for VNet and Storage Account from the Azure Portal.
- Deployed via **Template Specs** for consistency.
- Verified resources appeared in **Deployment History** as successful.

### 5. Testing Access & Encryption
- Generated a **Shared Access Signature (SAS)** token for secure access.
- Tested using:
  - **Azure Storage Explorer**: Successfully connected with SAS URI.
  - **AzCopy CLI**: Verified upload/download to the container.

## ✅ Key Learnings
- **Subnets + NSGs** provide layered network security.
- **Private Endpoints** enforce secure access paths for sensitive resources.
- **Encryption at rest** is enabled by default, but you can choose Microsoft-managed or customer-managed keys.
- **ARM templates** allow repeatable deployments and governance at scale.
- **SAS tokens** provide temporary, scoped access to storage resources.
