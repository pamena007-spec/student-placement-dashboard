# Student Placement Dashboard

A React single-page application that helps students browse placement opportunities, apply to them, track applications, receive notifications, manage a profile and view placement statistics.

> **Important:** this is a frontend-only college project.
> - **Authentication is simulated.** Accounts and passwords are saved in the browser's `localStorage` in plain text. This is a demo and is **not production authentication**.
> - **All companies, jobs, announcements and statistics are sample data.** They are not real vacancies or real placement figures.

## Features

| Module | What it does |
| --- | --- |
| Authentication | Login, registration, logout, protected routes, show/hide password, validation, loading and error states |
| Dashboard | Summary cards, upcoming interviews, recent applications, deadlines, announcements, placement statistics |
| Opportunities | Job cards with company, title, type, location, package, skills, eligibility, deadline, posted date, description |
| Search and filters | Search by company, title or skill; filters for company, location, job type, package, skill, eligibility and deadline; Clear Filters |
| Apply | Confirmation dialog with resume check, optional note, duplicate prevention, success message |
| Application tracking | Status tabs, interview details, timeline history, withdraw, demo status updates |
| Analytics | Recharts: status pie chart, pipeline chart, placement trend, package bands, top recruiters, department placement |
| Notifications | Created when you apply or when a status changes; mark as read, mark all, clear |
| Profile | Edit details, skills, resume status; profile completion percentage |
| Responsive UI | Sidebar becomes a slide-in menu on tablets and phones |

## Demo account

- Email: `demo@student.com`
- Password: `Demo@1234`

The demo account comes with sample applications and notifications. Any new account you register starts empty.

## Technologies Used

React 18, Vite, React Router DOM v6, React Hooks, Context API, Fetch API, Recharts, JavaScript ES6+, HTML5, CSS3, npm, Git and GitHub.

## How to Run

1. Install Node.js (version 18 or newer).
2. Open the project folder in VS Code.
3. Run `npm install`.
4. Run `npm run dev` and open the address shown (usually http://localhost:5173).
5. Log in with the demo account or register a new student.

Other commands: `npm run build` and `npm run preview`.

## Project Structure

```
placement-dashboard/
├── index.html
├── package.json
├── vite.config.js
├── public/data/            Mock REST data loaded with fetch()
│   ├── jobs.json
│   ├── announcements.json
│   └── placementStats.json
└── src/
    ├── main.jsx            Entry point, providers, router
    ├── App.jsx             Routes
    ├── constants.js        Statuses, departments, demo credentials
    ├── index.css           All styles
    ├── context/
    │   ├── AuthContext.jsx          Users, session, login, register, profile update
    │   ├── DataContext.jsx          Jobs, announcements, statistics (fetch)
    │   └── ApplicationsContext.jsx  Applications and notifications
    ├── hooks/useLocalStorage.js
    ├── services/api.js
    ├── utils/                  dates, formatting, validators, profile completion
    ├── components/             Layout, JobCard, ApplyModal, StatCard, forms, loaders, etc.
    └── pages/                  Login, Register, Dashboard, Jobs, Applications,
                                Analytics, Notifications, Profile, NotFound
```

## Routes

| Path | Page | Access |
| --- | --- | --- |
| `/login`, `/register` | Authentication | Public (redirects if signed in) |
| `/dashboard` | Dashboard home | Signed-in students |
| `/jobs` | Opportunities, search, filters, apply | Signed-in students |
| `/applications` | Application tracking | Signed-in students |
| `/analytics` | Charts | Signed-in students |
| `/notifications` | Notifications | Signed-in students |
| `/profile` | Profile management | Signed-in students |

## Context API State Management

- **AuthContext:** the list of users, the signed-in session, `login`, `register`, `logout`, `updateProfile`.
- **DataContext:** loads jobs, announcements and statistics with `fetch()` and exposes loading, error and retry.
- **ApplicationsContext:** the signed-in student's applications and notifications, with `applyToJob`, `updateStatus`, `withdrawApplication` and notification actions. It reloads for each student because `App.jsx` gives it a `key` based on the user id.

## How Applying Works

1. Click **Apply** on a job card. A dialog shows the job, your resume status and profile completion.
2. If the resume status is "Not uploaded", applying is blocked and you are pointed to the profile page.
3. Add an optional note (up to 300 characters) and submit.
4. The application is saved with status "Applied", a notification is created, and the card shows "Applied ✓" so you cannot apply twice.
5. On the Applications page, use **Update status (demo)** to simulate the employer moving your application along (Under Review, Shortlisted, Interview Scheduled, Selected or Rejected).

## Form Validation

- Login: required email and password, email format, minimum password length.
- Registration: all fields required, email format, password of at least 8 characters with a letter and a number, matching confirmation, 10-digit mobile number.
- Profile: same rules for editable fields, plus skill checks (no blanks, no duplicates, maximum 15).

## Git and GitHub

```bash
git init
git add .
git commit -m "Initial Student Placement Dashboard"
git branch -M main
git remote add origin YOUR_GITHUB_REPOSITORY_URL
git push -u origin main
```

Suggested commit messages:

1. `Set up Vite React project with routing and Context API`
2. `Add login, registration and protected routes`
3. `Build dashboard layout and summary cards`
4. `Add job listings with search and filters`
5. `Implement apply flow and application tracking`
6. `Add analytics charts with Recharts`
7. `Add notifications and profile management`
8. `Improve responsive design and documentation`
