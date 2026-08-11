# Uninet Frontend API Integration Specification

This document provides a comprehensive blueprint for backend developers constructing RESTful APIs for the **Uninet** frontend application. It outlines the data contracts, expected HTTP methods, URL routes, request payloads, and response structures for every screen component.

---

## Table of Contents
1. [Architecture & Global Headers](#1-architecture--global-headers)
2. [Smart Feed Screen (`/`)](#2-smart-feed-screen-)
3. [Society Discovery Directory (`/societies`)](#3-society-discovery-directory-societies)
4. [Badge & Co-Curricular Portfolio Screen (`/badges`)](#4-badge--co-curricular-portfolio-screen-badges)
5. [My Profile Screen (`/profile`)](#5-my-profile-screen-profile)
6. [Account Settings Screen (`/settings`)](#6-account-settings-screen-settings)
7. [ExCom & Society Dashboard (`/excom`)](#7-excom--society-dashboard-excom)
8. [Automated Recruitment Pipeline (`/recruitment`)](#8-automated-recruitment-pipeline-recruitment)
9. [Participation & Diversity Analytics (`/analytics`)](#9-participation--diversity-analytics-analytics)

---

## 1. Architecture & Global Headers

All API requests should originate from the React frontend using standard REST standards with JSON payloads.

### Standard Request Headers
```http
Authorization: Bearer <JWT_TOKEN>
Content-Type: application/json
Accept: application/json
```

### Standard Error Response Format
```json
{
  "success": false,
  "error": {
    "code": "UNAUTHORIZED | NOT_FOUND | VALIDATION_ERROR | SERVER_ERROR",
    "message": "Human-readable message explaining the failure."
  }
}
```

---

## 2. Smart Feed Screen (`/`)

*Component Source:* [`SmartFeed.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/SmartFeed.jsx)

### 2.1 Fetch AI Recommended Feed
Returns event cards ordered by AI match percentage based on student TF-IDF recommendation profile.

* **Endpoint:** `GET /api/v1/feed`
* **Query Parameters:**
  * `search` (optional string): Keyword filter for title or society name.
  * `category` (optional string): Category name (`workshop`, `hackathon`, `seminar`, `sports`).
  * `module` (optional string): Academic module tag (`Computer Science`, `Engineering`, `IT`, `Business`).

#### Response `200 OK`
```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "title": "IEEE Cloud Computing Workshop",
      "society": "IEEE CS Chapter",
      "category": "workshop",
      "module": "Computer Science",
      "date": "2026-08-20",
      "matchScore": 95,
      "image": "https://domain.com/flyers/cloud.jpg",
      "tags": ["Cloud", "AWS", "DevOps"],
      "isRegistered": false
    }
  ]
}
```

### 2.2 One-Click Event Registration
Registers the currently authenticated student for an event.

* **Endpoint:** `POST /api/v1/events/:eventId/register`
* **Request Payload:** `{}` *(User ID extracted from Auth JWT)*

#### Response `200 OK`
```json
{
  "success": true,
  "message": "Successfully registered for event.",
  "data": {
    "eventId": 1,
    "registrationId": "REG-94821",
    "calendarSyncUrl": "https://calendar.google.com/calendar/render?action=TEMPLATE&..."
  }
}
```

---

## 3. Society Discovery Directory (`/societies`)

*Component Source:* [`SocietyDiscovery.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/SocietyDiscovery.jsx)

### 3.1 Fetch Society Directory & WIE Mentors
Retrieves all active campus organizations, committee rosters, skills gained, and WIE mentor spotlights.

* **Endpoint:** `GET /api/v1/societies`
* **Query Parameters:**
  * `search` (optional string): Matches society name, description, or skills.
  * `category` (optional string): Filter (`Technical`, `Inclusivity`, `Business`, `Sports`).

#### Response `200 OK`
```json
{
  "success": true,
  "data": {
    "wieMentors": [
      {
        "id": "M1",
        "name": "Dr. Chamila Rathnayake",
        "role": "Faculty Mentor · Senior Lecturer",
        "initials": "CR",
        "tags": ["AI", "Research"],
        "contactEmail": "chamila@wusl.ac.lk"
      }
    ],
    "societies": [
      {
        "id": 1,
        "name": "IEEE Student Branch Chapter",
        "shortName": "IEEE SBC",
        "category": "Technical",
        "description": "The flagship IEEE student branch driving engineering excellence through workshops.",
        "pastEvents": ["HackElite 2025", "PCB Design Workshop"],
        "skills": ["Leadership", "Project Management", "Networking"],
        "excom": [
          { "name": "Asel Perera", "role": "Chairperson", "initials": "AP" }
        ],
        "memberCount": 120,
        "color": "#1565C0",
        "isWIE": false,
        "hasApplied": false
      }
    ]
  }
}
```

### 3.2 Apply to Join Society
Submits a student membership application.

* **Endpoint:** `POST /api/v1/societies/:societyId/apply`

#### Response `200 OK`
```json
{
  "success": true,
  "message": "Application sent to IEEE Student Branch Chapter!"
}
```

---

## 4. Badge & Co-Curricular Portfolio Screen (`/badges`)

*Component Source:* [`BadgePortfolio.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/BadgePortfolio.jsx)

### 4.1 Fetch Student Badges & Co-Curricular History
Returns earned points, current badge tier, unlocked digital badges, and verified activities.

* **Endpoint:** `GET /api/v1/portfolio/my-badges`

#### Response `200 OK`
```json
{
  "success": true,
  "data": {
    "currentPoints": 530,
    "badgeTier": "Gold",
    "nextTier": {
      "name": "Platinum",
      "pointsRequired": 1000
    },
    "publicProfileEnabled": true,
    "badges": [
      {
        "id": 1,
        "title": "Hackathon Hero",
        "category": "Innovation",
        "tier": "Gold",
        "unlocked": true,
        "points": 150,
        "earnedDate": "2026-05-12",
        "icon": "🏆",
        "description": "Participated and placed in top 3 in HackElite 2025."
      }
    ],
    "resumeActivities": [
      {
        "id": 1,
        "role": "Lead Organiser & Student Lead",
        "organization": "IEEE Student Branch Chapter",
        "event": "HackElite 2025 Hackathon",
        "category": "Leadership & Management",
        "period": "Mar 2025 – May 2025",
        "verified": true
      }
    ]
  }
}
```

### 4.2 Toggle Public Community Profile Visibility
* **Endpoint:** `PATCH /api/v1/portfolio/public-toggle`
* **Request Payload:**
```json
{
  "publicProfile": true
}
```

### 4.3 Export Co-Curricular PDF Portfolio
* **Endpoint:** `GET /api/v1/portfolio/export-pdf`
* **Response:** Binary PDF stream (`Content-Type: application/pdf`).

---

## 5. My Profile Screen (`/profile`)

*Component Source:* [`MyProfile.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/MyProfile.jsx)

### 5.1 Fetch Student Smart Profile
* **Endpoint:** `GET /api/v1/profile`

#### Response `200 OK`
```json
{
  "success": true,
  "data": {
    "name": "Jane Doe",
    "email": "jane@wusl.ac.lk",
    "university": "Wayamba University of Sri Lanka",
    "faculty": "Faculty of Applied Sciences",
    "degreeStream": "BSc (Hons) in Computer Science",
    "batch": "Batch of 2022/23",
    "badgeTier": "Gold",
    "totalPoints": 530,
    "nextTierPoints": 600,
    "skills": ["Full-Stack Development", "Cloud Computing", "AI & Machine Learning"],
    "interests": ["Hackathons", "Open Source", "WIE Leadership"],
    "academicModules": ["CS3102 - Web Engineering", "CS3204 - Artificial Intelligence"]
  }
}
```

### 5.2 Update Profile Tags (Feeds Recommender Engine)
* **Endpoint:** `PUT /api/v1/profile/tags`
* **Request Payload:**
```json
{
  "skills": ["Full-Stack Development", "DevOps"],
  "interests": ["Hackathons", "Robotics"],
  "academicModules": ["CS3102 - Web Engineering"]
}
```

---

## 6. Account Settings Screen (`/settings`)

*Component Source:* [`AccountSettings.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/AccountSettings.jsx)

### 6.1 Update Personal Contact Information
* **Endpoint:** `PUT /api/v1/settings/personal-info`
* **Request Payload:**
```json
{
  "fullName": "Jane Doe",
  "email": "jane@wusl.ac.lk",
  "phone": "+94 77 123 4567"
}
```

### 6.2 Update Notification Preferences
* **Endpoint:** `PUT /api/v1/settings/notifications`
* **Request Payload:**
```json
{
  "inAppAlerts": true,
  "emailUpdates": true,
  "recruitmentNotifs": false,
  "societyBroadcasts": true
}
```

### 6.3 Change Password
* **Endpoint:** `POST /api/v1/auth/change-password`
* **Request Payload:**
```json
{
  "currentPassword": "OldPassword123!",
  "newPassword": "NewPassword456!"
}
```

---

## 7. ExCom & Society Dashboard (`/excom`)

*Component Source:* [`ExComDashboard.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/ExComDashboard.jsx)

### 7.1 Publish New Event Post
* **Endpoint:** `POST /api/v1/excom/events`
* **Request Payload:**
```json
{
  "title": "IEEE Full-Stack Web Development Sprint",
  "description": "Hands-on coding workshop...",
  "targetModules": ["CS3102 - Web Engineering"],
  "requiredSkills": ["React", "Node.js"],
  "flyerUrl": "https://domain.com/uploads/flyer1.png"
}
```

### 7.2 Fetch Recruitment Drives & Boost Status
* **Endpoint:** `GET /api/v1/excom/recruitment-drives`

### 7.3 Boost Event / Recruitment Drive Promotion
Pushes the post to the top of targeted student feeds.

* **Endpoint:** `POST /api/v1/excom/drives/:driveId/boost`
* **Request Payload:**
```json
{
  "targetReach": 500
}
```

---

## 8. Automated Recruitment Pipeline (`/recruitment`)

*Component Source:* [`RecruitmentPipeline.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/RecruitmentPipeline.jsx)

### 8.1 Fetch Applicants & AI-Matched Candidate Suggestions
* **Endpoint:** `GET /api/v1/recruitment/candidates`

#### Response `200 OK`
```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "Kavindi Bandara",
      "email": "kavindi@wusl.ac.lk",
      "initials": "KB",
      "badgeLevel": "Gold",
      "points": 620,
      "matchScore": 96,
      "appliedFor": "HackElite 2026 OC Lead",
      "type": "applicant",
      "academicBackground": "BSc Hons Computer Science (3rd Year)",
      "skills": ["Full-Stack Dev", "Event Management"],
      "pastContributions": "Sub-committee Lead for PCB Workshop 2025.",
      "rating": 5,
      "status": "Pending"
    }
  ]
}
```

### 8.2 Update Candidate Pipeline Status (Review, Recruit, Ignore)
Updates the pipeline stage status of a candidate application.

* **Endpoint:** `PUT /api/v1/recruitment/candidates/:candidateId/status` (or `POST /api/v1/recruitment/candidates/:candidateId/review`, `/recruit`, `/ignore`)
* **Request Body:**
```json
{
  "status": "Under Review" // Options: "Pending", "Under Review", "Recruited", "Ignored"
}
```

#### Response `200 OK`
```json
{
  "success": true,
  "message": "Candidate status updated to Under Review.",
  "data": {
    "id": 1,
    "name": "Kavindi Bandara",
    "status": "Under Review"
  }
}
```

### 8.3 One-Click Recruitment Invitation & Direct Recruit
Recruits candidate or dispatches recruitment invitation.

* **Endpoint:** `POST /api/v1/recruitment/candidates/:candidateId/recruit` (or `POST /api/v1/recruitment/candidates/:candidateId/dispatch-invite`)

#### Response `200 OK`
```json
{
  "success": true,
  "message": "Candidate Kavindi Bandara has been successfully Recruited!",
  "data": {
    "id": 1,
    "name": "Kavindi Bandara",
    "status": "Recruited"
  }
}
```

### 8.4 Ignore Candidate Application
Marks candidate application as ignored/passed.

* **Endpoint:** `POST /api/v1/recruitment/candidates/:candidateId/ignore`

#### Response `200 OK`
```json
{
  "success": true,
  "message": "Candidate Kavindi Bandara has been Ignored."
}
```

### 8.5 Submit New Student Candidate Application
Submits a student application for recruitment drives or committee positions.

* **Endpoint:** `POST /api/v1/recruitment/candidates`
* **Request Body:**
```json
{
  "name": "Sahan Perera",
  "email": "sahan@wusl.ac.lk",
  "appliedFor": "Logistics OC Lead",
  "academicBackground": "BSc Industrial Management (2nd Year)",
  "skills": ["Logistics", "Budgeting", "Vendor Relations"],
  "pastContributions": "Coordinator for Sports Meet 2025."
}
```

#### Response `201 Created`
```json
{
  "success": true,
  "message": "Candidate application submitted successfully",
  "data": {
    "id": 6,
    "name": "Sahan Perera",
    "status": "Pending"
  }
}
```

---

## 9. Participation & Diversity Analytics (`/analytics`)

*Component Source:* [`Analytics.jsx`](file:///home/janidu/workbench/Hackelite/uninet-frontend/src/screens/Analytics.jsx)

### 9.1 Fetch Campus Analytics Metrics
* **Endpoint:** `GET /api/v1/analytics/dashboard`
* **Query Parameters:**
  * `range` (optional string: `7d`, `30d`, `90d`, `1y`).
  * `trendView` (optional string: `weekly`, `monthly`, `yearly`).

#### Response `200 OK`
```json
{
  "success": true,
  "data": {
    "summaryMetrics": {
      "totalActiveStudents": 1480,
      "avgTurnoutPercent": 89.4,
      "wieFemaleParticipationPercent": 42.0,
      "totalEngagementPoints": 48250
    },
    "registrationVsAttendance": [
      { "event": "Cloud Workshop", "registrations": 120, "attendance": 105 }
    ],
    "diversityMetrics": [
      { "name": "Female Undergraduates", "value": 42.0 },
      { "name": "Male Undergraduates", "value": 54.0 }
    ],
    "participationTrends": [
      { "time": "May", "engagements": 1200 },
      { "time": "Jun", "engagements": 1850 }
    ]
  }
}
```
