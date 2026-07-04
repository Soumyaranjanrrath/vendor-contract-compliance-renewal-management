# Phase 2 - Solution Design

## 2.1 Solution Overview

### Objective

The objective of this phase is to design a centralized ServiceNow application that manages the complete lifecycle of vendor contracts. The solution focuses on contract management, compliance tracking, automated renewal reminders, approval workflows, and reporting to reduce manual effort and prevent missed contract renewals.

### Proposed Solution

The application consists of the following modules:

- Vendor Management
- Contract Management
- Compliance Management
- Renewal Management
- Reports & Dashboard

### Key Features

- Centralized vendor and contract repository
- Compliance document tracking
- Automated contract renewal reminders
- Approval workflow for renewals
- Role-based access control
- Reports and dashboards for contract status

### ServiceNow Components Used

| Component | Purpose |
|-----------|---------|
| Custom Tables | Store vendors, contracts and compliance data |
| Forms & Lists | Data entry and record management |
| Flow Designer | Automate renewal workflow |
| Business Rules | Perform server-side validations |
| Notifications | Send renewal reminders |
| Reports & Dashboards | Display contract insights |
| Roles & ACLs | Secure application access |

### Expected Outcome

- Prevent missed contract renewals
- Improve compliance tracking
- Reduce manual work
- Increase process visibility through dashboards

---

## 2.2 Application Architecture

### Application Structure

```
Vendor Contract Compliance & Renewal Management

├── Dashboard
├── Vendors
├── Contracts
├── Compliance
├── Renewals
├── Reports
└── Administration
```

### Architecture Overview

```
Users
   │
   ▼
Forms / Lists / Dashboard
   │
   ▼
Business Rules + Flow Designer
   │
   ▼
Custom Tables
```

### User Roles

| Role | Responsibility |
|------|----------------|
| Vendor Manager | Manage vendors and contracts |
| Compliance Officer | Verify compliance documents |
| Procurement Manager | Approve contract renewals |
| System Administrator | Configure and maintain the application |

### Application Workflow

```
Vendor
   │
   ▼
Contract
   │
   ▼
Compliance Verification
   │
   ▼
Renewal Reminder
   │
   ▼
Approval
   │
   ▼
Contract Renewed / Closed
```

### Design Approach

The application follows a modular design where each module handles a specific business function. Automation is implemented using Flow Designer and Business Rules, while role-based access ensures secure access to application data.

### Expected Outcome

- Well-structured application modules
- Scalable architecture
- Easy maintenance
- Secure access control

## 2.3 Data Model

### Objective

Design the database structure required to store vendor, contract, compliance, and renewal information.

---

### Custom Tables

#### 1. Vendor

| Field | Type |
|-------|------|
| Vendor ID | Auto Number |
| Vendor Name | String |
| Contact Person | String |
| Email | Email |
| Phone | Phone |
| Category | Choice |
| Status | Choice |
| Risk Level | Choice |

---

#### 2. Contract

| Field | Type |
|-------|------|
| Contract Number | Auto Number |
| Vendor | Reference (Vendor) |
| Contract Name | String |
| Start Date | Date |
| End Date | Date |
| Contract Value | Currency |
| Status | Choice |
| Renewal Status | Choice |

---

#### 3. Compliance Document

| Field | Type |
|-------|------|
| Document Name | String |
| Vendor | Reference (Vendor) |
| Contract | Reference (Contract) |
| Expiry Date | Date |
| Verification Status | Choice |
| Attachment | Attachment |

---

#### 4. Renewal Request

| Field | Type |
|-------|------|
| Request Number | Auto Number |
| Contract | Reference (Contract) |
| Requested By | Reference (User) |
| Request Date | Date |
| Approval Status | Choice |
| Remarks | String |

---

### Table Relationships

```
Vendor
   │
   ├────────── Contract
   │               │
   │               ├──────── Compliance Document
   │               │
   │               └──────── Renewal Request
```

---

### Expected Outcome

The data model establishes a structured relationship between vendors, contracts, compliance documents, and renewal requests, ensuring efficient data management and future scalability.