# PowerSchool Scraper

A Playwright-based scraper that extracts student gradebook data from PowerSchool (a common K-12 student information system), normalizes it into a local SQLite store, and surfaces it through a parent-facing dashboard with configurable alerts.

> *This repo is a public overview. The running code is private.*

---

## What it is

PowerSchool's parent portal is hard to navigate — multiple logins, buried menus, no cross-course view, no trend analysis. This scraper bypasses the UX by talking directly to the gradebook endpoints, then presents everything as a clean dashboard and a ruleset-driven alert system.

## What it does

- **Authenticates via session reuse** (Playwright + stored browser profile — no password handling)
- **Pulls gradebook, assignment, and attendance data** on a scheduled cadence
- **Normalizes into SQLite** with historical snapshots so you can see when a grade changed, not just the latest value
- **Runs a rules engine** — alerts fire on trigger conditions (e.g., "new zero grade", "missing assignment past due", "grade drop > N points")
- **Delivers alerts to Discord** so parents don't have to check a portal manually

## Software

| Layer | Tech |
|---|---|
| Scraper | Python, Playwright (session reuse pattern) |
| Storage | SQLite with snapshot tables for history |
| Alerts | Discord webhooks, configurable rule evaluation |
| Scheduling | `launchd` |

## What this demonstrates

- **Working around bad vendor UX** — the "UI is the API" pattern for systems with no official API
- **Session-reuse scraping** — more robust than password automation, avoids re-auth issues
- **Rules engine design** — declarative alert configuration decoupled from the scraper
- **Real problem, real users** — built to solve an actual daily friction

## Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)
![Discord](https://img.shields.io/badge/Discord-5865F2?style=flat&logo=discord&logoColor=white)

---

Part of the AIOS portfolio. See the [profile README](https://github.com/mikecutillo) for the full system map.
