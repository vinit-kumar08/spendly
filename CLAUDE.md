# Spendly (Expense Tracker) - Developer Guide

Spendly is a multi-step, web-based expense tracker application built using Python Flask, HTML5, CSS3, JavaScript, and SQLite.

## Folder Structure

```
expense-tracker/
├── .venv/                      # Python virtual environment (git-ignored)
├── expense-tracker/            # Main application source directory
│   ├── database/               # Database modules
│   │   ├── __init__.py
│   │   └── db.py               # SQLite database setup and helper functions
│   ├── static/                 # Static assets
│   │   ├── css/
│   │   │   └── style.css       # Core stylesheets
│   │   └── js/
│   │       └── main.js         # Frontend JavaScript behavior
│   ├── templates/              # Jinja2 HTML templates
│   │   ├── base.html           # Main base template
│   │   ├── landing.html        # Landing page
│   │   ├── login.html          # Sign-in page
│   │   ├── privacy.html        # Privacy Policy page
│   │   ├── register.html       # Sign-up page
│   │   └── terms.html          # Terms & Conditions page
│   ├── .gitignore              # Git ignored patterns for the subfolder
│   ├── app.py                  # Main Flask application entry point
│   └── requirements.txt        # Python package dependencies
```

## Development Commands

### 1. Setup Virtual Environment
Run these commands from the root directory:
```powershell
# Create virtual environment
python -m venv .venv

# Activate virtual environment
# Windows (PowerShell):
.venv\Scripts\Activate.ps1
# Windows (CMD):
.venv\Scripts\activate.bat
# macOS/Linux:
source .venv/bin/activate
```

### 2. Install Dependencies
```bash
pip install -r expense-tracker/requirements.txt
```

### 3. Run the Application
Start the Flask development server (runs by default on `http://127.0.0.1:5001` with debug mode enabled):
```bash
python expense-tracker/app.py
```

### 4. Running Tests
Run pytest to verify implementation correctness:
```bash
pytest
```

## Coding Standards

### Python & Flask
- Follow **PEP 8** style guidelines for clean, readable Python code.
- Always use **parameterized queries** in SQL executions to prevent SQL injection.
- Keep route handlers in [app.py](file:///d:/Desktop%20D/New%20folder/expense-tracker/expense-tracker/app.py) small; delegate database operations or complex business logic to dedicated helper files.
- Return appropriate HTTP status codes (e.g., 200 OK, 400 Bad Request, 404 Not Found, etc.).

### Database (SQLite)
- Implement SQLite interaction in [db.py](file:///d:/Desktop%20D/New%20folder/expense-tracker/expense-tracker/database/db.py).
- Ensure foreign key constraints are enabled: `conn.execute("PRAGMA foreign_keys = ON;")`.
- Enable dict-like behavior for results: `conn.row_factory = sqlite3.Row`.
- Use a Context Manager (e.g., `with`) for database connections and transaction management.

### HTML, CSS & JavaScript
- Write clean, semantic HTML5 structure.
- Always extend the base layout [base.html](file:///d:/Desktop%20D/New%20folder/expense-tracker/expense-tracker/templates/base.html) for pages to maintain visual consistency.
- Use CSS variables for layout spacing and theme colors in [style.css](file:///d:/Desktop%20D/New%20folder/expense-tracker/expense-tracker/static/css/style.css).
- Write modular, vanilla JavaScript in [main.js](file:///d:/Desktop%20D/New%20folder/expense-tracker/expense-tracker/static/js/main.js). Avoid raw inline JS in templates.

## Testing Instructions
- Put all test modules in a `tests/` directory (e.g. `tests/test_routes.py`).
- Run tests using `pytest` or `python -m pytest`.
- Name test files with prefix `test_` and test functions with prefix `test_`.

## Git Conventions
- **Commit Messages**: Write clear, descriptive, and imperative-style commit messages (e.g. `feat: implement user registration`).
- **Branching**: For step-by-step development, use feature branches prefixing the step name: `step-<number>-<feature-description>` (e.g. `step-1-db-setup`).
