# Project ROI Analytics Platform

A **ROI Analytics Web Application** designed to help organizations track, calculate, analyze, and visualize the financial performance of business projects from a centralized platform.

The application combines **project management, ROI calculations, savings analysis, data visualization, Excel automation, authentication, and database integration** into a single workflow.

---

## Overview

Managing project investments and their financial outcomes often requires data from multiple sources. This platform provides a centralized solution for tracking important project metrics such as:

* Project Investment
* Planned Savings
* Realized Savings
* Net Value
* ROI Percentage
* Manhours Saved
* Project Status
* Business Unit
* Project Category
* Priority
* Target Dates

The platform provides both **project-level management** and **high-level analytics** to help users understand project performance and financial impact.

---

## Key Features

### 1. Analytics Dashboard

The dashboard provides an interactive overview of project and financial performance.

**Features include:**

* Interactive savings and trend visualizations
* Monthly/quarterly savings analysis
* Project status distribution
* Business Unit and category analysis
* Investment vs. savings comparison
* Value Matrix for impact and effort analysis
* ROI and net value calculations
* KPI summary cards
* Animated counters and visual feedback

---

### 2. Project Management

Users can manage projects directly from the application.

**Project management functionality:**

* Add new projects
* Edit existing projects
* Search projects
* Filter by:

  * Status
  * Category
  * Business Unit
* Sort project records
* Track project priority
* Track target dates
* Monitor planned and realized savings
* Calculate ROI dynamically

---

### 3. ROI & Financial Calculations

The platform automatically calculates important financial metrics.

Example metrics:

```text
Net Value = Realized Savings - Project Investment

ROI (%) = ((Realized Savings - Project Investment) / Project Investment) × 100
```

These calculations allow users to understand the financial contribution of individual projects.

---

### 4. Bulk Excel / CSV Import

The application supports importing large amounts of project data without manually entering every record.

**Supported formats:**

* `.xlsx`
* `.csv`

**Import workflow:**

```text
Upload File
     ↓
Read Excel / CSV
     ↓
Detect Columns
     ↓
Map Columns
     ↓
Validate Data
     ↓
Batch Insert
     ↓
Database
```

This is useful when existing project information is maintained in spreadsheets.

---

### 5. Excel Export

Users can export project data and customized reports into Excel format.

This allows project and financial data to be easily shared, analyzed, or used for reporting outside the application.

---

### 6. Bulk Editing

Multiple projects can be selected and updated simultaneously.

Users can perform bulk updates for fields such as:

* Project Status
* Priority
* Business Unit

This reduces repetitive manual operations when managing large project datasets.

---

### 7. Authentication & Role-Based Access

The application includes an authentication system with role-based authorization.

### Supported Roles

| Role    | Access                              |
| ------- | ----------------------------------- |
| Admin   | Full system access                  |
| Manager | Project and management-level access |
| Viewer  | View-only access                    |

The authentication layer helps control which actions different users can perform within the application.

---

## User Interface

The application includes a modern responsive interface with:

* Dark Mode
* Light Mode
* Responsive layouts
* Smooth transitions
* Micro-animations
* Interactive charts
* Animated KPI counters
* Target-achievement feedback

---

## Technology Stack

### Frontend

* **React 18**
* **Vite**
* **Tailwind CSS**
* **PostCSS**
* **Lucide React**
* **XLSX**
* **Canvas Confetti**

### Backend

* **Node.js**
* **Express.js**
* **RESTful APIs**

### Database

* **SQLite**
* **MySQL**

The application supports SQLite for simple local execution while maintaining MySQL compatibility for enterprise-oriented deployments.

---

## Architecture

```text
                    ┌──────────────────────┐
                    │      User / Client   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    React Frontend    │
                    │      + Vite          │
                    └──────────┬───────────┘
                               │
                         REST API
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Express Backend    │
                    │      Node.js         │
                    └──────────┬───────────┘
                               │
                    ┌──────────┴──────────┐
                    │                     │
                    ▼                     ▼
             ┌──────────────┐      ┌──────────────┐
             │    SQLite    │      │    MySQL     │
             │ Local DB     │      │ Enterprise DB│
             └──────────────┘      └──────────────┘
```

---

## API Structure

The backend exposes RESTful API endpoints for project management, analytics, and health monitoring.

### Projects

```text
GET    /api/projects
POST   /api/projects
PUT    /api/projects/:id
DELETE /api/projects/:id
```

### Analytics

```text
GET /api/analytics
```

### Health Check

```text
GET /health
```

> API endpoints may vary depending on the deployed version of the application.

---

## Project Structure

A simplified project structure:

```text
project-roi-analytics/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── DashboardView.jsx
│   │   │   ├── ProjectList.jsx
│   │   │   ├── ProjectForm.jsx
│   │   │   ├── BulkImportModal.jsx
│   │   │   ├── ExportModal.jsx
│   │   │   ├── BulkEditModal.jsx
│   │   │   └── AnimatedCounter.jsx
│   │   │
│   │   ├── context/
│   │   │   └── AuthContext.jsx
│   │   │
│   │   └── ...
│   │
│   ├── package.json
│   └── vite.config.js
│
├── backend/
│   ├── routes/
│   ├── controllers/
│   ├── database/
│   ├── middleware/
│   ├── server.js
│   └── package.json
│
├── roi_database.sqlite
│
├── package.json
└── README.md
```

---

## Installation

### Prerequisites

Make sure the following are installed:

* Node.js
* npm
* Git

For MySQL deployment:

* MySQL Server
* MySQL Client

---

## Clone Repository

```bash
git clone https://github.com/your-username/project-roi-analytics.git

cd project-roi-analytics
```

---

## Install Dependencies

### Backend

```bash
cd backend
npm install
```

### Frontend

```bash
cd ../frontend
npm install
```

---

## Environment Variables

Create a `.env` file in the backend directory.

Example:

```env
PORT=5000

DB_TYPE=sqlite

SQLITE_DATABASE=./roi_database.sqlite

# MySQL configuration
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_DATABASE=roi_database
MYSQL_USER=root
MYSQL_PASSWORD=your_password
```

Do not commit sensitive credentials to GitHub.

---

## Running the Application

### Start Backend

```bash
cd backend
npm start
```

Backend will run on:

```text
http://localhost:5000
```

### Start Frontend

Open another terminal:

```bash
cd frontend
npm run dev
```

Frontend will typically run on:

```text
http://localhost:5173
```

---

## Application Workflow

The general workflow is:

```text
Login
  ↓
Dashboard
  ↓
View Project Analytics
  ↓
Add / Edit Projects
  ↓
Import or Export Data
  ↓
Calculate ROI & Savings
  ↓
Analyze Project Performance
```

---

## Data Import Workflow

For bulk project creation:

```text
Excel / CSV File
       ↓
Upload
       ↓
Column Mapping
       ↓
Data Validation
       ↓
Batch Processing
       ↓
Database
       ↓
Dashboard
```

---

## Database Support

### SQLite

SQLite is useful for:

* Local development
* Standalone execution
* Testing
* Lightweight deployments

Database file:

```text
roi_database.sqlite
```

### MySQL

MySQL can be used for:

* Multi-user environments
* Centralized databases
* Enterprise deployments
* Larger production workloads

---

## Security Considerations

The application includes role-based access control to differentiate user permissions.

For production deployment, additional security practices should be implemented, including:

* Secure password hashing
* HTTPS
* Environment-based secrets
* JWT/session security
* Input validation
* API rate limiting
* Database access restrictions
* Proper CORS configuration

---

## Use Cases

This platform can be used for organizations that need to track:

* Digital transformation projects
* Cost-saving initiatives
* Automation projects
* Operational improvement projects
* IT investments
* Business process improvement
* Financial benefits realization
* Project portfolio performance

---

## Future Enhancements

Potential improvements include:

* Advanced financial forecasting
* Power BI integration
* Automated scheduled reports
* Email notifications
* Advanced user administration
* Audit logs
* Project approval workflows
* Cloud database support
* Advanced role and permission management
* AI-powered project insights
* Predictive ROI analysis

---

## Learning & Development

This project provided practical experience with:

* Full-stack application development
* REST API development
* React application architecture
* Database integration
* SQL and data management
* Financial KPI calculations
* Excel data automation
* Authentication and authorization
* Role-based access control
* Data visualization
* Business analytics
* Frontend and backend integration

---

## Author

**Nikunj Saini**

B.Tech — Artificial Intelligence & Data Science

**Portfolio:**
https://nikunjsaini.netlify.app/

**GitHub:**
https://github.com/Nikunj-Saini

---

## License

This project is intended for educational, portfolio, and organizational use. Add an appropriate open-source license if the repository is intended for public distribution.
