Here is the extended MUI component mapping incorporating the **Global Layout Wrapper Components** (Header, Footer, Expandable Sidebar, and Profile Popup).

---

### 🌐 Global Layout & Shell Components

#### 1. Responsive Header (Navbar)

* **Main Bar Container:** `MuiAppBar` (position `sticky` or `fixed`), `MuiToolbar`.
* **Sidebar Toggle:** `MuiIconButton` with `<MenuIcon/>` / `<MenuOpenIcon/>` to expand or collapse the drawer.
* **App Branding/Logo:** `MuiTypography` (variant `h6`), `MuiBox` (for logo image asset).
* **Search / Quick Action Bar:** `MuiInputBase` or `MuiOutlinedInput` wrapped in `MuiBox` with background transparency.
* **Header Actions & Notifications:** `MuiIconButton` with `<NotificationsIcon/>`, `MuiBadge` (showing unread counts), `MuiTooltip`.
* **Profile Trigger Avatar:** `MuiAvatar` wrapped in `MuiIconButton` (opens the Profile Info Popup).

#### 2. Expandable / Collapsible Sidebar (Navigation Drawer)

* **Drawer Container:** `MuiDrawer` (variant `responsive` / `persistent` / `temporary` for mobile).
* **Expand/Collapse Action:** `MuiIconButton` with `<ChevronLeftIcon/>` / `<ChevronRightIcon/>` at the top header of the drawer.
* **Navigation Items:** `MuiList`, `MuiListItem`, `MuiListItemButton`, `MuiListItemIcon` (e.g., `<HomeIcon/>`, `<ExploreIcon/>`, `<EmojiEventsIcon/>`, `<AnalyticsIcon/>`), `MuiListItemText`.
* **Active State Styling:** `MuiListItemButton` with `selected` state and custom background highlights.
* **Section Dividers & Headers:** `MuiDivider`, `MuiListSubheader` (e.g., "Student View", "ExCom Management").

#### 3. Profile Info Quick Popup (User Menu)

* **Menu Container:** `MuiPopover` or `MuiMenu` (anchored to the header Avatar icon).
* **Profile Header:** `MuiMenuItem` or `MuiBox` containing:
* Large `MuiAvatar`
* `MuiTypography` (User's full name & university email)
* `MuiChip` (Badge tier e.g., "Gold Member" or Role e.g., "WIE ExCom Chair")


* **Quick Navigation Links:** `MuiList`, `MuiListItemButton`, `MuiListItemIcon`:
* "My Profile" (`<AccountCircleIcon/>`) -> Navigates to **My Profile Screen**
* "Account Settings" (`<SettingsIcon/>`) -> Navigates to **Account Settings Screen**
* "My Portfolio" (`<DescriptionIcon/>`) -> Downloads or navigates to **Co-Curricular Resume**


* **Logout Button:** `MuiDivider`, `MuiMenuItem` with `<LogoutIcon/>` (styled with `color="error"`).

#### 4. Global Site Footer

* **Footer Container:** `MuiBox` (styled with `component="footer"`), `MuiContainer`.
* **Navigation & Links:** `MuiGrid`, `MuiLink` (for Terms, Privacy Policy, IEEE WIE Contact Links, HackElite Info).
* **Branding & Social Links:** `MuiStack` with `MuiIconButton` (Facebook, LinkedIn, GitHub icons).
* **Copyright & Version Info:** `MuiTypography` (variant `body2`, `color="text.secondary"`).

---

### Updated Full Architecture Layout Blueprint

```text
 +-------------------------------------------------------------------------------------+
 |  MuiAppBar (Header)                                                                 |
 |  [MenuToggle]  [Logo/Uninet]                          [Notifications]   [MuiAvatar] |
 +-------------------------------------------------------------------------|-----------+
 |                                                                         |  (Opens)  |
 |  MuiDrawer (Sidebar)   |  Main Screen Content Container                 v           |
 |  (Expand/Collapse)     |  (Smart Feed / Settings / Discovery / etc.)   +----------+ |
 |                        |                                               | Popover  | |
 |  * Smart Feed          |                                               | User Info| |
 |  * Discovery           |                                               | Profile  | |
 |  * My Profile          |                                               | Settings | |
 |  * Badges              |                                               | Logout   | |
 |  * ExCom Dashboard     |                                               +----------+ |
 |                        |                                                            |
 +------------------------+------------------------------------------------------------+
 |  MuiBox (Footer)                                                                    |
 |  Links | Copyright © MIZU | IEEE SBC Wayamba University of Sri Lanka                |
 +-------------------------------------------------------------------------------------+

```