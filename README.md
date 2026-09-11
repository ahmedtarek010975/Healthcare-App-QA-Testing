# CareNest Clinic Booking System - QA & Security Audit

🔗 **Live Target Application:** [CareNest Clinic Booking](https://ahmedsayed28.github.io/Clinic-Booking-App/index.html)

## 📌 Project Overview
A comprehensive Manual Quality Assurance and Client-Side Security Assessment for the "CareNest" healthcare appointment booking platform. This project demonstrates strict adherence to Software Testing Life Cycle (STLC) principles, blending Functional validation with Web Penetration Testing methodologies.

## 🎯 Scope of Work
* **Functional Testing:** Validated core features (Registration, Authentication) using Boundary Value Analysis (BVA) and Equivalence Partitioning (EP).
* **Security Testing:** Conducted client-side vulnerability assessments focusing on state persistence, authentication flaws, and sensitive data exposure.
* **Responsive/UI Testing:** Ensured layout integrity and user experience across multiple device viewports.
* **Defect Management:** Documented and tracked bugs using Jira with full traceability back to original requirements.

## 🔍 Key Discoveries & Bug Reports
| Bug ID | Vulnerability / Defect | Severity | Category | Description |
| :--- | :--- | :--- | :--- | :--- |
| **SEC-01** | Plaintext Password Exposure | Critical | Security | System stored user passwords in raw text within browser `localStorage` post-registration. |
| **FUN-01** | DOB Minimum Age Bypass | Major | Functional (BVA) | System accepted a user exactly 17 years and 364 days old, failing the >=18 age restriction. |
| **FUN-02** | Invalid Telecom Prefix | Moderate | Functional (EP) | Phone validation logic incorrectly accepted the invalid Egyptian carrier prefix '013'. |
| **FUN-03** | Malformed Email Acceptance | Medium | Input Validation | Validation regex failed by accepting malformed domains with consecutive dots. |

## 📂 Repository Structure
* `/Requirements`: Contains the original Software Requirements Specification (SRS) document, serving as the baseline for all test cases and traceability.
* `/Test_Cases`: Contains the `Testcases.pdf` file covering all 22 executed Functional and Security test scenarios extracted from Jira.
* `/Bug_Reports`: Contains detailed Markdown and PDF reports alongside **full video evidence (.mp4)** for all critical bugs and vulnerabilities.

## 🛠️ Tools & Methodologies Used
* **Testing Techniques:** Black-box testing, Boundary Value Analysis, Equivalence Partitioning.
* **Security & Inspection:** Chrome Developer Tools (Network & Application tabs), State Persistence Analysis.
* **Test Management:** Jira (Test Execution, Bug Tracking, Traceability).
