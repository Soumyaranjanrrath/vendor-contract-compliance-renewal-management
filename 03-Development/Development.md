# Phase 3 - Development

## 3.1 Application Creation

### Objective
Create the scoped ServiceNow application that will contain all project components.

### Activities
- Created a scoped application using App Engine Studio.
- Configured the application name and description.
- Generated the application scope.
- Verified successful application creation.

### Outcome
The application is ready for developing custom tables, workflows, notifications, reports, dashboards, and security components.

---

# Phase 3 – Development

## 3.1 Application & Data Model Setup

### Completed
- Created scoped ServiceNow application:
  - Vendor Contract Compliance & Renewal Management
- Configured application scope
- Created Vendor Contract table extending the Task table
- Added core dictionary fields
- Configured reference and choice fields
- Set Contract Number as the display field

### Fields Created

| Field | Type |
|--------|------|
| Contract Number | String |
| Vendor Name | String |
| Contract Title | String |
| Contract Type | Choice |
| Contract Value | Currency |
| Start Date | Date |
| End Date | Date |
| Renewal Date | Date |
| Compliance Status | Choice |
| Renewal Status | Choice |
| Contract Owner | Reference (User) |
| Department | Reference (Department) |
| Description | HTML |

---

## 3.2 Form Design

### Completed

Designed a user-friendly contract entry form using multiple sections for better usability.

### Sections

- Contract Information
- Contract Timeline
- Compliance
- Contract Ownership
- Additional Details

### Form Highlights

- Logical grouping of related fields
- Clean layout for contract management
- Choice fields for status tracking
- Reference fields for ownership
- HTML description field for detailed notes

---

## Current Status

✅ Application Created

✅ Vendor Contract Table Created

✅ Dictionary Fields Configured

✅ Form Layout Completed

➡ Next Phase: Business Rules & Automation