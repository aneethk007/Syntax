# Syntax

A single-file classroom dashboard, originally built for a Teachers Day hackathon. One shared space for a teacher and their students to run a live whiteboard, take attendance, hold public Q&A, poll the class, and collect feedback on the day's lesson — all in one chalkboard-turned-clean dashboard UI.

**Live demo:** https://aneethk007.github.io/Syntax/syntax.html

**Team No:** 22

**Problem Statement:** Classrooms run on a patchwork of disconnected tools — one app for attendance, another for sharing notes, a group chat for doubts that gets buried in noise, no easy way to gauge whether a topic actually landed, and no simple channel for students to give honest feedback on how a lesson went. Teachers lose visibility into their class in real time, and students lose a single place to ask, follow, and revisit what happened in class.

**Objective:** Build one unified, real-time classroom dashboard — a shared live whiteboard, attendance tracking, a public doubts board, a quick "repeat this topic?" poll, and a lesson feedback wall — all in a single lightweight app that needs no install, no backend setup, and works the moment a teacher and their students open the same link.

**Technology used:** Built in VS Code, with a little help from Claude (Anthropic) along the way. Under the hood: React (loaded via CDN, no build step or bundler), Babel Standalone for in-browser JSX compilation, the HTML5 Canvas + Pointer Events API for the whiteboard, hand-rolled inline SVG icons, and Claude's artifact platform capabilities (a realtime shared database and live presence/room channel) for cross-device sync — with a local-storage fallback so the app still runs standalone anywhere else.

**Project Link:**
- Live demo: https://aneethk007.github.io/Syntax/syntax.html
- Repository: https://github.com/aneethk007/Syntax

## Screenshots

<!-- Add screenshots here, e.g.: -->
<!-- ![The Board](screenshots/board.png) -->
<!-- ![Ask the Class](screenshots/doubts.png) -->

## Demo Video

<!-- Add your demo video link here, e.g. a YouTube/Drive link, or drag the video file into this README while editing on GitHub -->

## What it does

### 🔐 Login & accounts
- Sign up as a **Student** or **Teacher**, or log in with an existing account.
- Two built-in demo accounts for instant access, no sign-up needed:
  - `teacher` / `teach123` — Ms. Rao
  - `student` / `student123` — Arjun
- Sessions persist per-device, so refreshing the page keeps you logged in.

### ✏️ The Board
A live shared whiteboard. The teacher draws with a canvas — pick from five marker colors, adjust stroke thickness, erase, or clear the board — and every stroke syncs out automatically. Students get a read-only view that refreshes every few seconds, so the whole class watches along in real time.

### 📋 Roll Call
The teacher picks a date and marks each registered student Present or Absent with one click. Students get their own view: a running history of every day they were marked, plus a quick summary of total days present.

### ❓ Ask the Class
A public Q&A board. Students post a doubt (subject + question), optionally attaching a file (like a screenshot of their notes). Everyone — every student and the teacher — can see every question and its answer, not just the person who asked. The teacher replies inline, can attach a file of their own (e.g. reference notes), and marking a reply sent resolves the doubt. Once resolved, anyone can react to the answer with 👍 ❤️ 🎉 🤔.

### 🗳️ Topic Poll
The teacher names what was taught that day and opens a poll: *repeat this topic, or move on?* Students vote once, and results update live for everyone as a simple bar chart — a quick pulse-check the teacher can use to decide whether to revisit something.

### ⭐ Feedback Wall
Students rate and review the day's lesson — a 1–5 star rating plus an optional comment — posted publicly as a card, or anonymously via a "post without my name" option. A running average rating is shown at the top of the wall.

### 🟢 Who's online
A Discord-style presence panel in the sidebar shows which teachers are currently online, live, so students always know if their teacher is around right now.

## Demo accounts

| Role    | Username  | Password     |
|---------|-----------|--------------|
| Teacher | `teacher` | `teach123`   |
| Student | `student` | `student123` |

These bypass storage entirely, so they always work regardless of hosting mode below.

## Two ways this runs

This is a single HTML file, but it behaves differently depending on where you open it:

- **As a Claude Artifact** (the environment it was built for) — every feature is fully synced in real time across every device and browser: accounts, the whiteboard, attendance, doubts, polls, and feedback are all shared classroom-wide through a live backend.
- **Anywhere else** (GitHub Pages, or opened as a local file, like this repo's live demo link above) — there's no backend available, so the app automatically falls back to storing everything in that one browser's local storage instead. Every feature still works, but data stays on that single device rather than syncing across a class. A small notice on the login screen makes this clear. It's a great way to try the whole app solo.

## Tech

- Single-file **React** app — no build step, no bundler.
- React, ReactDOM, and Babel Standalone loaded from CDN; JSX compiled in-browser.
- Hand-rolled inline SVG icons (no icon library dependency).
- Canvas-based whiteboard using the Pointer Events API (mouse, touch, and pen all work).
- Light and dark mode, switchable per-user, remembered per device.
- IBM Plex Sans + Lexend for type; a small custom `</>` mark as the logo.

## Project structure

