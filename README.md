# Story Tracker — Jira Evolution Hub

A lightweight, browser-based checklist and progress tracking tool for Agile/Scrum teams. It helps **Business Analysts, Developers, and Testers** independently track their work on a Jira story and merge everything into a single final report — with zero installation, zero backend, and zero cost.

---

## Table of Contents

- [Overview](#overview)
- [Use Cases](#use-cases)
- [Pages & Features](#pages--features)
  - [Hub (index.html)](#hub-indexhtml)
  - [BA Page (ba.html)](#ba-page-bahtml)
  - [Developer Page (dev.html)](#developer-page-devhtml)
  - [Tester Page (tester.html)](#tester-page-testerhtml)
- [Workflow](#workflow)
- [File Structure](#file-structure)
- [Tech Stack](#tech-stack)
- [How to Use Locally](#how-to-use-locally)
- [Data & Privacy](#data--privacy)

---

## Overview

Story Tracker is a **static web application** — no server, no database, no login. Each team member opens the relevant role page in their browser, fills in their details, and downloads a `.json` report. The **Hub page** accepts all three `.json` files and generates a single, unified final report (HTML) that covers the complete lifecycle of a Jira story from BA sign-off to QA sign-off.

---

## Use Cases

### Agile / Scrum Teams
Track every Jira story end-to-end. Each role fills their page independently and the team lead merges them in the hub for a delivery checklist summary.

### Sprint Release Reviews
Generate a clean, printable HTML report for every story before a sprint release. Attach it to the Jira ticket or share with stakeholders.

### Audit & Compliance
Keep a documented trail of who did what, when — FSD sign-offs, code reviews, test evidence, defect logs — all in one downloadable report.

### Remote / Distributed Teams
No shared server needed. Each member downloads their `.json` from their own machine and sends it (email, Teams, Slack) to whoever is compiling the final report.

### Onboarding
New team members get a clear picture of the full story lifecycle and what is expected from each role — BA, Dev, and QA — in a structured checklist format.

---

## Pages & Features

### Hub (`index.html`)
The central control page.

| Feature | Details |
|---|---|
| Story Info | Enter Jira number, story title, sprint, module, priority, and description |
| Role Navigation | Cards to open BA, Dev, and Tester pages directly |
| JSON Upload | Upload `.json` exports from all three role pages (in any order) |
| Live Preview | Instantly renders a merged summary — progress bars, checklist status, links, sign-off proofs |
| Final Report | Download a fully formatted standalone `.html` report covering all three roles |
| Reset | Clears hub state and all upload slots |

---

### BA Page (`ba.html`)
For the **Business Analyst**.

| Feature | Details |
|---|---|
| BA Details | Name, Jira number, FSD start/end dates, validator name |
| Requirement Brief | Free text summary of the business requirement |
| FSD Modification History | Add multiple FSD modification entries with version, date, description, and CEB link |
| Sign-off Proof | Toggle between pasting a link **or** uploading a screenshot of the sign-off mail |
| Download JSON | Exports all BA data as a `.json` file for hub upload |
| Download HTML Report | Generates a standalone purple-themed BA report |
| Auto-save | All data is saved to browser localStorage automatically |

---

### Developer Page (`dev.html`)
For the **Developer**.

| Feature | Details |
|---|---|
| Dev Details | Name, Jira number, start/end dates, reviewer name, review date |
| Code Review Recording | Paste a Teams/meeting URL with a quick-open button |
| Implementation Progress | Slider showing % of code implementation complete |
| 9-Step Development Checklist | Tracks: Jira & FSD Understanding → WBS → TDD → Code Implementation → Unit Testing → Full Impact Analysis → Code Review → Sign-off Mail → Release Track Folder |
| Document Links | Direct URL inputs for WBS, TDD, UT doc, and Full Impact Analysis — each with a one-click open button |
| Sign-off Mail Proof | Toggle between link and image upload |
| Download JSON | Exports all dev data for hub upload |
| Download HTML Report | Generates a standalone blue-themed developer report |
| Auto-save | localStorage persistence per Jira number |

---

### Tester Page (`tester.html`)
For the **QA Tester**.

| Feature | Details |
|---|---|
| Tester Details | Name, Jira number, testing start/end dates |
| Test Metrics | Total scenarios, executed, passed, failed — with auto-calculated progress bar |
| Test Proof Link | URL to test evidence or proof document with a quick-open button |
| Defect Tracker | Add defects with: defect ID, severity (Critical/Major/Minor/Trivial), status (Open/In Progress/Fixed/Closed/Retest), description, and raised date |
| Download JSON | Exports all tester data for hub upload |
| Download HTML Report | Generates a standalone teal-themed tester report |
| Auto-save | localStorage persistence per Jira number |

---

## Workflow

```
1. BA fills ba.html         →  Downloads ba_report.json
        ↓
2. Dev fills dev.html       →  Downloads dev_report.json
        ↓
3. Tester fills tester.html →  Downloads tester_report.json
        ↓
4. Hub (index.html)
   - Upload all 3 JSON files (any order)
   - Review merged live preview
   - Download Final Report (.html)
        ↓
5. Final report shared with team / attached to Jira
```

Each role page works **independently** — team members do not need to coordinate timing or share a system.

---

## File Structure

```
/
├── index.html       ← Hub — upload, merge, final report
├── ba.html          ← Business Analyst page
├── dev.html         ← Developer page
├── tester.html      ← Tester page
├── shared.css       ← Common stylesheet for all pages
└── README.md        ← This file
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 (custom properties, CSS Grid, Flexbox) |
| Logic | Vanilla JavaScript (ES6) |
| Storage | Browser `localStorage` |
| File I/O | `FileReader` API (JSON/image upload), `Blob + URL.createObjectURL` (downloads) |
| Build | None — open directly in any browser |
| Hosting | Works locally or on any static host (GitHub Pages, Netlify, etc.) |

---

## How to Use Locally

1. Download or clone this repository
2. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari)
3. No server or install needed — it runs entirely in the browser

> Each team member should open the relevant role page (`ba.html`, `dev.html`, or `tester.html`) from their own machine.

---

## Data & Privacy

- **All data stays in the browser.** Nothing is sent to any server.
- Data is saved per Jira number in `localStorage` — clearing browser data will erase it.
- The `.json` files downloaded from each role page are the only persistent records — **save them**.
- The final `.html` report is entirely self-contained and can be stored, emailed, or attached to Jira directly.
