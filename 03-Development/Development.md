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

# Phase 3.5 – Dynamic UI Policy for Renewal Date

## Objective
Implement dynamic form behavior to make the **Renewal Date** field mandatory only for contract types that require renewal tracking.

## Implementation
- Created a UI Policy on the **Vendor Contract** table.
- Applied conditions for:
  - Software License
  - Service Agreement
- Added a UI Policy Action to make the **Renewal Date** field mandatory.
- Enabled **Reverse if false** so the field automatically becomes optional for all other contract types.

## Business Logic
- If Contract Type is **Software License** or **Service Agreement**, Renewal Date becomes mandatory.
- For all other contract types, Renewal Date remains optional.

## Outcome
- Improved user experience by enforcing data entry only when applicable.
- Reduced unnecessary mandatory fields.
- Implemented client-side validation using ServiceNow UI Policies.

## Skills Learned
- UI Policies
- UI Policy Actions
- Dynamic Form Behavior
- Client-side Form Validation
- Conditional Mandatory Fields

---

# Phase 3.6 – Automatic Renewal Status using Business Rule

## Objective
Automate the **Renewal Status** field based on the contract's Renewal Date to eliminate manual updates and ensure consistent renewal tracking.

## Implementation
- Created a **Before Business Rule** on the Vendor Contract table.
- Configured the Business Rule to execute on:
  - Insert
  - Update
- Used **GlideDate** API to compare dates and automatically determine the contract's renewal status.

## Business Logic
| Renewal Date | Renewal Status |
|--------------|----------------|
| Past Date | Expired |
| Within Next 30 Days | Renewal Due |
| More Than 30 Days | Active |

## Testing Performed
Verified the Business Rule using multiple scenarios:
- Renewal Date in the past → Expired
- Renewal Date within 30 days → Renewal Due
- Renewal Date beyond 30 days → Active
- Confirmed functionality during both record creation and record updates.

## Outcome
- Eliminated manual maintenance of the Renewal Status field.
- Ensured consistent server-side validation across all data sources.
- Improved reliability of renewal tracking for vendor contracts.

## Skills Learned
- Business Rules
- Server-side Scripting
- GlideDate API
- Date Comparison Logic
- Before Insert & Before Update Execution
- Automated Field Population

---