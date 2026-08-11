# University Societies & Clubs Reference Data

This document contains the official seed dataset and schema specifications for societies and clubs at Wayamba University of Sri Lanka (Faculty of Applied Sciences). It is **100% compatible** with the backend `Society` SQLAlchemy model in `uninet-backend/src/uninet/models.py` and the PostgreSQL `societies` database table.

---

## 📋 Society Data Catalog

| ID | Society / Club Name | Short Name | Category | Description | Committee Members (ExCom) | Past Events | Primary Target Modules / Keywords | WIE Chapter |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---: |
| 1 | Computing & Information Systems Society | CMIS Society | Technical | Premier society for computing, software engineering, web development, and IT innovation. | • Asel Perera (Chairperson)<br>• Kasun Silva (Vice Chair)<br>• Nimal Fernando (Secretary)<br>• Dilan Raj (Treasurer) | • HackElite 2025<br>• Full-Stack Web Sprint<br>• AI & Data Science Workshop<br>• Cloud DevFest 2025 | CMIS, Web Development, Full-Stack, AI | ❌ |
| 2 | Environmental Science Society | ESOC | Academic | Fosters environmental sustainability, ecological research, and green campus initiatives. | • Kavindi Bandara (President)<br>• Sahan Perera (Vice President)<br>• Nuwanthi Silva (Secretary)<br>• Tharindu Jayasinghe (Treasurer) | • Green Campus Tree Planting Drive 2025<br>• EcoTech Innovation Forum<br>• Biodiversity Survey & Hike<br>• Plastic Recycling Awareness Week | Environmental Science, Biology, Sustainability | ❌ |
| 3 | Mathematical Society | Math Society | Academic | Drives passion for pure/applied mathematics, data analysis, and competitive problem-solving. | • Ruwan Bandara (President)<br>• Chamari Dias (Vice President)<br>• Dilini Wickramasinghe (Secretary)<br>• Mahesh Karunaratne (Treasurer) | • Inter-University Math Olympiad 2025<br>• Data Analytics Workshop<br>• LaTeX Academic Writing Bootcamp<br>• Pi Day Quiz Championship | MATH, Applied Math, Statistics, Logic | ❌ |
| 4 | Industrial Management Society | IMGT Society | Business | Bridges management science, operations research, supply chain, and entrepreneurship. | • Malith Jayasuriya (President)<br>• Hiruni Wijesinghe (Vice President)<br>• Ravindu Perera (Secretary)<br>• Dinushi Alwis (Treasurer) | • Supply Chain Management Summit 2025<br>• Lean Six Sigma Workshop<br>• Young Entrepreneurs Pitch Night<br>• Industry 4.0 & Logistics Expo | IMGT, Management, Business Analytics | ❌ |
| 5 | Electronics Society | Electronic Society | Technical | Hub for hardware engineering, embedded systems, IoT development, and robotics. | • Kaveen Rathnayake (President)<br>• Janith Senanayake (Vice President)<br>• Shenali Fonseka (Secretary)<br>• Prabath Kumara (Treasurer) | • Arduino & Robotics Bootcamp 2025<br>• IoT Smart Campus Challenge<br>• PCB Design Masterclass<br>• Hardware Hackathon 2025 | ELTN, Embedded Systems, IoT, Hardware | ❌ |
| 6 | IEEE Student Branch Chapter | IEEE Society | Technical | Flagship global technical community driving workshops, competitions, and professional growth. | • Asel Perera (Chairperson)<br>• Sanduni Wickrama (Vice Chair)<br>• Thilini Jayawardena (Secretary)<br>• Dilan Raj (Treasurer) | • HackElite 2025 Hackathon<br>• IEEE Day Celebrations 2025<br>• Technical Writing & Research Series<br>• WIE Leadership Summit 2025 | Engineering, IT, Research, Networking | ❌ |
| 7 | Gavel Club | Gavel Club | Leadership | Public speaking, communication mastery, and Toastmasters-aligned leadership development. | • Nipuni Jayawardena (President)<br>• Tharindu Fernando (VP Education)<br>• Anuki Mendis (VP Public Relations)<br>• Chathura Madawala (Secretary) | • SpeechCraft 2025 Workshop<br>• Inter-Faculty Impromptu Speech Contest<br>• Toastmasters Leadership Summit<br>• Humorous Speech Championship | Public Speaking, Leadership, Soft Skills | ❌ |
| 8 | WireScope Photography Society | WireScope | Creative | Photography, digital media creation, event coverage, and visual storytelling. | • Pathum Herath (President)<br>• Rashmi Gunawardena (Vice President)<br>• Ishan Liyanage (Secretary)<br>• Amanda Cooray (Treasurer) | • Focus 2025 Annual Photo Exhibition<br>• Portrait & Landscape Workshop<br>• Inter-Faculty Short Film Fest<br>• Digital Media & Lightroom Editing | Photography, Videography, Media, Editing | ❌ |
| 9 | Wire Explorers | Wire Explorers | Adventure | Outdoor adventures, hiking, community exploration, and youth engagement. | • Danushka Wickramaratne (Leader)<br>• Isuru Jayasundara (Co-Leader)<br>• Keshani Abeywickrama (Secretary)<br>• Lakshan Rodrigo (Treasurer) | • Ella Rock Hiking Expedition 2025<br>• Knuckles Wilderness Survival Camp<br>• River Rafting & Team Building<br>• Coastal Clean-up & Campfire Night | Outdoor, Adventure, Team Building | ❌ |
| 10 | Chess Club | Chess Club | Sports | Strategic board gaming, university tournament training, and tactical analysis. | • Supun Gamage (Captain)<br>• Madusha Peiris (Vice Captain)<br>• Oshada Samarasinghe (Secretary)<br>• Piyumi Senanayake (Treasurer) | • Inter-Faculty Chess Championship 2025<br>• Grandmaster Simul Exhibition Match<br>• Rapid Chess Arena 2025<br>• Tactical Opening Masterclass | Chess, Strategy, Tactics, Mind Sports | ❌ |
| 11 | Badminton Club | Badminton Club | Sports | Indoor racket sports, university athletic meets, and physical endurance training. | • Sachini Liyanage (Captain)<br>• Charith De Silva (Vice Captain)<br>• Nimasha Perera (Secretary)<br>• Harsha Abeykoon (Treasurer) | • Annual Inter-Faculty Badminton 2025<br>• Mixed Doubles Smash Cup<br>• Varsity Fitness & Agility Clinic<br>• Novices Racket Championship 2025 | Sports, Badminton, Fitness, Athletics | ❌ |
| 12 | Cricket Club | Cricket Club | Sports | University varsity cricket, competitive matches, and inter-faculty tournaments. | • Chathura Madawala (Captain)<br>• Roshen Silva (Vice Captain)<br>• Dasun Fernando (Secretary)<br>• Bhanuka Gunatilake (Treasurer) | • Wayamba Premier League (WPL) 2025<br>• Inter-Faculty Sixes Tournament<br>• Annual Varsity Encounter Match<br>• Leather Ball Cricket Clinic | Sports, Cricket, Athletics, Teamwork | ❌ |

---

## 👥 Committee Members (ExCom) & Past Events Detailed Specification

Below is the structured breakdown of Executive Committee (ExCom) leadership members and historical past events for each society, fully serialized in JSON format for backend seeding:

### 1. Computing & Information Systems Society (CMIS Society)
- **Executive Committee (ExCom)**:
  - **Asel Perera** — Chairperson (Initials: `AP`)
  - **Kasun Silva** — Vice Chair (Initials: `KS`)
  - **Nimal Fernando** — Secretary (Initials: `NF`)
  - **Dilan Raj** — Treasurer (Initials: `DR`)
- **Past Events**:
  1. HackElite 2025
  2. Full-Stack Web Sprint
  3. AI & Data Science Workshop
  4. Cloud DevFest 2025

### 2. Environmental Science Society (ESOC)
- **Executive Committee (ExCom)**:
  - **Kavindi Bandara** — President (Initials: `KB`)
  - **Sahan Perera** — Vice President (Initials: `SP`)
  - **Nuwanthi Silva** — Secretary (Initials: `NS`)
  - **Tharindu Jayasinghe** — Treasurer (Initials: `TJ`)
- **Past Events**:
  1. Green Campus Tree Planting Drive 2025
  2. EcoTech Innovation Forum
  3. Biodiversity Survey & Hike
  4. Plastic Recycling Awareness Week

### 3. Mathematical Society (Math Society)
- **Executive Committee (ExCom)**:
  - **Ruwan Bandara** — President (Initials: `RB`)
  - **Chamari Dias** — Vice President (Initials: `CD`)
  - **Dilini Wickramasinghe** — Secretary (Initials: `DW`)
  - **Mahesh Karunaratne** — Treasurer (Initials: `MK`)
- **Past Events**:
  1. Inter-University Math Olympiad 2025
  2. Data Analytics Workshop
  3. LaTeX Academic Writing Bootcamp
  4. Pi Day Quiz Championship

### 4. Industrial Management Society (IMGT Society)
- **Executive Committee (ExCom)**:
  - **Malith Jayasuriya** — President (Initials: `MJ`)
  - **Hiruni Wijesinghe** — Vice President (Initials: `HW`)
  - **Ravindu Perera** — Secretary (Initials: `RP`)
  - **Dinushi Alwis** — Treasurer (Initials: `DA`)
- **Past Events**:
  1. Supply Chain Management Summit 2025
  2. Lean Six Sigma Workshop
  3. Young Entrepreneurs Pitch Night
  4. Industry 4.0 & Logistics Expo

### 5. Electronics Society (Electronic Society)
- **Executive Committee (ExCom)**:
  - **Kaveen Rathnayake** — President (Initials: `KR`)
  - **Janith Senanayake** — Vice President (Initials: `JS`)
  - **Shenali Fonseka** — Secretary (Initials: `SF`)
  - **Prabath Kumara** — Treasurer (Initials: `PK`)
- **Past Events**:
  1. Arduino & Robotics Bootcamp 2025
  2. IoT Smart Campus Challenge
  3. PCB Design Masterclass
  4. Hardware Hackathon 2025

### 6. IEEE Student Branch Chapter (IEEE Society)
- **Executive Committee (ExCom)**:
  - **Asel Perera** — Chairperson (Initials: `AP`)
  - **Sanduni Wickrama** — Vice Chair (Initials: `SW`)
  - **Thilini Jayawardena** — Secretary (Initials: `TJ`)
  - **Dilan Raj** — Treasurer (Initials: `DR`)
- **Past Events**:
  1. HackElite 2025 Hackathon
  2. IEEE Day Celebrations 2025
  3. Technical Writing & Research Series
  4. WIE Leadership Summit 2025

### 7. Gavel Club (Gavel Club)
- **Executive Committee (ExCom)**:
  - **Nipuni Jayawardena** — President (Initials: `NJ`)
  - **Tharindu Fernando** — VP Education (Initials: `TF`)
  - **Anuki Mendis** — VP Public Relations (Initials: `AM`)
  - **Chathura Madawala** — Secretary (Initials: `CM`)
- **Past Events**:
  1. SpeechCraft 2025 Workshop
  2. Inter-Faculty Impromptu Speech Contest
  3. Toastmasters Leadership Summit
  4. Humorous Speech Championship

### 8. WireScope Photography Society (WireScope)
- **Executive Committee (ExCom)**:
  - **Pathum Herath** — President (Initials: `PH`)
  - **Rashmi Gunawardena** — Vice President (Initials: `RG`)
  - **Ishan Liyanage** — Secretary (Initials: `IL`)
  - **Amanda Cooray** — Treasurer (Initials: `AC`)
- **Past Events**:
  1. Focus 2025 Annual Photo Exhibition
  2. Portrait & Landscape Workshop
  3. Inter-Faculty Short Film Fest
  4. Digital Media & Lightroom Editing

### 9. Wire Explorers (Wire Explorers)
- **Executive Committee (ExCom)**:
  - **Danushka Wickramaratne** — Leader (Initials: `DW`)
  - **Isuru Jayasundara** — Co-Leader (Initials: `IJ`)
  - **Keshani Abeywickrama** — Secretary (Initials: `KA`)
  - **Lakshan Rodrigo** — Treasurer (Initials: `LR`)
- **Past Events**:
  1. Ella Rock Hiking Expedition 2025
  2. Knuckles Wilderness Survival Camp
  3. River Rafting & Team Building
  4. Coastal Clean-up & Campfire Night

### 10. Chess Club (Chess Club)
- **Executive Committee (ExCom)**:
  - **Supun Gamage** — Captain (Initials: `SG`)
  - **Madusha Peiris** — Vice Captain (Initials: `MP`)
  - **Oshada Samarasinghe** — Secretary (Initials: `OS`)
  - **Piyumi Senanayake** — Treasurer (Initials: `PS`)
- **Past Events**:
  1. Inter-Faculty Chess Championship 2025
  2. Grandmaster Simul Exhibition Match
  3. Rapid Chess Arena 2025
  4. Tactical Opening Masterclass

### 11. Badminton Club (Badminton Club)
- **Executive Committee (ExCom)**:
  - **Sachini Liyanage** — Captain (Initials: `SL`)
  - **Charith De Silva** — Vice Captain (Initials: `CS`)
  - **Nimasha Perera** — Secretary (Initials: `NP`)
  - **Harsha Abeykoon** — Treasurer (Initials: `HA`)
- **Past Events**:
  1. Annual Inter-Faculty Badminton 2025
  2. Mixed Doubles Smash Cup
  3. Varsity Fitness & Agility Clinic
  4. Novices Racket Championship 2025

### 12. Cricket Club (Cricket Club)
- **Executive Committee (ExCom)**:
  - **Chathura Madawala** — Captain (Initials: `CM`)
  - **Roshen Silva** — Vice Captain (Initials: `RS`)
  - **Dasun Fernando** — Secretary (Initials: `DF`)
  - **Bhanuka Gunatilake** — Treasurer (Initials: `BG`)
- **Past Events**:
  1. Wayamba Premier League (WPL) 2025
  2. Inter-Faculty Sixes Tournament
  3. Annual Varsity Encounter Match
  4. Leather Ball Cricket Clinic

---

## 🛢️ Society Database Mapping & Field Specifications

The backend `societies` table maps directly to the SQLAlchemy `Society` model defined in [`models.py`](file:///home/janidu/workbench/Hackelite/uninet-backend/src/uninet/models.py):

| Column Name | PostgreSQL Data Type | SQLAlchemy Type | Constraints | Description |
| :--- | :--- | :--- | :--- | :--- |
| `id` | `VARCHAR(10)` | `db.String(10)` | Primary Key | Society unique ID string (e.g., `'1'`, `'2'`, `'SOC001'`) |
| `name` | `VARCHAR(120)` | `db.String(120)` | Not Null | Official society name |
| `short_name` | `VARCHAR(50)` | `db.String(50)` | Nullable | Abbreviated name (e.g., `'CMIS Society'`) |
| `category` | `VARCHAR(50)` | `db.String(50)` | Nullable | Category (`'Technical'`, `'Academic'`, `'Business'`, `'Leadership'`, `'Creative'`, `'Adventure'`, `'Sports'`) |
| `description` | `TEXT` | `db.Text` | Nullable | Full society description |
| `past_events` | `TEXT` | `db.Text` | Default `'[]'` | JSON string array of historical event titles |
| `skills` | `TEXT` | `db.Text` | Default `'[]'` | JSON string array of primary target keywords and skills |
| `excom` | `TEXT` | `db.Text` | Default `'[]'` | JSON string array of Executive Committee members (`[{"name": "...", "role": "...", "initials": "..."}]`) |
| `member_count` | `INTEGER` | `db.Integer` | Default `100` | Total active members |
| `color` | `VARCHAR(30)` | `db.String(30)` | Default `'#1565C0'` | UI theme badge / card accent color hex code |
| `is_wie` | `BOOLEAN` | `db.Boolean` | Default `FALSE` | WIE affinity group indicator |
| `mentor_available` | `BOOLEAN` | `db.Boolean` | Default `FALSE` | Availability of dedicated society mentors |
| `created_at` | `TIMESTAMP` | `db.DateTime` | Default `UTC Now` | Record creation timestamp |

---

## 🛢️ SQL DDL & Data Seeding Script (Neon PostgreSQL Compatible)

Copy and execute the following SQL script directly in your **Neon Postgres Console SQL Editor**:

```sql
-- Ensure societies table matches SQLAlchemy model schema
CREATE TABLE IF NOT EXISTS societies (
    id VARCHAR(10) PRIMARY KEY,
    name VARCHAR(120) NOT NULL,
    short_name VARCHAR(50),
    category VARCHAR(50),
    description TEXT,
    past_events TEXT DEFAULT '[]',
    skills TEXT DEFAULT '[]',
    excom TEXT DEFAULT '[]',
    member_count INTEGER DEFAULT 100,
    color VARCHAR(30) DEFAULT '#1565C0',
    is_wie BOOLEAN DEFAULT FALSE,
    mentor_available BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Insert / Upsert 12 Official University Societies Data with Complete ExCom & Past Events
INSERT INTO societies (id, name, short_name, category, description, past_events, skills, excom, member_count, color, is_wie, mentor_available)
VALUES
  (
    '1', 
    'Computing & Information Systems Society', 
    'CMIS Society', 
    'Technical', 
    'Premier society for computing, software engineering, web development, and IT innovation.', 
    '["HackElite 2025", "Full-Stack Web Sprint", "AI & Data Science Workshop", "Cloud DevFest 2025"]', 
    '["CMIS", "Web Development", "Full-Stack", "AI"]', 
    '[{"name": "Asel Perera", "role": "Chairperson", "initials": "AP"}, {"name": "Kasun Silva", "role": "Vice Chair", "initials": "KS"}, {"name": "Nimal Fernando", "role": "Secretary", "initials": "NF"}, {"name": "Dilan Raj", "role": "Treasurer", "initials": "DR"}]', 
    100, 
    '#1E88E5', 
    FALSE,
    FALSE
  ),
  (
    '2', 
    'Environmental Science Society', 
    'ESOC', 
    'Academic', 
    'Fosters environmental sustainability, ecological research, and green campus initiatives.', 
    '["Green Campus Tree Planting Drive 2025", "EcoTech Innovation Forum", "Biodiversity Survey & Hike", "Plastic Recycling Awareness Week"]', 
    '["Environmental Science", "Biology", "Sustainability"]', 
    '[{"name": "Kavindi Bandara", "role": "President", "initials": "KB"}, {"name": "Sahan Perera", "role": "Vice President", "initials": "SP"}, {"name": "Nuwanthi Silva", "role": "Secretary", "initials": "NS"}, {"name": "Tharindu Jayasinghe", "role": "Treasurer", "initials": "TJ"}]', 
    100, 
    '#4CAF50', 
    FALSE,
    FALSE
  ),
  (
    '3', 
    'Mathematical Society', 
    'Math Society', 
    'Academic', 
    'Drives passion for pure/applied mathematics, data analysis, and competitive problem-solving.', 
    '["Inter-University Math Olympiad 2025", "Data Analytics Workshop", "LaTeX Academic Writing Bootcamp", "Pi Day Quiz Championship"]', 
    '["MATH", "Applied Math", "Statistics", "Logic"]', 
    '[{"name": "Ruwan Bandara", "role": "President", "initials": "RB"}, {"name": "Chamari Dias", "role": "Vice President", "initials": "CD"}, {"name": "Dilini Wickramasinghe", "role": "Secretary", "initials": "DW"}, {"name": "Mahesh Karunaratne", "role": "Treasurer", "initials": "MK"}]', 
    100, 
    '#3F51B5', 
    FALSE,
    FALSE
  ),
  (
    '4', 
    'Industrial Management Society', 
    'IMGT Society', 
    'Business', 
    'Bridges management science, operations research, supply chain, and entrepreneurship.', 
    '["Supply Chain Management Summit 2025", "Lean Six Sigma Workshop", "Young Entrepreneurs Pitch Night", "Industry 4.0 & Logistics Expo"]', 
    '["IMGT", "Management", "Business Analytics"]', 
    '[{"name": "Malith Jayasuriya", "role": "President", "initials": "MJ"}, {"name": "Hiruni Wijesinghe", "role": "Vice President", "initials": "HW"}, {"name": "Ravindu Perera", "role": "Secretary", "initials": "RP"}, {"name": "Dinushi Alwis", "role": "Treasurer", "initials": "DA"}]', 
    100, 
    '#FF9800', 
    FALSE,
    FALSE
  ),
  (
    '5', 
    'Electronics Society', 
    'Electronic Society', 
    'Technical', 
    'Hub for hardware engineering, embedded systems, IoT development, and robotics.', 
    '["Arduino & Robotics Bootcamp 2025", "IoT Smart Campus Challenge", "PCB Design Masterclass", "Hardware Hackathon 2025"]', 
    '["ELTN", "Embedded Systems", "IoT", "Hardware"]', 
    '[{"name": "Kaveen Rathnayake", "role": "President", "initials": "KR"}, {"name": "Janith Senanayake", "role": "Vice President", "initials": "JS"}, {"name": "Shenali Fonseka", "role": "Secretary", "initials": "SF"}, {"name": "Prabath Kumara", "role": "Treasurer", "initials": "PK"}]', 
    100, 
    '#E91E63', 
    FALSE,
    FALSE
  ),
  (
    '6', 
    'IEEE Student Branch Chapter', 
    'IEEE Society', 
    'Technical', 
    'Flagship global technical community driving workshops, competitions, and professional growth.', 
    '["HackElite 2025 Hackathon", "IEEE Day Celebrations 2025", "Technical Writing & Research Series", "WIE Leadership Summit 2025"]', 
    '["Engineering", "IT", "Research", "Networking"]', 
    '[{"name": "Asel Perera", "role": "Chairperson", "initials": "AP"}, {"name": "Sanduni Wickrama", "role": "Vice Chair", "initials": "SW"}, {"name": "Thilini Jayawardena", "role": "Secretary", "initials": "TJ"}, {"name": "Dilan Raj", "role": "Treasurer", "initials": "DR"}]', 
    100, 
    '#00629B', 
    FALSE,
    FALSE
  ),
  (
    '7', 
    'Gavel Club', 
    'Gavel Club', 
    'Leadership', 
    'Public speaking, communication mastery, and Toastmasters-aligned leadership development.', 
    '["SpeechCraft 2025 Workshop", "Inter-Faculty Impromptu Speech Contest", "Toastmasters Leadership Summit", "Humorous Speech Championship"]', 
    '["Public Speaking", "Leadership", "Soft Skills"]', 
    '[{"name": "Nipuni Jayawardena", "role": "President", "initials": "NJ"}, {"name": "Tharindu Fernando", "role": "VP Education", "initials": "TF"}, {"name": "Anuki Mendis", "role": "VP Public Relations", "initials": "AM"}, {"name": "Chathura Madawala", "role": "Secretary", "initials": "CM"}]', 
    100, 
    '#9C27B0', 
    FALSE,
    FALSE
  ),
  (
    '8', 
    'WireScope Photography Society', 
    'WireScope', 
    'Creative', 
    'Photography, digital media creation, event coverage, and visual storytelling.', 
    '["Focus 2025 Annual Photo Exhibition", "Portrait & Landscape Workshop", "Inter-Faculty Short Film Fest", "Digital Media & Lightroom Editing"]', 
    '["Photography", "Videography", "Media", "Editing"]', 
    '[{"name": "Pathum Herath", "role": "President", "initials": "PH"}, {"name": "Rashmi Gunawardena", "role": "Vice President", "initials": "RG"}, {"name": "Ishan Liyanage", "role": "Secretary", "initials": "IL"}, {"name": "Amanda Cooray", "role": "Treasurer", "initials": "AC"}]', 
    100, 
    '#795548', 
    FALSE,
    FALSE
  ),
  (
    '9', 
    'Wire Explorers', 
    'Wire Explorers', 
    'Adventure', 
    'Outdoor adventures, hiking, community exploration, and youth engagement.', 
    '["Ella Rock Hiking Expedition 2025", "Knuckles Wilderness Survival Camp", "River Rafting & Team Building", "Coastal Clean-up & Campfire Night"]', 
    '["Outdoor", "Adventure", "Team Building"]', 
    '[{"name": "Danushka Wickramaratne", "role": "Leader", "initials": "DW"}, {"name": "Isuru Jayasundara", "role": "Co-Leader", "initials": "IJ"}, {"name": "Keshani Abeywickrama", "role": "Secretary", "initials": "KA"}, {"name": "Lakshan Rodrigo", "role": "Treasurer", "initials": "LR"}]', 
    100, 
    '#009688', 
    FALSE,
    FALSE
  ),
  (
    '10', 
    'Chess Club', 
    'Chess Club', 
    'Sports', 
    'Strategic board gaming, university tournament training, and tactical analysis.', 
    '["Inter-Faculty Chess Championship 2025", "Grandmaster Simul Exhibition Match", "Rapid Chess Arena 2025", "Tactical Opening Masterclass"]', 
    '["Chess", "Strategy", "Tactics", "Mind Sports"]', 
    '[{"name": "Supun Gamage", "role": "Captain", "initials": "SG"}, {"name": "Madusha Peiris", "role": "Vice Captain", "initials": "MP"}, {"name": "Oshada Samarasinghe", "role": "Secretary", "initials": "OS"}, {"name": "Piyumi Senanayake", "role": "Treasurer", "initials": "PS"}]', 
    100, 
    '#607D8B', 
    FALSE,
    FALSE
  ),
  (
    '11', 
    'Badminton Club', 
    'Badminton Club', 
    'Sports', 
    'Indoor racket sports, university athletic meets, and physical endurance training.', 
    '["Annual Inter-Faculty Badminton 2025", "Mixed Doubles Smash Cup", "Varsity Fitness & Agility Clinic", "Novices Racket Championship 2025"]', 
    '["Sports", "Badminton", "Fitness", "Athletics"]', 
    '[{"name": "Sachini Liyanage", "role": "Captain", "initials": "SL"}, {"name": "Charith De Silva", "role": "Vice Captain", "initials": "CS"}, {"name": "Nimasha Perera", "role": "Secretary", "initials": "NP"}, {"name": "Harsha Abeykoon", "role": "Treasurer", "initials": "HA"}]', 
    100, 
    '#D32F2F', 
    FALSE,
    FALSE
  ),
  (
    '12', 
    'Cricket Club', 
    'Cricket Club', 
    'Sports', 
    'University varsity cricket, competitive matches, and inter-faculty tournaments.', 
    '["Wayamba Premier League (WPL) 2025", "Inter-Faculty Sixes Tournament", "Annual Varsity Encounter Match", "Leather Ball Cricket Clinic"]', 
    '["Sports", "Cricket", "Athletics", "Teamwork"]', 
    '[{"name": "Chathura Madawala", "role": "Captain", "initials": "CM"}, {"name": "Roshen Silva", "role": "Vice Captain", "initials": "RS"}, {"name": "Dasun Fernando", "role": "Secretary", "initials": "DF"}, {"name": "Bhanuka Gunatilake", "role": "Treasurer", "initials": "BG"}]', 
    100, 
    '#1976D2', 
    FALSE,
    FALSE
  )
ON CONFLICT (id) DO UPDATE 
SET name = EXCLUDED.name,
    short_name = EXCLUDED.short_name,
    category = EXCLUDED.category,
    description = EXCLUDED.description,
    past_events = EXCLUDED.past_events,
    skills = EXCLUDED.skills,
    excom = EXCLUDED.excom,
    member_count = EXCLUDED.member_count,
    color = EXCLUDED.color,
    is_wie = EXCLUDED.is_wie,
    mentor_available = EXCLUDED.mentor_available;
```