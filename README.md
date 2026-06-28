# Gastimate — PH Hospital Cost Guide

A free, no-sign-up **PWA** that tells Filipinos roughly **how much to prepare** for common
hospital procedures, how much **PhilHealth** may cover, and **where to get help paying**.

It's an **information tool only** — estimates, not quotes; not medical or financial advice.
Real prices vary by hospital and change, so the app always says *"call to confirm."*

## Why
There is no single Philippine app that shows what a procedure will cost across hospitals with
payment/coverage info — people have to call around. This fills that gap for the most common,
high-anxiety procedures, with a bias toward helping low-income patients (the financial-aid
directory is a core feature, not an afterthought).

## Features
- Tap a procedure → **"Prepare roughly ₱X–₱Y"** (private), with a government-hospital comparison
- **PhilHealth** case-rate deduction baked in (toggle "I have active PhilHealth")
- **"What to ask when you call"** + document checklist
- **Where to get help paying**: Malasakit, PCSO, DSWD AICS, congressional/LGU aid, hospital
  charity, PhilHealth Konsulta/YAKAP, NGOs
- **Bilingual** (English / Tagalog), works **offline**, installable to the home screen

## Tech
Plain vanilla HTML/CSS/JS — no framework, no build step. Single `index.html` + a service worker
(`sw.js`) for offline + a web manifest. Bootstrap Icons are inlined as SVG (no external requests).
Deployed as a static site on Vercel.

## Data & accuracy
- **PhilHealth case rates** come from official PhilHealth circulars (public). Updated manually when
  a new circular is issued (a few times a year).
- **Cost ranges** are aggregated from public/secondary sources and shown as *ranges* with a
  confidence label and a "last reviewed" date. They are deliberately approximate.
- There is **no public API** for PH hospital prices or PhilHealth rates, so updates are manual
  today; crowdsourced "what I paid" reports are planned to keep ranges fresh.
- All figures live in the `PROCEDURES`, `AID`, and `PHIL` objects in `index.html` — easy to edit.

## Disclaimer
Estimates only. Always confirm costs and coverage directly with the hospital and PhilHealth.
This project stores no personal data and requires no account.
