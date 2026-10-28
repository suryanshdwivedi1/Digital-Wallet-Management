<div align="center">

# 💳 Digital Wallet Management System

### Software Requirements Specification & UML Design

**A Software Engineering Project | CSE**

[![Documentation](https://img.shields.io/badge/Documentation-Available-blue)](Team-5_Digital_Wallet_Management_SRS.pdf)
[![UML](https://img.shields.io/badge/UML-7%20Diagrams-purple)](#-uml-design-documentation)
[![Standard](https://img.shields.io/badge/SRS-IEEE%20830--1998-green)](Team-5_Digital_Wallet_Management_SRS.pdf)
[![Status](https://img.shields.io/badge/Project-Requirements%20%26%20Design-orange)](#-project-status)

**Designing a secure, reliable, and maintainable digital wallet management system through structured software engineering practices.**

</div>

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Project Objectives](#-project-objectives)
- [Key Features](#-key-features)
- [System Stakeholders](#-system-stakeholders)
- [System Architecture](#-system-architecture)
- [Core Workflows](#-core-workflows)
- [Security and Reliability](#-security-and-reliability)
- [Requirements Specification](#-requirements-specification)
- [UML Design Documentation](#-uml-design-documentation)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Project Team](#-project-team)
- [Future Scope](#-future-scope)
- [Project Status](#-project-status)
- [License](#-license)

---

## 📖 Overview

The **Digital Wallet Management System (DWMS)** is a Software Engineering project focused on the systematic analysis, specification, and design of a digital financial management platform.

The proposed system enables users to manage digital wallets, add funds, transfer money, make payments, and review transaction histories. It also defines administrative capabilities for monitoring users, reviewing transactions, and maintaining records of important activities.

Because financial applications must preserve data integrity and protect sensitive information, the system emphasizes authentication, authorization, transaction consistency, reliability, auditability, and maintainable architecture.

The project documents these requirements through a Software Requirements Specification (SRS) and a collection of UML diagrams that model the system's structure, behavior, interactions, state transitions, and components.

### Project Information

| Attribute | Details |
|---|---|
| Project Name | Digital Wallet Management System |
| Abbreviation | DWMS |
| Domain | Digital Finance / Financial Management |
| Subject | Software Engineering |
| Documentation | SRS and UML Design Artifacts |
| SRS Format | IEEE Std 830-1998 recommended practice |
| Team | Team 5 |
| Department | Computer Science & Engineering |

---

## 🎯 Problem Statement

Digital financial applications must coordinate user authentication, wallet operations, financial transactions, external payment services, and transaction records while preserving accuracy and security.

A poorly designed system can introduce inconsistent balances, incomplete transfers, unauthorized operations, and insufficient transaction traceability.

DWMS addresses these concerns at the requirements and design level by defining the system's expected behavior, identifying its principal components, and modeling important workflows before implementation.

The project provides a structured foundation for understanding how a digital wallet system should be organized and how its financial operations should behave.

---

## 🚀 Project Objectives

The primary objectives of DWMS are to:

- **Enable digital wallet management:** Support wallet balances, funding operations, and financial activity.
- **Support money transfers:** Define validation and processing rules for transfers between wallet users.
- **Facilitate payment processing:** Specify interactions with external banking and payment services.
- **Maintain transaction integrity:** Preserve consistency between wallet balances and transaction records.
- **Protect user accounts:** Define authentication, authorization, and other appropriate security controls.
- **Improve traceability:** Maintain transaction histories and audit records for relevant operations.
- **Support administrative oversight:** Enable authorized monitoring of users and transactions.
- **Promote modular design:** Separate presentation, application logic, persistence, and external integrations.
- **Establish a foundation for implementation:** Translate requirements into understandable structural and behavioral models.

---

## ✨ Key Features

### 👤 1. User Registration and Authentication

- User registration and account authentication.
- Authentication before access to protected wallet operations.
- Authorization checks for restricted operations.
- Support for additional verification mechanisms where required.

### 💰 2. Wallet Management

- Wallet creation and management.
- Balance viewing.
- Supported wallet funding operations.
- Validation of balance-changing operations.
- Consistent maintenance of wallet records.

### 🔄 3. Money Transfer

- Transfer initiation by the sender.
- Recipient and request validation.
- Sufficient-balance verification.
- Consistent updates to sender and recipient wallets.
- Transaction recording and status tracking.
- Relevant transaction notifications.

**Core design requirement:** A failed transfer must not leave wallet balances partially updated.

### 🏦 4. Payment Processing

- Payment request initiation and validation.
- Integration with external banking or payment gateway services.
- Processing outcome and status recording.
- Appropriate confirmation or failure information.
- Transaction traceability.

### 📜 5. Transaction History

- Recording of financial activities.
- Tracking transaction amounts, types, timestamps, and statuses.
- Access to relevant transaction history.
- Support for authorized administrative monitoring.

### 🔔 6. Notifications

- Notifications for relevant account events.
- Transaction outcome notifications.
- Transfer-related notifications.
- Integration with configured OTP or notification delivery services.

### 🛡️ 7. Administration

- User and transaction monitoring.
- Review of potentially suspicious activity.
- Authorized account-management operations.
- Audit records of administrative actions.

> These are capabilities specified or modeled for the proposed system; their presence in this README does not imply that a working application has already been implemented.

---

## 👥 System Stakeholders

The SRS identifies three principal stakeholder groups.

| Stakeholder | Responsibilities |
|---|---|
| **Customer / User** | Registers, authenticates, manages a wallet, transfers funds, makes payments, and reviews transaction history. |
| **Administrator** | Monitors users and transactions, reviews suspicious activity, and performs authorized administrative operations. |
| **Bank / Payment Gateway** | Supports external financial operations and returns processing or authorization outcomes. |

OTP and notification providers are additional external services used for verification and message delivery.

---

## 🏗️ System Architecture

DWMS uses a **logical layered architecture** to separate user interaction, application services, data persistence, and external integrations.

```text
┌─────────────────────────────────────────────┐
│              System Stakeholders            │
│              Customer / Admin               │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│             PRESENTATION LAYER              │
│              Web / Mobile UI                │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│              APPLICATION LAYER              │
│                                             │
│  Authentication & API                       │
│  Wallet Management                          │
│  Transaction Processing                     │
│  Payment Processing                         │
│  Notifications                              │
│  Administration & Audit                     │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│                 DATA LAYER                  │
│                                             │
│  User Records                               │
│  Wallet Records                             │
│  Transaction Ledger                         │
│  Audit Logs                                 │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│             INTEGRATION LAYER               │
│                                             │
│  Bank / Payment Gateway APIs                │
│  OTP / Notification Services                │
└─────────────────────────────────────────────┘
```

*Conceptual overview of the logical layers. Refer to the component diagram for the modeled software components and their dependencies.*

### Architectural Principles

| Principle | Application in DWMS |
|---|---|
| Separation of Concerns | Presentation, business logic, persistence, and integration have distinct responsibilities. |
| Modularity | Wallet, transaction, payment, notification, and administrative responsibilities are separated. |
| Security | Authentication and authorization are enforced at appropriate boundaries. |
| Data Integrity | Financial operations preserve consistency between balances and transaction records. |
| Maintainability | Changes to external integrations should have minimal impact on unrelated business logic. |
| Auditability | Important financial and administrative operations should be traceable. |
| Reliability | Failed operations must be handled without leaving inconsistent financial records. |

---

## 🔁 Core Workflows

### 1. Money Transfer Workflow

A typical wallet-to-wallet transfer follows these steps:

1. The sender enters the recipient and transfer amount.
2. The wallet interface submits the transfer request.
3. The system validates the request and recipient.
4. The sender's available balance is checked.
5. The transfer is processed with consistent wallet and ledger updates.
6. The transaction outcome is recorded.
7. Relevant notifications are generated.
8. The transaction result is returned to the user.

**Consistency requirement:** The transfer must behave as one logical financial operation. A failure must not leave only one wallet updated.

### 2. Payment Processing Workflow

1. The user initiates a payment.
2. The system validates the payment request.
3. Applicable authentication, authorization, and balance checks are performed.
4. The system communicates with the external payment service.
5. The response is used to determine the payment outcome.
6. The transaction status is recorded.
7. The user receives the result and relevant notification.

### 3. Administrative Monitoring Workflow

1. An administrator accesses the monitoring interface.
2. The system verifies the administrator's authorization.
3. Relevant user or transaction information is reviewed.
4. Authorized administrative operations are performed.
5. Administrative actions are recorded for traceability.

---

## 🔐 Security and Reliability

Security and reliability are essential design concerns for any system that handles digital funds.

The DWMS requirements emphasize the following areas:

| Area | Design Consideration |
|---|---|
| Authentication | Verify user identity before granting access to protected operations. |
| Password Security | Use appropriate password hashing instead of storing plaintext passwords. |
| Authorization | Restrict privileged operations to authorized users. |
| Additional Verification | Support mechanisms such as OTP or multi-factor verification where required. |
| Transaction Integrity | Keep wallet balances and transaction records consistent. |
| Atomic Transfers | Prevent partially applied transfers from leaving inconsistent balances. |
| Auditability | Record important financial and administrative actions. |
| Reliability | Handle processing failures without silently corrupting financial data. |
| Performance | Keep supported operations responsive under the intended workload. |
| Availability | Account for application and external-service availability. |
| Scalability | Structure the system to accommodate future workload growth. |

These considerations define design expectations. Their effectiveness must be verified through implementation, testing, and appropriate security assessment.

---

## 📑 Requirements Specification

The Software Requirements Specification is the primary reference document for the project.

### SRS Contents

- Introduction, purpose, and product scope
- Overall system description
- External interface requirements
- User registration and authentication
- Wallet management
- Money transfer
- Payment processing
- Transaction history
- Notifications
- Administration
- Performance, safety, and security requirements
- Software quality attributes
- Business rules, constraints, and assumptions
- Supporting analysis models

### 📄 Read the SRS

**[View Team-5 Digital Wallet Management SRS (PDF)](Team-5_Digital_Wallet_Management_SRS.pdf)**

The document follows the structure of IEEE Std 830-1998, as stated in the SRS itself.

---

## 📐 UML Design Documentation

The repository includes seven UML lab assignments that model different aspects of the DWMS.

| Lab | Diagram | Description | Document |
|---|---|---|---|
| 03 | Class Diagram | Represents the domain classes, attributes, operations, and relationships. | [View PDF](Lab_03_UML_Class_Diagram.pdf) |
| 04 | Activity Diagram | Models activity flows, decisions, and alternative paths. | [View PDF](Lab_04_Activity_Diagram.pdf) |
| 05 | Sequence Diagram — Money Transfer | Describes the interactions between participants during a wallet transfer. | [View PDF](Lab_05_Sequence_Diagram_Money_Transfer.pdf) |
| 06 | Sequence Diagram — Payment Processing | Models the interactions involved in processing a payment. | [View PDF](Lab_06_Sequence_Diagram_Payment_Processing.pdf) |
| 07 | Collaboration / Communication Diagram | Illustrates collaborating objects and their numbered messages during a transfer. | [View PDF](DWMS_Collaboration_Diagram_LAB7.pdf) |
| 08 | State Transition Diagram | Represents states and transitions of the modeled system entity. | [View PDF](Lab_08_State_Transition_Diagram.pdf) |
| 09 | Component Diagram | Shows software components, responsibilities, and dependencies. | [View PDF](Lab_09_Component_Diagram.pdf) |

### Why These Diagrams Matter

Together, these models provide complementary views of the system:

- **Structural view:** Class and component diagrams.
- **Behavioral view:** Activity and state transition diagrams.
- **Interaction view:** Sequence and collaboration diagrams.

These artifacts help connect the requirements to the proposed design and provide a foundation for future implementation and testing.

### Additional Assignment

The repository also includes an additional Software Engineering assignment:

[View Suryansh's Software Engineering Assignment 2 (PDF)](202401100200315_Suryansh_SEDP_Assignment_2.pdf)

---

## 📁 Repository Structure

The following tree reflects the files currently present in the repository root.

```text
Digital-Wallet-Management/
│
├── README.md
│
├── Team-5_Digital_Wallet_Management_SRS.pdf
│
├── Lab_03_UML_Class_Diagram.pdf
├── Lab_04_Activity_Diagram.pdf
├── Lab_05_Sequence_Diagram_Money_Transfer.pdf
├── Lab_06_Sequence_Diagram_Payment_Processing.pdf
├── DWMS_Collaboration_Diagram_LAB7.pdf
├── Lab_08_State_Transition_Diagram.pdf
├── Lab_09_Component_Diagram.pdf
│
└── 202401100200315_Suryansh_SEDP_Assignment_2.pdf
```

**Repository note:** The SRS and UML PDFs are currently stored in the root directory. The README links use those existing filenames, so a separate `docs/` directory is not required.

---

## ⚙️ Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/suryanshdwivedi1/Digital-Wallet-Management.git
```

### 2. Navigate to the Project

```bash
cd Digital-Wallet-Management
```

### 3. Explore the Documentation

Open `README.md` for the project overview, then review the SRS and UML PDFs for detailed requirements and design models.

For example, on Linux:

```bash
xdg-open Team-5_Digital_Wallet_Management_SRS.pdf
```

To open a UML assignment:

```bash
xdg-open Lab_03_UML_Class_Diagram.pdf
```

A PDF viewer is required to read the documents.

### Implementation Status

This repository currently serves as a **requirements and design documentation project**. The documented workflow describes the intended system; it is not a set of installation instructions for a running wallet application.

Application dependencies, environment variables, database configuration, and runtime commands should be added if and when an executable implementation is included.

---

## 👨‍💻 Project Team

**Team 5 — Department of Computer Science & Engineering**

| Team Member | Student ID |
|---|---|
| Suryansh Dwivedi | 2400290100314 |
| Shubh Tiwari | 2400290100296 |
| Subrat Dwivedi | 2400290100311 |
| Tejasvi Gupta | 2400290100322 |

### Contributions

The team prepared the Software Requirements Specification and supporting software design documentation for the Digital Wallet Management System.

The UML assignments cover the system's structural organization, activity flows, transaction interactions, state transitions, and component dependencies.

---

## 🔮 Future Scope

The project can be extended toward implementation and validation through the following activities:

- Develop a functional web or mobile wallet application.
- Implement user registration, authentication, and authorization.
- Build wallet and transaction management services.
- Integrate supported external payment gateway APIs.
- Implement transaction consistency controls and failure handling.
- Add automated unit, integration, and system tests.
- Introduce security testing and transaction integrity checks.
- Develop administrative monitoring and audit interfaces.
- Add performance testing and monitoring.
- Document deployment, configuration, and operational procedures.

These are potential future enhancements, not claims of currently available features.

---

## 📌 Project Status

**Current focus:** Software requirements analysis and UML design documentation.

| Deliverable | Status |
|---|---|
| Software Requirements Specification | Available |
| UML Class Diagram | Available |
| UML Activity Diagram | Available |
| Money Transfer Sequence Diagram | Available |
| Payment Processing Sequence Diagram | Available |
| Collaboration / Communication Diagram | Available |
| State Transition Diagram | Available |
| Component Diagram | Available |
| Executable Application | Not documented in this repository's current file listing |

---

## 📄 License

No license file is currently listed in the repository.

Until a license is selected and added, do not assume that the project is licensed for unrestricted reuse, redistribution, or modification.

---

<div align="center">

### Digital Wallet Management System

**Requirements • Architecture • UML • Software Engineering**

</div>
