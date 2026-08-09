Here is the comprehensive component mapping for every screen using **MUI (Material UI v5/v6)** components. This maps your exact functional requirements to production-ready UI building blocks.

---

### 1. Smart Profile Screen

* **Student Header Card:** `MuiCard`, `MuiCardHeader`, `MuiAvatar`, `MuiTypography`, `MuiChip` (for status/batch indicators).
* **Editable Tags (Skills/Interests/Modules):** `MuiAutocomplete` (with `multiple` & `freeSolo` options), `MuiChip` (deletable), `MuiBox`.
* **Badge Status Summary:** `MuiPaper`, `MuiLinearProgress` (for tier progress bar), `MuiBadge`, `MuiTooltip`, `MuiTypography`.
* **Portfolio Link/Download:** `MuiButton` (with `startIcon={<DownloadIcon/>}`), `MuiCircularProgress` (for dynamic loading state).

---

### 2. Account Settings Screen

* **Personal Information Editor:** `MuiCard`, `MuiAvatar` (with badge upload icon), `MuiTextField`, `MuiIconButton` (for photo change), `MuiGrid`.
* **Theme & Appearance Controls:** `MuiToggleButtonGroup`, `MuiToggleButton`, `MuiFormLabel`, `MuiRadioGroup`, `MuiFormControlLabel`, `MuiRadio`.
* **Notification Preferences:** `MuiList`, `MuiListItem`, `MuiListItemText`, `MuiSwitch`, `MuiDivider`.
* **Account Security:** `MuiAccordion`, `MuiAccordionSummary`, `MuiAccordionDetails`, `MuiTextField` (password type), `MuiButton` (variant `contained` / `outlined` color `error` for logout).

---

### 3. Personalized Smart Feed (Home Dashboard)

* **AI Recommendation Cards:** `MuiCard`, `MuiCardMedia` (for event flyers), `MuiCardContent`, `MuiCardActions`, `MuiChip` (styled with match percentage score).
* **Search & Filters:** `MuiTextField` (with `InputProps={{ startAdornment: <SearchIcon/> }}`), `MuiSelect`, `MuiMenuItem`, `MuiFormControl`, `MuiStack`.
* **One-Click Registration Action:** `MuiButton` (variant `contained`, color `primary`), `MuiSnackbar` / `MuiAlert` (for instant registration feedback).

---

### 4. Society Discovery Directory

* **Society Profiles & Grid:** `MuiGrid`, `MuiCard`, `MuiCardHeader`, `MuiAvatarGroup` (for ExCom members), `MuiCollapse` (for expandable details).
* **Skill & Benefit Mapping:** `MuiStack`, `MuiChip` (variant `outlined` color `secondary`), `MuiList`, `MuiListItemIcon` (check marks), `MuiListItemText`.
* **WIE Mentorship Spotlight:** `MuiPaper` (with custom accent border), `MuiAvatar`, `MuiTypography`, `MuiButton` (for booking/contacting mentors), `MuiRating` / `MuiChip`.

---

### 5. Event Detail & One-Click Registration View

* **Event Schedule & Details:** `MuiContainer`, `MuiTypography`, `MuiTimeline` (from `@mui/lab`), `MuiTimelineItem`, `MuiTimelineSeparator`, `MuiTimelineContent`, `MuiBreadcrumbs`.
* **Auto-Filled Registration Form:** `MuiDialog` or `MuiPaper`, `MuiTextField` (disabled/read-only mode showing auto-pulled profile data), `MuiAlert` (info banner).
* **Confirmation & Calendar Sync:** `MuiSnackbar`, `MuiAlert`, `MuiButton` (variant `outlined` with Google Calendar icon), `MuiDialogActions`.

---

### 6. Gamified Badge & Co-Curricular Portfolio Screen

* **Digital Badge Display:** `MuiGrid`, `MuiPaper`, `MuiAvatar` (large custom badge assets), `MuiLinearProgress` (tier progress tracker), `MuiTooltip`.
* **Public Achievement Setting:** `MuiFormControlLabel`, `MuiSwitch`, `MuiTypography`.
* **Verifiable Co-Curricular Export:** `MuiTable`, `MuiTableBody`, `MuiTableCell`, `MuiTableContainer`, `MuiTableHead`, `MuiTableRow`, `MuiButton` (variant `contained` with PDF icon).

---

### 7. Society Committee / ExCom Dashboard

* **Event Post Creator:** `MuiStepper`, `MuiStep`, `MuiStepLabel`, `MuiTextField`, `MuiAutocomplete` (for target module tags), `MuiButton` (file upload picker).
* **Active Recruitment Drive Managers:** `MuiDataGrid` (from `@mui/x-data-grid`) or `MuiTable`, `MuiChip` (for status: Active/Closed), `MuiIconButton` (edit/delete actions).
* **Boost Promotions Controls:** `MuiButton` (color `warning` or `secondary`), `MuiDialog` (confirmation prompt), `MuiSlider` (target reach selector).

---

### 8. Automated Committee Recruitment Pipeline

* **Applicant List & AI Candidates:** `MuiDataGrid` (with custom cell rendering for match scores), `MuiAvatar`, `MuiRating`, `MuiTabs`, `MuiTab`.
* **Candidate Review Cards:** `MuiCard`, `MuiCardContent`, `MuiChip` (displaying student badge levels), `MuiTypography`, `MuiDivider`.
* **One-Click Dispatch System:** `MuiButton` (variant `contained` color `success`), `MuiLoadingButton` (from `@mui/lab`), `MuiSnackbar` (dispatch confirmation).

---

### 9. Participation & Diversity Analytics Screen

* **Registration & Attendance Analytics:** `MuiCard`, `MuiCardContent`, Chart integration wrapped in `MuiBox` (e.g., using Recharts or MUI X Charts `@mui/x-charts`), `MuiSelect` (for date range selection).
* **Demographic Tracking Metrics:** `MuiGrid`, `MuiPaper`, Circular progress / Donut chart wrappers, `MuiTypography`, `MuiTooltip`.
* **Campus Participation Trends:** `MuiStack`, Line/Bar chart containers, `MuiToggleButtonGroup` (weekly/monthly/yearly view toggle).