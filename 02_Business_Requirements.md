# 📑 Chapter 2: Business Requirements & User Stories

**Project:** ParaBank Online Banking  
**Purpose:** This document defines the functional business requirements (`REQ-01` through `REQ-09`) mapped in the Requirement Traceability Matrix (RTM) and validated across 66 manual test cases.

---

## REQ-01: Customer Registration
* **User Story:** As a new visitor, I want to register an online banking profile with my personal details and unique credentials so that I can access banking services.
* **Acceptance Criteria:**
  * All mandatory fields (First Name, Last Name, Address, City, State, Zip Code, SSN, Username, Password, Confirm Password) must be validated.
  * Password and Confirm Password fields must match; mismatched entries must show a clear error.
  * Duplicate usernames must be rejected with *"This username already exists."*
  * Successful registration automatically logs the user in and displays a welcome message.

## REQ-02: User Authentication & Session Security
* **User Story:** As a registered customer, I want to securely log in and log out of my account so that my financial data remains protected.
* **Acceptance Criteria:**
  * Valid username/password redirects to the **Accounts Overview** page.
  * Invalid credentials or blank fields display an authentication error without revealing which field was incorrect.
  * Clicking **Log Out** invalidates the session; clicking the browser **Back** button must not expose cached account data.

## REQ-03: Account Overview & Opening New Accounts
* **User Story:** As a logged-in customer, I want to view all my existing accounts with real-time balances and open new Checking or Savings accounts.
* **Acceptance Criteria:**
  * Accounts Overview displays Account Number, Balance, Available Amount, and Total Balance accurately.
  * Users can open a new **CHECKING** or **SAVINGS** account funded by an existing account.
  * Newly created accounts immediately appear in the Accounts Overview list with the transferred initial deposit.

## REQ-04: Internal Fund Transfers
* **User Story:** As a customer with multiple accounts, I want to transfer money between my accounts quickly and accurately.
* **Acceptance Criteria:**
  * Transferring a valid positive amount deducts the exact amount from the Source Account and credits the Destination Account.
  * Zero (`0`), negative (`-50`), or non-numeric inputs (`abc`) must be blocked with validation errors.
  * Transfers exceeding the available balance must be rejected (or flagged per overdraft rules).

## REQ-05: Bill Pay Service
* **User Story:** As a customer, I want to pay utility or vendor bills directly from my bank account by entering payee details.
* **Acceptance Criteria:**
  * All payee fields (Name, Address, Phone, Account #, Verify Account #, Amount) are mandatory.
  * `Account #` and `Verify Account #` must match; non-numeric account numbers must be rejected.
  * Payment amount must be positive and within the selected source account's balance.

## REQ-06: Find Transactions
* **User Story:** As a customer, I want to search and filter my transaction history so I can audit specific payments or deposits.
* **Acceptance Criteria:**
  * Users can search transactions by **Transaction ID**, **Exact Date**, **Date Range (From/To)**, or **Amount**.
  * Invalid date formats or end dates earlier than start dates must display a validation warning.

## REQ-07: Update Contact Information
* **User Story:** As a customer, I want to update my mailing address and phone number so my bank records stay current.
* **Acceptance Criteria:**
  * Existing user profile details pre-populate when opening the **Update Contact Info** page.
  * Saving valid changes displays a confirmation message and persists across subsequent logins.
  * Blank mandatory fields (First Name, Last Name, Address, City, State, Zip) cannot be saved.

## REQ-08: Request Loan
* **User Story:** As a customer, I want to apply for a loan online with a specified down payment and receive an instant eligibility decision.
* **Acceptance Criteria:**
  * Loan application requires Loan Amount, Down Payment, and From Account.
  * Down payment cannot exceed the available balance in the funding account.
  * Approved loans generate a new Loan Account number and credit the funds; denied loans display a clear reason.

## REQ-09: UI Responsiveness & Security Controls
* **User Story:** As a user on any device, I want a clean, responsive interface protected against common web vulnerabilities.
* **Acceptance Criteria:**
  * Input fields sanitize special characters/SQL payloads (`' OR '1'='1`).
  * Accessing another user's Account ID directly via URL query parameters is blocked.
  * Navigation menus and tables remain usable on both desktop and mobile screen widths.
