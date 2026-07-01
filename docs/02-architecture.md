
# Architecture

**Project:** Career Journal

**Version:** 1.0

**Last Updated:** 2026-07-01

**Status:** Draft

---

# Architecture Overview

Career Journal is designed as a modular application.

The MVP focuses on personal job application tracking, while the overall architecture is prepared for future expansion into a community-driven career platform with automated job aggregation and AI-powered recommendations.

The architecture is divided into two independent workspaces:

* Public Workspace
* Personal Workspace

This separation keeps user data private while allowing the community to build a shared company directory.

---

# System Overview

```
                    Public Workspace
            ┌──────────────────────────┐
            │      Company Directory    │
            │   Career Websites         │
            │   Industries              │
            │   Locations               │
            └─────────────┬─────────────┘
                          │
                          │
            Shared Company Database
                          │
──────────────────────────┼──────────────────────────
                          │
                          ▼
                  Personal Workspace
            ┌──────────────────────────┐
            │ Job Applications         │
            │ Pipeline                 │
            │ Tasks                    │
            │ Notes                    │
            │ Documents                │
            │ Analytics                │
            └──────────────────────────┘
```

---

# Module 1 – Authentication

Responsible for:

* User registration
* Login
* User profile
* Session management

Every personal record belongs to exactly one authenticated user.

---

# Module 2 – Company Directory

The Company Directory is the only shared database inside the application.

Its purpose is to maintain a clean catalogue of companies that users can reference when creating job applications.

Each company contains:

* Company name
* Industry
* Headquarters
* Career website
* Locations
* Website
* Description (optional)

Future versions may include:

* ATS platform
* Company size
* Logo
* Social links

---

# Module 3 – Job Applications

Each application represents one position the user has applied for.

Applications are private.

Each application references one company from the Company Directory.

An application contains:

* Position
* Company
* Application date
* Source
* Status
* Job URL
* Salary (optional)
* Notes
* Next action date

---

# Module 4 – Application Pipeline

Applications move through predefined stages.

Default stages:

* Wishlist
* Applied
* Recruiter Contact
* HR Interview
* Technical Interview
* Final Interview
* Offer
* Accepted
* Rejected
* Withdrawn

Future versions may allow users to customize their own pipeline.

---

# Module 5 – Tasks

Tasks help users organize their job search.

Examples:

* Send follow-up email
* Prepare for interview
* Update CV
* Complete assessment

Each task includes:

* Due date
* Priority
* Status
* Related application

---

# Module 6 – Notes

Users can create unlimited notes for every application.

Typical notes:

* Interview feedback
* Recruiter communication
* Technical questions
* Salary discussion

---

# Module 7 – Documents

Users can attach files to an application.

Supported document types:

* Resume
* Cover Letter
* Portfolio
* Certificates

Each application can contain multiple documents.

---

# Module 8 – Dashboard

The Dashboard provides a real-time overview of the user's job search.

Main widgets:

* Active applications
* Upcoming tasks
* Interview schedule
* Recent activity
* Quick statistics

---

# Module 9 – Analytics

Analytics transforms application history into useful insights.

Examples:

* Applications over time
* Response rate
* Interview rate
* Offer rate
* Rejection rate
* Average response time
* Applications by source
* Applications by company

The goal is to help users improve their job search strategy through measurable data.

---

# Module 10 – Community Features

The application includes a shared Company Directory.

Registered users can:

* Add new companies
* Suggest edits
* Report duplicate companies

Future versions may introduce moderation workflows.

---

# Security Model

Public data

* Companies
* Industries
* Locations

Private data

* Applications
* Notes
* Tasks
* Documents
* Analytics

Every personal record is protected using Row Level Security (RLS).

---

# Scalability

The architecture is intentionally designed to support future modules without requiring database redesign.

Planned future modules include:

* Automatic job aggregation
* AI recommendations
* Community statistics
* Calendar integration
* Email integration

---

# Design Principles

Career Journal follows six core principles:

* Simplicity before complexity
* Privacy by default
* Community contribution
* Data-driven insights
* Modular architecture
* AI-ready foundation

Every new feature should support at least one of these principles.
