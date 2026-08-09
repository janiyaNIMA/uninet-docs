Uninet/
└──uninet-backend/
    ├── .env.example                  # Environment variable blueprint (no secrets)[cite: 2, 3]
    ├── .gitignore                    # Ignores .venv, __pycache__, .env, *.db
    ├── .python-version               # Python version managed by uv (e.g., 3.12)
    ├── pyproject.toml                # Project dependencies and build config
    ├── README.md                     # Setup instructions & API documentation
    ├── uv.lock                       # Auto-generated reproducible lockfile
    └── src/
        └── uninet/                   # Core application package
            ├── __init__.py           # Package marker
            ├── config.py             # Configuration loader (DB URL, JWT secrets, App settings)
            ├── main.py               # Flask Application Factory & Server entry point
            ├── models.py             # SQLAlchemy ORM Database Schemas[cite: 1]
            ├── recommender.py        # Scikit-learn TF-IDF & Cosine Similarity matching engine
            ├── seed.py               # Seed script to insert initial database records
            ├── utils/                # Helper utilities & PDF generators
            │   ├── __init__.py
            │   ├── pdf_generator.py  # ReportLab PDF generator for co-curricular export
            │   └── security.py       # Password hashing & JWT token helpers
            └── routes/               # API Endpoint Blueprints
                ├── __init__.py
                ├── analytics.py      # Campus & Diversity analytics endpoints (/api/v1/analytics)
                ├── auth.py           # Authentication & password change endpoints (/api/v1/auth)
                ├── excom.py          # ExCom dashboard & event posting endpoints (/api/v1/excom)[cite: 8]
                ├── feed.py           # Smart feed & event registration endpoints (/api/v1/feed)[cite: 8]
                ├── portfolio.py     # Badges & co-curricular portfolio endpoints (/api/v1/portfolio)[cite: 8]
                ├── profile.py        # Smart profile management endpoints (/api/v1/profile)[cite: 8]
                ├── recruitment.py    # Automated committee recruitment endpoints (/api/v1/recruitment)[cite: 8]
                ├── settings.py       # User account settings & notification endpoints (/api/v1/settings)[cite: 8]
                └── societies.py      # Society directory & WIE mentor endpoints (/api/v1/societies)[cite: 8]
└──uninet-frontend/
    ├── .gitignore
    ├── README.md
    ├── eslint.config.js
    ├── index.html
    ├── node_modules/
    ├── package-lock.json
    ├── package.json
    ├── public/
    ├── src/
    │   ├── App.css
    │   ├── App.jsx
    │   ├── assets/
    │   ├── components/
    │   ├── index.css
    │   ├── main.jsx
    │   ├── navigation/
    │   │   ├── AppLayout.jsx
    │   │   ├── Footer.jsx
    │   │   ├── Header.jsx
    │   │   ├── ProfilePopup.jsx
    │   │   └── Sidebar.jsx
    │   └── screens/
    │       ├── AccountSettings.jsx
    │       ├── Analytics.jsx
    │       ├── BadgePortfolio.jsx
    │       ├── ExComDashboard.jsx
    │       ├── MyProfile.jsx
    │       ├── RecruitmentPipeline.jsx
    │       ├── SmartFeed.jsx
    │       └── SocietyDiscovery.jsx
    └── vite.config.js
    ├── README.md                      # Mandatory HackElite Markdown Format
    └── MIZU.pdf                       # Step-by-step setup guide for judges