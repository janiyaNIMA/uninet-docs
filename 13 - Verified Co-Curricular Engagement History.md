# Verified Co-Curricular Engagement History & Database Architecture

This document defines the official database schema, table specifications, and SQL initialization scripts for the **Verified Co-Curricular Engagement History** system in the UniNet platform for Wayamba University of Sri Lanka (Faculty of Applied Sciences).

---

## 🛢️ 1. Database Table Specs

### **A. `users` Table (Student Profiles & Points Store)**
- **Note on Primary Key (`id`)**: 
  - If your `users` table uses string identifiers (e.g. `'U001'`, `'U002'`), `id` is `VARCHAR(10)`.
  - If your database uses auto-incrementing integer IDs (e.g. `1`, `2`), `id` is `SERIAL` / `INTEGER`.

### **B. `resume_activities` Table (Verified Co-Curricular Engagement History)**
Stores student leadership roles, project achievements, event involvement, and verification flags for official portfolio exports.

| Column Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | `SERIAL` | Primary Key | Unique record ID |
| `user_id` | `VARCHAR(10)` | FK $\rightarrow$ `users(id)` ON DELETE CASCADE | Target student user ID |
| `role` | `VARCHAR(150)` | Not Null | Designation / Role held (e.g. `Lead Organiser & Student Lead`) |
| `organization` | `VARCHAR(150)` | Not Null | Host society or chapter (e.g. `IEEE Student Branch Chapter`) |
| `event` | `VARCHAR(200)` | Not Null | Specific event or project name |
| `category` | `VARCHAR(100)` | Not Null | Skill classification (`Leadership & Management`, `Technical Skill`, etc.) |
| `period` | `VARCHAR(100)` | Not Null | Active duration period (e.g. `Mar 2025 – May 2025`) |
| `verified` | `BOOLEAN` | Default: `TRUE` | Institutional verification badge flag |
| `points_awarded` | `INT` | Default: `0` | Co-curricular engagement points earned |
| `created_at` | `TIMESTAMP` | Default: `CURRENT_TIMESTAMP` | Record creation timestamp |

---

### **C. `badges` Table (Gamified Digital Badges)**
Stores earned digital badges, point values, categories, icons, and unlock criteria.

| Column Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | `SERIAL` | Primary Key | Unique badge ID |
| `user_id` | `VARCHAR(10)` | FK $\rightarrow$ `users(id)` ON DELETE CASCADE | Student recipient ID |
| `title` | `VARCHAR(150)` | Not Null | Badge title (e.g. `Hackathon Hero`) |
| `category` | `VARCHAR(50)` | Not Null | Badge domain (`Innovation`, `Technical`, `Leadership`, `Creative`) |
| `tier` | `VARCHAR(20)` | `CHECK(tier IN ('Bronze', 'Silver', 'Gold', 'Platinum'))` | Badge tier level |
| `unlocked` | `BOOLEAN` | Default: `TRUE` | Unlock status |
| `points` | `INT` | Default: `0` | Co-curricular points awarded |
| `earned_date` | `VARCHAR(50)` | Nullable | Earned date string (`YYYY-MM-DD`) |
| `icon` | `VARCHAR(20)` | Default: `'🏆'` | Emoji or icon identifier |
| `description` | `TEXT` | Nullable | Achievement criteria summary |

---

## 💻 2. Complete PostgreSQL Initialization Script

### **Option A: For Databases with String User IDs (`'U001'`, `'U002'`)**

```sql
-- 1. Create Primary Users Table with VARCHAR ID
CREATE TABLE IF NOT EXISTS users (
    id VARCHAR(10) PRIMARY KEY,
    username VARCHAR(80) UNIQUE NOT NULL,
    email VARCHAR(120) UNIQUE NOT NULL,
    password_hash VARCHAR(256),
    role VARCHAR(20) DEFAULT 'student',
    full_name VARCHAR(120) DEFAULT 'Jane Doe',
    degree_stream VARCHAR(150) DEFAULT 'BSc (Hons) in Computer Science',
    batch VARCHAR(50) DEFAULT 'Batch of 2022/23',
    badge_tier VARCHAR(50) DEFAULT 'Gold',
    total_points INT DEFAULT 530,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- If users table already exists as INTEGER, run this conversion:
-- ALTER TABLE users ALTER COLUMN id TYPE VARCHAR(10) USING id::text;

-- 2. Create Verifiable Co-Curricular Engagement History Table
CREATE TABLE IF NOT EXISTS resume_activities (
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(10) NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    role VARCHAR(150) NOT NULL,
    organization VARCHAR(150) NOT NULL,
    event VARCHAR(200) NOT NULL,
    category VARCHAR(100) NOT NULL,
    period VARCHAR(100) NOT NULL,
    verified BOOLEAN DEFAULT TRUE,
    points_awarded INT DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 3. Create Gamified Digital Badges Catalog Table
CREATE TABLE IF NOT EXISTS badges (
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(10) REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(150) NOT NULL,
    category VARCHAR(50) NOT NULL,
    tier VARCHAR(20) NOT NULL CHECK (tier IN ('Bronze', 'Silver', 'Gold', 'Platinum')),
    unlocked BOOLEAN DEFAULT TRUE,
    points INT NOT NULL DEFAULT 0,
    earned_date VARCHAR(50),
    icon VARCHAR(20) DEFAULT '🏆',
    description TEXT,
    issuer VARCHAR(100) DEFAULT 'UniNet Campus',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Seed Student User Profiles
INSERT INTO users (id, username, email, role, full_name, degree_stream, batch, badge_tier, total_points)
VALUES
  ('U001', 'jane', 'jane@wusl.ac.lk', 'student', 'Jane Doe', 'BSc (Hons) in Computer Science', 'Batch of 2022/23', 'Gold', 530),
  ('U002', 'leader', 'leader@wusl.ac.lk', 'society_leader', 'Asel Perera', 'BSc (Hons) in Computer Science', 'Batch of 2022/23', 'Silver', 400)
ON CONFLICT (id) DO UPDATE 
SET full_name = EXCLUDED.full_name,
    badge_tier = EXCLUDED.badge_tier,
    total_points = EXCLUDED.total_points;
```

---

### **Option B: For Databases with Integer User IDs (`1`, `2`)**

```sql
-- Seed Student User Profiles with Numeric Integer IDs
INSERT INTO users (id, username, email, role, full_name, degree_stream, batch, badge_tier, total_points)
VALUES
  (1, 'jane', 'jane@wusl.ac.lk', 'student', 'Jane Doe', 'BSc (Hons) in Computer Science', 'Batch of 2022/23', 'Gold', 530),
  (2, 'leader', 'leader@wusl.ac.lk', 'society_leader', 'Asel Perera', 'BSc (Hons) in Computer Science', 'Batch of 2022/23', 'Silver', 400)
ON CONFLICT (id) DO UPDATE 
SET full_name = EXCLUDED.full_name,
    badge_tier = EXCLUDED.badge_tier,
    total_points = EXCLUDED.total_points;
```
