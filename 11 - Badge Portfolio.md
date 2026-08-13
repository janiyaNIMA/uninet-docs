# Gamified Badges & Co-Curricular Portfolio Reference Data

This document defines the official gamification logic, digital badge catalog, co-curricular point thresholds, and the **Verifiable Co-Curricular Engagement History** for student portfolios at Wayamba University of Sri Lanka (Faculty of Applied Sciences).

---

## 🏆 Badge Tier Progression & Thresholds

Students earn **Engagement Points** by registering for and attending workshops, hackathons, sports meets, and organizing committee (OC) roles.

| Tier Level | Minimum Points Required | Tier Color | Unlocked Perks & Privileges |
| :--- | :---: | :---: | :--- |
| **Bronze** | 0 pts | `#CD7F32` | Standard profile display, basic event registration. |
| **Silver** | 250 pts | `#C0C0C0` | Early-bird event notifications, priority OC recruitment listing. |
| **Gold** | 500 pts | `#FFD700` | Featured student badge on Smart Feed, WIE mentor priority access. |
| **Platinum** | 1000 pts | `#E5E4E2` | Verifiable Co-Curricular Resume PDF export for corporate job fairs. |

---

## 📋 Digital Badge Catalog

| ID | Badge Title | Category | Tier | Points Awarded | Icon / Emoji | Trigger Condition / Description |
| :--- | :--- | :--- | :---: | :---: | :---: | :--- |
| 1 | Hackathon Hero | Innovation | Gold | 150 pts | 🏆 | Participated and placed in the top 3 in HackElite or similar hackathons. |
| 2 | Code Sprint Veteran | Technical | Silver | 100 pts | 💻 | Attended 3+ technical coding workshops (CMIS / IEEE / Electronic Society). |
| 3 | WIE Champion | Inclusivity | Gold | 120 pts | 💜 | Active participation in IEEE WIE affinity group workshops or mentorship programs. |
| 4 | Orator Mastery | Leadership | Silver | 90 pts | 🎙️ | Delivered a speech or completed a module in Gavel Club public speaking drives. |
| 5 | Tactical Mind | Sports | Bronze | 50 pts | ♟️ | Participated in university chess tournaments or inter-faculty board meets. |
| 6 | Lens Master | Creative | Bronze | 50 pts | 📸 | Contributed media coverage for a campus event via WireScope Photography. |
| 7 | Lead Organizer | Management | Platinum | 200 pts | 👑 | Served as an Organizing Committee (OC) lead for a major university event. |
| 8 | Eco Warrior | Community | Bronze | 50 pts | 🌿 | Participated in ESOC environmental sustainability or green campus initiatives. |

---

## 📜 Verifiable Co-Curricular Engagement History

The UniNet platform generates an officially verified co-curricular portfolio record for students. Below is the co-curricular engagement history for the two primary seed users (`User U001: Jane Doe` and `User U002: Asel Perera`).

### 👤 User 1: Jane Doe (`U001`)
- **Student ID**: `U001`
- **Full Name**: Jane Doe
- **Degree Stream**: BSc (Hons) in Computer Science
- **Batch**: Batch of 2022/23
- **Badge Tier**: **Gold** (530 total points)
- **Role**: Student (`student`)

| Activity ID | Role / Designation | Organization | Event / Project Name | Category | Period | Verification Status | Points |
| :---: | :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| 1 | Lead Organiser & Student Lead | IEEE Student Branch Chapter | HackElite 2025 Hackathon | Leadership & Management | Mar 2025 – May 2025 | Verified ✅ | 200 pts |
| 2 | Participant & Runner-Up | IEEE Computer Society | Cloud Computing Sprint | Technical Skill | Jun 2026 | Verified ✅ | 150 pts |
| 3 | WIE Ambassador | IEEE Women in Engineering | STEM Outreach Programme | Community & Mentorship | Jul 2026 | Verified ✅ | 100 pts |
| 4 | Sub-Committee Member | Entrepreneurship Club | Pitch Night Vol. 3 | Business & Soft Skills | Jan 2026 | Verified ✅ | 80 pts |

---

### 👤 User 2: Asel Perera (`U002`)
- **Student ID**: `U002`
- **Full Name**: Asel Perera
- **Degree Stream**: BSc (Hons) in Computer Science
- **Batch**: Batch of 2022/23
- **Badge Tier**: **Silver** (400 total points)
- **Role**: Society Leader (`society_leader`)

| Activity ID | Role / Designation | Organization | Event / Project Name | Category | Period | Verification Status | Points |
| :---: | :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| 5 | Chairperson & Head Organiser | Computing & Information Systems Society | CMIS CodeSprint 2025 | Leadership & Management | Feb 2025 – Apr 2025 | Verified ✅ | 200 pts |
| 6 | Technical Lead & Speaker | IEEE Student Branch Chapter | Web Architecture & API Masterclass | Technical Skill | Oct 2025 | Verified ✅ | 100 pts |
| 7 | Event Coordinator | Sports Council | Annual Inter-Faculty Sports Meet 2025 | Sports & Event Ops | Aug 2025 | Verified ✅ | 60 pts |
| 8 | Active Debate Participant | Gavel Club | SpeechCraft 2025 Public Speaking Series | Public Speaking & Communication | Nov 2025 | Verified ✅ | 40 pts |

---

## 🛢️ Neon Database SQL Insert Script

Copy and execute the following SQL script directly in your **Neon Postgres Console SQL Editor**:

```sql
-- 1. Create Badges Table
CREATE TABLE IF NOT EXISTS badges (
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(10) REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(150) NOT NULL,
    category VARCHAR(50) NOT NULL,
    tier VARCHAR(20) NOT NULL CHECK (tier IN ('Bronze', 'Silver', 'Gold', 'Platinum')),
    unlocked BOOLEAN DEFAULT TRUE,
    points INT NOT NULL DEFAULT 0,
    earned_date VARCHAR(50),
    icon VARCHAR(20) DEFAULT '🏅',
    description TEXT,
    issuer VARCHAR(100) DEFAULT 'UniNet Campus',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 2. Create Resume / Co-Curricular Engagement Activities Table
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

-- 3. Insert Badges Data
INSERT INTO badges (id, user_id, title, category, tier, unlocked, points, earned_date, icon, description)
VALUES
  (1, 'U001', 'Hackathon Hero', 'Innovation', 'Gold', TRUE, 150, '2026-05-12', '🏆', 'Participated and placed in top 3 in HackElite 2025.'),
  (2, 'U001', 'Cloud Specialist', 'Technical', 'Silver', TRUE, 100, '2026-06-20', '☁️', 'Completed IEEE CS Cloud Computing workshop series.'),
  (3, 'U001', 'WIE Trailblazer', 'Leadership', 'Gold', TRUE, 200, '2026-07-04', '🌟', 'Led outreach initiative for female undergraduates in STEM.'),
  (4, 'U001', 'Open Source Contributor', 'Community', 'Bronze', TRUE, 80, '2026-07-18', '💻', 'Submitted 3+ merged PRs during FOSS Hacktoberfest.'),
  (5, 'U002', 'Lead Organizer', 'Management', 'Platinum', TRUE, 200, '2025-04-15', '👑', 'Served as Head Organiser for CMIS CodeSprint 2025.'),
  (6, 'U002', 'Code Sprint Veteran', 'Technical', 'Silver', TRUE, 100, '2025-10-20', '💻', 'Delivered Web Architecture & API workshop series.')
ON CONFLICT (id) DO UPDATE 
SET title = EXCLUDED.title,
    category = EXCLUDED.category,
    tier = EXCLUDED.tier,
    points = EXCLUDED.points,
    icon = EXCLUDED.icon,
    description = EXCLUDED.description;

-- 4. Insert Verifiable Co-Curricular Engagement History (User U001 & User U002)
INSERT INTO resume_activities (id, user_id, role, organization, event, category, period, verified, points_awarded)
VALUES
  -- User 1: Jane Doe (U001)
  (1, 'U001', 'Lead Organiser & Student Lead', 'IEEE Student Branch Chapter', 'HackElite 2025 Hackathon', 'Leadership & Management', 'Mar 2025 – May 2025', TRUE, 200),
  (2, 'U001', 'Participant & Runner-Up', 'IEEE Computer Society', 'Cloud Computing Sprint', 'Technical Skill', 'Jun 2026', TRUE, 150),
  (3, 'U001', 'WIE Ambassador', 'IEEE Women in Engineering', 'STEM Outreach Programme', 'Community & Mentorship', 'Jul 2026', TRUE, 100),
  (4, 'U001', 'Sub-Committee Member', 'Entrepreneurship Club', 'Pitch Night Vol. 3', 'Business & Soft Skills', 'Jan 2026', TRUE, 80),

  -- User 2: Asel Perera (U002)
  (5, 'U002', 'Chairperson & Head Organiser', 'Computing & Information Systems Society', 'CMIS CodeSprint 2025', 'Leadership & Management', 'Feb 2025 – Apr 2025', TRUE, 200),
  (6, 'U002', 'Technical Lead & Speaker', 'IEEE Student Branch Chapter', 'Web Architecture & API Masterclass', 'Technical Skill', 'Oct 2025', TRUE, 100),
  (7, 'U002', 'Event Coordinator', 'Sports Council', 'Annual Inter-Faculty Sports Meet 2025', 'Sports & Event Ops', 'Aug 2025', TRUE, 60),
  (8, 'U002', 'Active Debate Participant', 'Gavel Club', 'SpeechCraft 2025 Public Speaking Series', 'Public Speaking & Communication', 'Nov 2025', TRUE, 40)
ON CONFLICT (id) DO UPDATE
SET user_id = EXCLUDED.user_id,
    role = EXCLUDED.role,
    organization = EXCLUDED.organization,
    event = EXCLUDED.event,
    category = EXCLUDED.category,
    period = EXCLUDED.period,
    verified = EXCLUDED.verified,
    points_awarded = EXCLUDED.points_awarded;

-- Reset sequence generators
SELECT setval('badges_id_seq', (SELECT MAX(id) FROM badges));
SELECT setval('resume_activities_id_seq', (SELECT MAX(id) FROM resume_activities));
```