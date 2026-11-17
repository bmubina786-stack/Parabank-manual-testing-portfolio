# 📊 Chapter 5: Test Closure & Summary Report

**Project:** ParaBank Online Banking Manual QA Project  
**Execution Status:** Completed  
**Master Execution Sheet:** `ParaBank_Manual_Testing_Full_Project.xlsx`  

---

## 1. Executive Summary
Manual testing was conducted across all **9 core modules** of the ParaBank web application. A total of **66 test cases** were designed and executed, resulting in **54 Passes (81.8%)** and **12 Failures (18.2%)**. All 12 failures have been documented in the Defect Log (`BUG-001` through `BUG-012`) with clear reproduction steps and severity classifications.

---

## 2. Module-Wise Execution Breakdown

| Requirement ID | Module Name | Total TCs | Passed | Failed | Blocked | Pass Rate | Linked Bugs |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **REQ-01** | User Registration | 8 | 7 | 1 | 0 | 87.5% | `BUG-001` |
| **REQ-02** | Login & Authentication | 8 | 7 | 1 | 0 | 87.5% | `BUG-002` |
| **REQ-03** | Account Overview & Open Account | 8 | 7 | 1 | 0 | 87.5% | `BUG-011` |
| **REQ-04** | Transfer Funds | 9 | 7 | 2 | 0 | 77.8% | `BUG-003`, `BUG-004` |
| **REQ-05** | Bill Pay | 8 | 6 | 2 | 0 | 75.0% | `BUG-005`, `BUG-006` |
| **REQ-06** | Find Transactions | 7 | 6 | 1 | 0 | 85.7% | `BUG-007` |
| **REQ-07** | Update Contact Info | 6 | 5 | 1 | 0 | 83.3% | `BUG-008` |
| **REQ-08** | Request Loan | 6 | 5 | 1 | 0 | 83.3% | `BUG-012` |
| **REQ-09** | UI, Security & Cross-Browser | 6 | 4 | 2 | 0 | 66.7% | `BUG-009`, `BUG-010` |
| **TOTAL** | **All Modules** | **66** | **54** | **12** | **0** | **81.8%** | **12 Bugs** |

---

## 3. Defect Analysis by Severity

| Severity Level | Count | Percentage | Key Impact Areas |
| :--- | :---: | :---: | :--- |
| **Critical** | 5 | 41.7% | Negative fund transfers, blank Bill Pay submissions, post-logout session caching |
| **High** | 4 | 33.3% | Overdraft transfers allowed, invalid loan down payments, missing account source checks |
| **Medium** | 2 | 16.7% | Weak registration ZIP/phone format validation, date range filter edge cases |
| **Low** | 1 | 8.3% | Minor mobile viewport table horizontal overflow on small screens |

---

## 4. Key Recommendations & Release Sign-Off Decision
* **Release Recommendation:** **HOLD / DO NOT RELEASE TO PRODUCTION** until Critical and High severity defects (`BUG-003`, `BUG-004`, `BUG-005`, `BUG-009`) are resolved and re-tested.
* **Engineering Action Items:**
  1. Enforce strict server-side numeric range checks (`amount > 0` and `amount <= availableBalance`) on all financial endpoints (**Transfer Funds**, **Bill Pay**, **Request Loan**).
  2. Add `Cache-Control: no-store, no-cache` HTTP headers on authenticated pages to prevent browser back-button data exposure after logout.
  3. Implement consistent client-side and server-side schema validation for empty strings across all forms.
