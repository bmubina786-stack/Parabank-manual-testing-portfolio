# 🏦 ParaBank Online Banking — End-to-End Manual QA Testing Project

![QA Status](https://img.shields.io/badge/Testing_Phase-Completed-brightgreen)
![Test Cases](https://img.shields.io/badge/Test_Cases-66-blue)
![Pass Rate](https://img.shields.io/badge/Pass_Rate-81.8%25-yellow)
![Defects Logged](https://img.shields.io/badge/Defects_Logged-12-red)

## 📌 Project Overview
This repository showcases a complete, real-world **Manual Software Testing (STLC)** portfolio project executed on **ParaBank** (`https://parabank.parasoft.com/`), a simulated retail banking web application. 

The goal of this project is to demonstrate end-to-end QA artifacts—from requirement analysis and test planning to test case design (using **Boundary Value Analysis** and **Equivalence Partitioning**), Requirement Traceability Matrix (RTM), defect management, and test closure reporting.

---

## 📊 Executive Execution Summary

| Metric | Count / Value |
| :--- | :--- |
| **Application Under Test (AUT)** | ParaBank Online Banking Web App |
| **Total Business Requirements** | 9 (`REQ-01` to `REQ-09`) |
| **Total Test Cases Executed** | **66** |
| **Passed** | **54** (81.8%) |
| **Failed** | **12** (18.2%) |
| **Blocked** | **0** (0.0%) |
| **Total Defects Logged** | **12** (`BUG-001` to `BUG-012`) |
| **Critical / High Severity Bugs** | 5 Critical, 4 High |

---

## 📂 Repository Structure

```text
parabank-manual-testing-portfolio/
├── README.md                                  # Project overview, metrics & interview highlights
├── 01_Test_Plan.md                            # Test strategy, scope, entry/exit criteria & risks
├── 02_Business_Requirements.md                # Reverse-engineered BRD & User Stories (REQ-01 to REQ-09)
├── 05_Test_Summary_Report.md                  # Final STLC closure report, defect analysis & sign-off
└── ParaBank_Manual_Testing_Full_Project.xlsx  # Master workbook (Dashboard, RTM, 66 Test Cases, 12 Bugs)
```

---

## 🧪 Test Design Techniques Applied
* **Boundary Value Analysis (BVA):** Tested minimum/maximum transaction limits (`$0.00`, `$0.01`, negative amounts, and balances exceeding available funds).
* **Equivalence Partitioning (EP):** Validated input partitions for registration fields, ZIP codes, phone numbers, and account numbers.
* **Security & Session Testing:** Verified back-button caching after logout, SQL injection resistance on login inputs, and cross-account unauthorized access via URL manipulation.
* **UI / Cross-Browser Compatibility:** Checked responsive layout rendering on Desktop (1920x1080) and Mobile viewports (375x812).

---

## 🐛 Key Defects Discovered (Highlights)
* **`BUG-003` (Critical):** *Transfer Funds* allows negative values (`-$50.00`), erroneously crediting the source account and debiting the destination account.
* **`BUG-005` (Critical):** *Bill Pay* allows submission with empty required payee fields without triggering client-side validation.
* **`BUG-009` (Critical):** *Security / Session Management* allows viewing cached account balances via browser Back button immediately after logout.
* **`BUG-011` (High):** *Open New Account* allows submitting a new account request without selecting a valid funding source in edge cases.

---

## 🛠️ Tools & Environment
* **Test Management & Reporting:** Microsoft Excel (Dynamic Formulas, RTM, Defect Log), Markdown
* **Browsers Tested:** Google Chrome (v130), Mozilla Firefox (v131)
* **OS:** Windows 11 / macOS
