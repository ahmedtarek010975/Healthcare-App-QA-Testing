# HealthCare3 — Bug Report Log
**Module:** Authentication & Access Control (HLTHCR3-2)

---

## HLTHCR3-101 — Date of Birth Accepts Users Strictly Under 18 Years Old (17 years, 364 days)

### Meta Data
| Field | Value |
|---|---|
| **Bug ID** | HLTHCR3-101 |
| **Status** | Done |
| **Priority (Ticket Field)** | Medium |
| **Priority (Test Case)** | High |
| **Severity** | Medium |
| **Type** | Bug |
| **Reporter** | Ahmed Tarek |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | HP ZBook Workstation G5 |
| **Linked Test Case** | Relates to HLTHCR3-66 — *Verify Date of Birth rejects ages under...* (Done) |
| **Created / Resolved** | 09/Sep/26 — 11/Sep/26 |

### Description
The system fails to validate the exact age boundary. It accepts a date of birth that makes the user 1 day short of 18 years old, violating the business requirement that users must be exactly 18 or older.

### Steps to Reproduce
1. Open the register page. (Note: the current system date is 09/09/2026.)
2. Fill all mandatory fields (Name, Email/Phone, Password, and Confirm Password) with valid data.
3. In the Date of Birth field, enter **09/10/2008** (this makes the user exactly 17 years and 364 days old today).
4. Click on the "Register" button.

### Expected Result
- The system blocks form submission for this attempt.
- An inline error is displayed indicating that the date must be in the past and the age must be 18 years relative to the system date.

### Actual Result
The system accepts the date of birth, bypasses the age restriction, and successfully registers the account.

### Attachments Reference
- 
- [Watch Video: 66.mp4](./66.mp4)
---

## HLTHCR3-102 — Phone Number Accepts Invalid Egyptian Prefixes (e.g., 013)

### Meta Data
| Field | Value |
|---|---|
| **Bug ID** | HLTHCR3-102 |
| **Status** | Done |
| **Priority** | Medium |
| **Severity** | Medium |
| **Type** | Bug |
| **Reporter** | Ahmed Tarek |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | HP ZBook Workstation G5 |
| **Linked Test Case** | Relates to HLTHCR3-50 — *Verify Phone Number rejects invalid l...* (Done) |
| **Created / Resolved** | 09/Sep/26 — 11/Sep/26 |

### Description
The system fails to validate the carrier prefix of the phone number. It successfully accepts and processes a phone number starting with an unsupported/invalid prefix (013), violating the business requirement that restricts inputs to valid Egyptian prefixes (010, 011, 012, 015).

### Steps to Reproduce
1. Open the register page.
2. Fill all mandatory fields with valid data EXCEPT the phone number.
3. Enter a phone number with an invalid prefix: **0131234568**.
4. Click "Register."

### Expected Result
The system should block the registration and display a validation error indicating that the phone number must start with a valid Egyptian network prefix (010, 011, 012, or 015).

### Actual Result
The system accepts the invalid prefix, bypasses validation, and successfully registers the account.

### Attachments Reference
- [Watch Video: 67.mp4](./67.mp4)

---

## HLTHCR3-109 — Email Validation Accepts Invalid Formats (Consecutive Dots in Domain)

### Meta Data
| Field | Value |
|---|---|
| **Bug ID** | HLTHCR3-109 |
| **Status** | Done |
| **Priority** | Medium |
| **Severity** | Medium |
| **Type** | Bug |
| **Reporter** | Ahmed Tarek |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | HP ZBook Workstation G5 |
| **Linked Test Case** | Relates to HLTHCR3-47 — *Verify Email Address rejects invalid...* (Done) |
| **Created / Resolved / Due** | 09/Sep/26 — 11/Sep/26 |

### Description
The email validation logic is insufficient. It successfully accepts an email address containing consecutive dots (`..`) in the domain part (e.g., `a@ab..c`), which violates standard email formatting rules (RFC standards).

### Steps to Reproduce
1. Open the register page.
2. Fill all mandatory fields with valid data, excepting the email address.
3. Enter an email missing the domain: `a@ab..c`.
4. Click on "Register."

### Expected Result
- The system blocks form submission for this attempt.
- An inline error is displayed indicating that the email format is invalid (must match standard RFC 5322 format).

### Actual Result
The system bypasses validation, accepts the invalid email, and successfully creates the account.

### Attachments Reference
- [Watch Video: 68.mp4](./68.mp4)

---

## HLTHCR3-113 — Password Exposed in Plain Text Within localStorage After Registration

### Meta Data
| Field | Value |
|---|---|
| **Bug ID** | HLTHCR3-113 |
| **Status** | Done |
| **Priority (Ticket Field)** | Medium |
| **Priority (Test Case)** | High |
| **Severity** | High |
| **Type** | Bug |
| **Reporter** | Ahmed Tarek |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | HP ZBook Workstation G5 |
| **Linked Test Case** | Relates to HLTHCR3-112 — *Verify password is not exposed in pla...* (Done) |
| **Created / Resolved** | 09/Sep/26 — 11/Sep/26 |

### Description
The system stores the user's password in plain text within the browser's localStorage after a successful registration. This violates the security requirement (NFR-03), which strictly prohibits exposing sensitive data in raw text logs. Any user with physical access to the device or malicious scripts can easily extract the password.

### Steps to Reproduce
1. Open the browser's Developer Tools (F12).
2. Navigate to the Application tab.
3. Expand Local Storage from the left sidebar and click on the application URL.
4. Fill the registration form with valid data (Password used: `Ahmed@2027`).
5. Click on the "Register" button.
6. Inspect the key-value pairs generated in the Local Storage panel.

### Expected Result
The system should maintain state across sessions but must NOT expose the password in raw text logs. The password field should either be omitted from storage or properly hashed/encrypted.

### Actual Result
The password `Ahmed@2027` is clearly visible and stored as a plain text string in the Local Storage panel.

### Attachments Reference
- [Watch Video: 110.mp4](./110.mp4)

---
