# UPI Payment Flow System

This project outlines the architecture and data flow for UPI (Unified Payments Interface) transactions as governed by the **NPCI UPI Network**. It captures all key actors and steps involved in initiating and completing a UPI-based fund transfer.

---

## 📘 Overview

The UPI system allows real-time money transfers between two bank accounts through mobile apps using a **Virtual Payment Address (VPA)**. This system eliminates the need to enter complex bank details like IFSC, account number, etc.

---

## 📊 Architecture Diagram

![Image](https://github.com/user-attachments/assets/b0bceb3e-b10d-453c-9804-c491a18b7f03)

---

## 🏛 About NPCI and the UPI Network

### 🏦 What is NPCI?

The **National Payments Corporation of India (NPCI)** is an umbrella organization for operating retail payments and settlement systems in India. It was established in 2008 by the Reserve Bank of India (RBI) and the Indian Banks' Association (IBA) under the provisions of the Payment and Settlement Systems Act, 2007.

NPCI's core mission is to provide infrastructure that supports interoperable, real-time, and robust payment systems that drive digital transactions at scale.

### 🔗 Role of NPCI in UPI

NPCI acts as the **central switch and clearing house** for the UPI system, with responsibilities including:

- Routing real-time interbank payment requests.
- Authenticating payee and payer information.
- Ensuring fund settlement between banks.
- Maintaining transaction integrity and regulatory compliance.
- Enforcing anti-fraud and security mechanisms.

### 🌐 UPI Network Highlights

- **24/7 Availability**: Unlike NEFT or IMPS with cut-off times, UPI operates 24x7, including holidays.
- **Interoperability**: Enables transfers between different banks and PSPs using a single system.
- **Transaction Speed**: Near-instant transfer confirmation and fund movement.
- **Low Cost**: Generally free or very minimal transaction fees, promoting mass adoption.
- **Ecosystem Integration**: Integrated with merchant apps, billers, utility providers, government portals, etc.

### 🧠 UPI Core Components Managed by NPCI

| Component              | Description |
|------------------------|-------------|
| **UPI Switch**         | Routes transactions between PSPs and banks. |
| **VPA Directory**      | Central directory service mapping VPAs to actual bank accounts. |
| **Authentication Layer** | Standardized security protocols (PIN, device binding, etc.). |
| **Dispute Management** | Manages failed/refunded transactions through standardized protocols. |
| **UPI Mapper & Registry** | Maintains mappings of PSPs, banks, handles, and mobile numbers. |
| **Analytics and Fraud Detection** | Tracks anomalies and potential misuse using behavioral and volume-based indicators. |

---

## 🧩 Components

### 1. **Customer (Payer)**
- Initiates the transaction.
- Uses a PSP mobile app to interact with the UPI network.

### 2. **Mobile Customer PSP App**
- Used by the customer to:
  - Create VPA
  - Initiate payments
  - Authenticate transactions
  - Receive payment notifications

### 3. **Payer (Customer) PSP**
- Payment Service Provider managing the payer’s UPI interactions.
- Handles VPA creation, payment authorization, and transaction routing.

### 4. **VPA Management Service**
- Creates and manages Virtual Payment Addresses.
- Responds to VPA creation requests from the PSP.

### 5. **QR Code Generator**
- Encodes payee's UPI details and metadata into scannable QR codes.

### 6. **NPCI UPI Network**
- Centralized switch for handling UPI transactions.
- Validates, routes, and settles requests between banks and PSPs.

### 7. **Remitter/Issuer Bank**
- Customer’s bank.
- Responsible for debiting funds after authorization.

### 8. **Beneficiary Bank**
- Payee’s bank.
- Receives credit instruction and processes deposit.

### 9. **Receiver PSP**
- Payment Service Provider of the payee.
- Validates payee details before transaction initiation.

---

## 🔄 Transaction Flow

### 1. **VPA Creation**
- User creates VPA via PSP app.
- PSP forwards the request to the VPA Management Service.
- VPA creation response is received and stored.

### 2. **Initiate Payment**
- Customer scans QR code or enters payee VPA.
- PSP sends payment request to NPCI.

### 3. **Authentication**
- User authenticates via PIN or biometric.
- PSP verifies and sends transaction to NPCI.

### 4. **Payee Validation**
- NPCI queries Receiver PSP for payee details.
- Receiver PSP validates and confirms.

### 5. **Funds Transfer**
- NPCI sends debit request to Remitter Bank.
- Upon success, credit request is sent to Beneficiary Bank.

### 6. **Completion**
- NPCI sends final payment status to Payer PSP.
- PSP notifies customer of transaction result.

---

## 🛡️ Security Measures

- All transactions are encrypted.
- User authentication is mandatory before processing payments.
- Real-time transaction validation ensures safety and integrity.
- NPCI continuously monitors for fraud and anomaly detection.
- PSPs and banks are required to comply with RBI cybersecurity standards.

---
