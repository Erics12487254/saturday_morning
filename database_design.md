# Database Design

## Schema & Tables

### Entity: Users
| Field Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `user_id` | INT | Primary Key, Auto Increment | Unique user identifier |
| `username` | VARCHAR(50) | UNIQUE, NOT NULL | Account handle |
| `email` | VARCHAR(100) | UNIQUE, NOT NULL | User contact email |
| `password_hash` | VARCHAR(255) | NOT NULL | Encrypted password string |
| `created_at` | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Account creation timestamp |

### Entity: Data_Logs / Submissions
| Field Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `submission_id` | INT | Primary Key, Auto Increment | Unique record ID |
| `user_id` | INT | Foreign Key (Users) | Owner reference |
| `title` | VARCHAR(150) | NOT NULL | Entry title |
| `payload` | TEXT | NULLABLE | Content body / submission payload |
| `created_at` | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Submission timestamp |

## Entity Relationships
* **Users to Submissions (1:N):** One user can own multiple submission records, but each record belongs strictly to one user.