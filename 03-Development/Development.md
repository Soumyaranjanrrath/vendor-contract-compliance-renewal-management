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

----

# Phase 3.3 – Business Rule: Contract Date Validation

## Objective
Prevent users from saving vendor contracts where the End Date is earlier than the Start Date.

## Implementation
- Created a **Before Insert/Update Business Rule** on the **Vendor Contract** table.
- Compared `Start Date` and `End Date`.
- Displayed an error message if End Date was earlier than Start Date.
- Aborted record insertion/update using `current.setAbortAction(true)`.

## Result
- Invalid contract records are prevented from being saved.
- Improved data integrity through server-side validation.

---

# Phase 3.4 – Automatic Contract Number Generation

## Objective
Automatically assign a unique contract number to every vendor contract.

## Implementation
- Used ServiceNow's built-in **Number** field for automatic numbering.
- Updated the form to display the auto-generated Number field as the contract identifier.
- Verified that unique contract numbers are generated automatically for new records.

## Result
- Every new vendor contract receives a unique system-generated identifier.
- Eliminated manual entry of contract numbers.
- Leveraged ServiceNow's native numbering mechanism for consistency and uniqueness.

---