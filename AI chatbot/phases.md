# Student Academic Companion Chatbot - Phase-wise Development Roadmap

This document maps out the implementation of the **Student Academic Companion Chatbot** in four progressive phases. Each phase builds upon the previous, transitioning from base configurations to core logic, advanced features, and final optimizations.

---

## Phase 1 – Foundation

### Objectives
Establish the workspace structure, initialize the Flask environment, define the SQLite schema, and set up a modern, responsive HTML/CSS shell with initial routing.

### Features
* Basic project layout configuration.
* SQLite database file initialization.
* Responsive, styled chatbot shell (without dynamic messaging logic).
* Landing page web routing.

### Deliverables
* Fully initialized workspace directories.
* Initial database file (`db.sqlite3`) and schema initialization script (`schema.sql`).
* Flask environment configuration (`config.py` and `app.py` entrypoint).
* Landing page template (`templates/index.html`) and premium dark-mode stylesheet (`static/css/style.css`).
* `requirements.txt` containing dependencies.

### Files/Modules Affected
* `requirements.txt`
* `config.py`
* `app.py`
* `schema.sql`
* `database.py`
* `templates/index.html`
* `static/css/style.css`

### Dependencies
* Python 3.x
* Flask (>= 3.0.0)

### Completion Criteria
1. Flask app launches locally without warnings or errors.
2. Navigating to `http://localhost:5000` loads a styled browser window showing the chatbot card shell.
3. Database file `db.sqlite3` exists and all defined tables are initialized successfully with no rows.

---

## Phase 2 – Core Chatbot

### Objectives
Implement the conversational questionnaire flow to collect student study requirements, process inputs, generate the personalized study schedule, and persist data in SQLite.

### Features
* Chat session instantiation and tracking.
* Dynamic message exchange with step-by-step state preservation (Exam Date, Syllabus Topics, Daily Hours, Prep Level, Timing).
* Core study plan generation algorithm.
* Timetable data serialization and database writing.
* Real-time dashboard view generation.

### Deliverables
* Completed questionnaire handlers in `app.py` using `session_id` to control step-wise routing.
* Core plan generation engine (`scheduler.py`) calculating daily/weekly timelines.
* JavaScript chat router (`static/js/chat.js`) supporting active inputs, selection buttons, and DOM message appending.
* Functional Dashboard showing the generated Study Plan data.

### Files/Modules Affected
* `app.py` (Add `/api/session`, `/api/chat`, `/api/generate-plan` endpoints)
* `database.py` (Add CRUD helpers for preferences, topics, and plans)
* `scheduler.py` (New module)
* `static/js/chat.js` (New module)
* `templates/index.html` (Integrate script calls and bind elements)

### Dependencies
* Phase 1 codebase.
* standard libraries (`uuid`, `datetime`, `math`, `json`).

### Completion Criteria
1. Student can start a chat session and input values step-by-step through the visual chat interface.
2. The backend correctly computes and stores subject parameters and schedule outputs in SQLite.
3. The frontend receives the calculated plan and populates the Dashboard panel dynamically with a daily checklist and weekly summary.

---

## Phase 3 – Additional Features

### Objectives
Equip the chatbot with resource linking, notes logging, and motivational support while refining the user experience (animations, error states, and strict validations).

### Features
* Study Notes manager: Create, view, and delete text notes keyed to study sessions or specific topics.
* Resource Links tracker: Save relevant web addresses and resources next to corresponding topics.
* Motivational study tip generator: Pulls relevant student encouraging quotes from seeded tips tables.
* Premium UI animations (typing bubble animation, glassmorphism hovers, and clean responsive card shifts).
* Server-side and client-side data validation.

### Deliverables
* Database seed scripts for pre-populating motivational tips.
* API endpoints and handlers for Notes operations.
* Premium transition classes and layouts in `style.css` and `chat.js`.
* Input validation layers checking for future dates, realistic hours, and distinct topic parameters.

### Files/Modules Affected
* `app.py` (Add `/api/notes` routes and `/api/tips` endpoints)
* `database.py` (Add queries for Notes and seeded Tips tables)
* `static/css/style.css` (Animations, transitions, and note card components)
* `static/js/chat.js` (Integrate notes editing panels and fetch tips)
* `schema.sql` (Check schema constraints)

### Dependencies
* Phase 2 codebase.

### Completion Criteria
1. User can click a "Get Study Tip" button or ask for tips and receive a random motivational quote.
2. User can add, view, and delete study notes and resource URLs through the sidebar manager interface.
3. Form submissions block invalid inputs (e.g., negative study hours or past dates) and show helpful warning states.

---

## Phase 4 – Finalization

### Objectives
Perform full integration verifications, run edge-case tests, clean up source code comments, and package the application for deployment.

### Features
* Integration testing coverage.
* Codebase optimization (connection leaks check, CSS refactoring, query optimizations).
* User-facing documentation and final user guide.
* Deployment configurations.

### Deliverables
* Complete documentation walkthrough (`walkthrough.md`) detailing setup and operations.
* Cleaned up, commented, PEP8-compliant codebase.
* Lightweight integration test script validating endpoints.
* Final deployment-ready package.

### Files/Modules Affected
* Entire project workspace (Code linting and refactoring).
* `requirements.txt` (Freeze versions).
* `README.md` (Add setup and running instructions).

### Dependencies
* Phase 3 codebase.

### Completion Criteria
1. All application routes return correct responses under simulated load/stress tests.
2. Database connection pools close properly without memory leaks.
3. Code contains zero debug logs or orphan files, ready for production.
