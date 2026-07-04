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

---

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

---

## 2.4 Table Relationships

### Objective

Define the relationships between the custom tables used in the application.

### Relationship Diagram

```
Vendor (1)
    │
    ├──────────────< Contract (Many)
    │                    │
    │                    ├──────────────< Compliance Document (Many)
    │                    │
    │                    └──────────────< Renewal Request (Many)
```

### Relationships

| Parent Table | Child Table | Relationship |
|--------------|-------------|--------------|
| Vendor | Contract | One-to-Many |
| Contract | Compliance Document | One-to-Many |
| Contract | Renewal Request | One-to-Many |

### Expected Outcome

The relationships ensure that each vendor can have multiple contracts, and each contract can maintain its own compliance documents and renewal requests.

---

## 2.5 Roles & Permissions

### Objective

Define user roles and their access permissions within the application.

| Role | Permissions |
|------|-------------|
| Vendor Manager | Create, Read, Update Vendors and Contracts |
| Compliance Officer | Read Contracts, Manage Compliance Documents |
| Procurement Manager | Approve Renewal Requests |
| System Administrator | Full Access |

### Expected Outcome

Role-based access ensures that users only perform actions relevant to their responsibilities.

---

## 2.6 User Interface Design

### Objective

Provide a simple and user-friendly interface for managing vendor contracts.

### Modules

- Dashboard
- Vendors
- Contracts
- Compliance
- Renewals
- Reports

### Forms

- Vendor Form
- Contract Form
- Compliance Document Form
- Renewal Request Form

### Lists

- Vendor List
- Contract List
- Compliance List
- Renewal List

### Expected Outcome

Users can easily create, update, search, and manage records through intuitive forms and lists.

---

## 2.7 Business Rules Design

### Objective

Automate common validations and updates using Business Rules.

| Business Rule | Purpose |
|---------------|---------|
| Validate Contract Dates | End Date must be after Start Date |
| Update Contract Status | Automatically mark expired contracts |
| Validate Compliance | Ensure required documents are uploaded |

### Expected Outcome

Business Rules improve data integrity and reduce manual validation.

---

## 2.8 Flow Designer Design

### Objective

Automate contract renewal and approval processes.

### Renewal Flow

```
Contract Near Expiry
        │
        ▼
Generate Renewal Request
        │
        ▼
Manager Approval
        │
 ┌──────┴──────┐
 │             │
Approved    Rejected
 │             │
 ▼             ▼
Renewed      Closed
```

### Expected Outcome

Automated workflows reduce manual effort and ensure timely contract renewals.

---

## 2.9 Notification Design

### Objective

Notify users about important contract events.

### Notifications

- Contract nearing expiry
- Renewal request created
- Renewal approved
- Renewal rejected
- Compliance document expiring

### Expected Outcome

Users receive timely email notifications, reducing the risk of missed actions.

---

## 2.10 Reports & Dashboard

### Objective

Provide insights into contract and compliance status.

### Reports

- Active Contracts
- Expiring Contracts
- Expired Contracts
- Pending Renewals
- Compliance Status

### Dashboard Widgets

- Total Vendors
- Active Contracts
- Contracts Expiring Soon
- Pending Renewals
- Compliance Overview

### Expected Outcome

Dashboards enable management to monitor contract health and compliance in real time.

---

## 2.11 Security Design

### Objective

Secure application data using ServiceNow access controls.

### Security Measures

- Role-Based Access Control (RBAC)
- Access Control Lists (ACLs)
- User Authentication
- Audit History

### Expected Outcome

Only authorized users can view or modify application records.

---

## 2.12 Integration Design

### Objective

The current version of the application is designed to operate independently without external integrations.

Future enhancements may include ERP or procurement system integrations using REST APIs.

---

## 2.13 Error Handling

### Strategy

- Mandatory field validation
- Business Rule validation
- Error messages for invalid input
- Prevent duplicate records where applicable

### Expected Outcome

Ensures accurate and reliable data entry.

---

## 2.14 Performance Considerations

### Performance Measures

- Use reference fields to avoid data duplication.
- Limit unnecessary Business Rules.
- Optimize list views with filters.
- Use indexed fields where appropriate.

### Expected Outcome

The application remains responsive as data volume grows.

---

## 2.15 Solution Summary

The solution provides a centralized platform for managing vendor contracts, compliance documents, and renewal requests. Automation through Business Rules and Flow Designer minimizes manual effort, while reports and dashboards improve visibility into contract status and compliance.

### Technologies Used

- ServiceNow Studio
- App Engine Studio
- Flow Designer
- Business Rules
- Notifications
- Reports & Dashboards
- ACLs

---