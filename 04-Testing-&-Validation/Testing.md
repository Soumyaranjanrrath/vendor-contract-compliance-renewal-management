# Phase 4 – Testing

## Objective

The objective of this phase was to verify that the Vendor Contract Compliance & Renewal Management application functions correctly according to the defined business requirements. Testing included functional validation, business rule execution, workflow automation, security checks, negative testing, and end-to-end user acceptance testing.

---

# 4.1 Test Planning

The following testing categories were performed:

- Functional Testing
- Business Rule Testing
- Flow Designer Testing
- Security & ACL Testing
- Negative Testing
- User Acceptance Testing (UAT)

---

# 4.2 Functional Testing

| Test ID | Test Scenario | Expected Result | Status |
|----------|---------------|-----------------|--------|
| FT-01 | Create Vendor Contract | Contract created successfully | ✅ Pass |
| FT-02 | Update Vendor Contract | Changes saved successfully | ✅ Pass |
| FT-03 | Renewal Status Calculation | Renewal Status updated automatically | ✅ Pass |
| FT-04 | Create Renewal Task | Renewal Task generated automatically | ✅ Pass |
| FT-05 | Email Notification | Email sent to Contract Owner | ✅ Pass |
| FT-06 | Process Renewal Decision | Renewal Status updated correctly | ✅ Pass |
| FT-07 | Reports & Dashboard | Reports displayed accurate information | ✅ Pass |

---

# 4.3 Business Rule Testing

| Test ID | Business Rule | Expected Result | Status |
|----------|---------------|-----------------|--------|
| BR-01 | End Date Validation | End Date cannot be earlier than Start Date | ✅ Pass |
| BR-02 | Renewal Status Calculation | Active / Renewal Due / Expired calculated automatically | ✅ Pass |
| BR-03 | Renewal Decision Processing | Vendor Contract updated after Renewal Decision | ✅ Pass |

---

# 4.4 Flow Designer Testing

| Test ID | Flow | Expected Result | Status |
|----------|------|-----------------|--------|
| FL-01 | Renewal Reminder Flow | Flow triggered successfully | ✅ Pass |
| FL-02 | Renewal Task Creation | Renewal Task created automatically | ✅ Pass |
| FL-03 | Email Notification | Email delivered successfully | ✅ Pass |

---

# 4.5 Security & ACL Testing

| Test ID | Scenario | Expected Result | Status |
|----------|----------|-----------------|--------|
| ACL-01 | Contract Manager Access | Full access | ✅ Pass |
| ACL-02 | Compliance Officer Access | Appropriate access | ✅ Pass |
| ACL-03 | Contract User Access | Limited access based on role | ✅ Pass |
| ACL-04 | Unauthorized Record Modification | Access denied | ✅ Pass |

---

# 4.6 Negative Testing

| Test ID | Scenario | Expected Result | Status |
|----------|----------|-----------------|--------|
| NT-01 | Missing Mandatory Fields | Record not saved | ✅ Pass |
| NT-02 | Invalid End Date | Validation error displayed | ✅ Pass |
| NT-03 | Missing Renewal Decision | Task could not be completed | ✅ Pass |
| NT-04 | Unauthorized Access | Operation blocked | ✅ Pass |
| NT-05 | Email without Recipient | Validation error generated | ✅ Pass |

---

# 4.7 User Acceptance Testing (UAT)

An end-to-end business scenario was executed.

### Scenario

1. Create Vendor Contract
2. Assign Contract Owner
3. Configure Renewal Date
4. Flow triggers automatically
5. Renewal Task created
6. Email notification sent
7. Renewal Decision processed
8. Vendor Contract updated
9. Reports refreshed successfully

### Result

**User Acceptance Testing completed successfully.**

---

# 4.8 Bug Fix Summary

| Issue | Resolution |
|-------|------------|
| Email recipient missing | Assigned Contract Owner with valid email |
| Renewal Status calculation | Business Rule updated |
| Contract User unable to access application | Application Menu role configuration corrected |
| Renewal Decision validation | Field made mandatory |
| Flow execution errors | Flow configuration updated and retested |

---

# 4.9 Test Summary

| Category | Total | Passed | Failed |
|----------|------:|-------:|-------:|
| Functional Tests | 7 | 7 | 0 |
| Business Rule Tests | 3 | 3 | 0 |
| Flow Tests | 3 | 3 | 0 |
| Security Tests | 4 | 4 | 0 |
| Negative Tests | 5 | 5 | 0 |
| UAT Scenarios | 1 | 1 | 0 |

---

## Overall Result

All planned test cases were executed successfully.

The application met the defined functional and business requirements. Business Rules, Flow Designer automation, email notifications, role-based security, and reporting features operated as expected.

No critical defects remained at the end of testing.

**Testing Phase Status:** ✅ Completed