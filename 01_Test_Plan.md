# 📋 Chapter 1: Master Test Plan — ParaBank Online Banking

**Document Version:** 1.0  
**Project Name:** ParaBank Web Application QA Validation  
**Prepared By:** Mubina Bhadgaon 
**Application URL:** `https://parabank.parasoft.com/parabank/index.htm`  

---

## 1. Introduction & Objective
The objective of this Test Plan is to define the testing strategy, scope, resources, schedule, and exit criteria for validating the core banking functionalities of the **ParaBank** web application. This ensures the platform meets functional, usability, boundary, and basic security standards prior to release.

---

## 2. Scope of Testing

### 2.1 In-Scope Modules
1. **User Registration (`REQ-01`):** New customer onboarding, field validations, duplicate username handling.
2. **Authentication & Session Management (`REQ-02`):** Login, logout, invalid credential handling, session expiry.
3. **Account Overview & Open New Account (`REQ-03`):** Checking/Savings creation, balance accuracy, account detail drill-down.
4. **Fund Transfers (`REQ-04`):** Internal transfers between user accounts, boundary checks, insufficient balance handling.
5. **Bill Pay Service (`REQ-05`):** Payee details validation, account number matching, payment processing.
6. **Find Transactions (`REQ-06`):** Search by Transaction ID, Date, Date Range, and Amount.
7. **Update Contact Info (`REQ-07`):** Profile editing, persistence of updated phone/address fields.
8. **Request Loan (`REQ-08`):** Down payment validation, loan approval/denial logic based on available funds.
9. **UI, Security & Cross-Browser Checks (`REQ-09`):** Input sanitization, URL manipulation, responsive layout.

### 2.2 Out-of-Scope
* Backend database administration and Parasoft Admin page configuration resets.
* Load/Performance stress testing (JMeter/LoadRunner) and automated CI/CD pipeline integration.
* Third-party payment gateway settlement APIs.

---

## 3. Test Strategy & Types of Testing
* **Smoke Testing:** Verify critical paths (Login, Account Overview, Transfer Funds) work before deep testing.
* **Functional Testing:** Validate every feature against the Business Requirements (`02_Business_Requirements.md`).
* **Negative & Boundary Testing:** Intentionally input negative numbers, zeros, special characters, and blank fields.
* **Security Testing:** Test SQL injection strings in login fields, URL parameter tampering, and post-logout browser history access.
* **Compatibility Testing:** Execute core flows on Google Chrome and Mozilla Firefox.

---

## 4. Entry & Exit Criteria

### 4.1 Entry Criteria
* Application URL (`parabank.parasoft.com`) is accessible and responsive.
* Business Requirements (`REQ-01` to `REQ-09`) are documented and baselined.
* Test cases (`TC-01` to `TC-66`) and test data sets are reviewed and ready.

### 4.2 Exit Criteria
* 100% of planned test cases (66/66) have been executed.
* All discovered defects are documented with reproducible steps, severity, and priority in the Defect Log.
* No Critical/Blocker defects remain undocumented or unanalyzed.
* Final Test Summary Report is completed and signed off.

---

## 5. Risks & Mitigation Plan

| Risk ID | Risk Description | Impact | Mitigation Strategy |
| :--- | :--- | :--- | :--- |
| **RSK-01** | ParaBank's public demo database automatically resets/cleans periodically. | High | Re-register a fresh test user immediately before executing stateful test suites (Transfers/Loans) and capture screenshots immediately upon finding bugs. |
| **RSK-02** | Public server downtime or slow response times during peak hours. | Medium | Schedule execution runs during off-peak hours and retry failed page loads before logging network timeouts as bugs. |
| **RSK-03** | Lack of an official Requirements Specification document from the vendor. | Medium | Reverse-engineer a structured BRD (`02_Business_Requirements.md`) based on standard retail banking domain rules. |

---

## 6. Test Environment & Deliverables
* **Hardware/OS:** Desktop (1920x1080), Windows 11
* **Browsers:** Google Chrome (Latest), Mozilla Firefox (Latest)
* **Deliverables:**
  1. `01_Test_Plan.md`
  2. `02_Business_Requirements.md`
  3. `ParaBank_Manual_Testing_Full_Project.xlsx` (RTM, 66 Test Cases, Defect Log)
  4. `05_Test_Summary_Report.md`
