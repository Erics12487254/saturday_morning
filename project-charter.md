# Project Charter

## 1. Project Overview & Charter
* **Project Name:** [Fitora]
* **Project Goal:** [Brief description of what your project aims to achieve]
* **Target Audience:** [Who will use this platform/system]
* **Key Team Roles:** 
  * Lead Developer: [Name]
  * Frontend/UI: [Name]
  * Backend/Database: [Name]

---

## 2. Requirements Specification

### Functional Requirements
* **FR-01:** Users must be able to create an account and log in securely.
* **FR-02:** The system must allow users to view, search, and filter primary features/items.
* **FR-03:** Users must be able to submit form data and receive dynamic feedback or recommendations.
* **FR-04:** Administrators can manage database entries through an admin dashboard.

### Non-Functional Requirements
* **NFR-01 (Performance):** The system should load page content in under 2 seconds.
* **NFR-02 (Security):** User credentials and API keys must be securely encrypted and stored using environment variables.
* **NFR-03 (Usability):** The application interface must be fully responsive on mobile and desktop screens.

---

## 3. Acceptance Criteria
* [ ] **User Authentication:** Sign-up and login forms correctly validate inputs and restrict unauthenticated access to protected routes.
* [ ] **Core Workflow:** Users can complete the primary project task end-to-end without system crashes.
* [ ] **API & Logic Integration:** Input data correctly triggers the backend or AI processing and returns expected results to the frontend.
* [ ] **Repository Structure:** All source code and documentation (`docs/project-charter.md`) are properly structured and available in the public GitHub repository.

---

## 4. Database Design

### Data Entities & Schema

#### Entity: Users
| Field Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `user_id` | INT | Primary Key, Auto Increment | Unique identifier for each user |
| `username` | VARCHAR(50) | UNIQUE, NOT NULL | Account login username |
| `email` | VARCHAR(100) | UNIQUE, NOT NULL | User contact email |
| `password_hash` | VARCHAR(255) | NOT NULL | Encrypted user password |
| `created_at` | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date account was created |

#### Entity: Projects / Submissions
| Field Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `item_id` | INT | Primary Key, Auto Increment | Unique record identifier |
| `user_id` | INT | Foreign Key (Users) | References the owner of the record |
| `title` | VARCHAR(150) | NOT NULL | Title or entry name |
| `description` | TEXT | NULLABLE | Detailed description or payload |
| `status` | VARCHAR(20) | DEFAULT 'active' | Current state of the item |

### Entity Relationships
* **User to Submissions (1:N):** A single user can create multiple entries or submissions, but each submission belongs to exactly one user.