---
title: Bulk Venue Setup Automation
headline: Turning hundreds of manual form entries into a validated, re-runnable automated setup
summary: An Excel-driven automation that creates test venues, rooms and reservations in the booking portal, with pre-flight checks and safety guards built in. It created 370 records in one run with zero failures.
category: Operational automation · AI-assisted
order: 4
role: Digital Platform Manager (designed and built, with an AI coding assistant)
period: Oct 2026
facts:
  - label: Scope
    value: ~86 venues, each with rooms and system reservations
  - label: Stack
    value: Python · Playwright · Excel
  - label: Status
    value: Validated in UAT, ready for production setup
metrics:
  - value: "0"
    label: Failures across 10 venues, 120 rooms and 240 reservations in one run
    short: Failures in a 370-record run
  - value: "~3 min"
    label: Per venue with 12 rooms and 24 reservations, running unattended
    short: Per venue, end to end
  - value: "29%"
    label: Faster in headless, full-speed mode than in a visible browser
    short: Faster in headless mode
tags: [Automation, Python, Playwright, Data validation, AI-assisted delivery]
---

## Context

A new booking setup needed about 86 test venues created in the booking portal. Each venue has its own rooms, and each room can have system reservations, so the setup ran to hundreds of records, all entered through multi-step forms.

## The problem

Entering it all by hand would have been slow and repetitive, and easy to get wrong in ways that are hard to spot: a mistyped timezone, a room added twice, a reservation on the wrong room. There was also no record of what had been done, so an interrupted session meant working out where things had stopped.

## What I built

Operations fill in one Excel workbook with three sheets (Venues, Rooms, Reservations). A Python script uses Playwright to work through the portal exactly as a person would.

- **Valid data only:** the workbook's dropdowns are built from values pulled from the portal itself, so only real regions, timezones and countries can be entered.
- **Pre-flight check:** before a browser opens, every row is checked for missing fields, invalid values, bad dates, duplicates and inconsistent capacities. Errors stop the run; warnings don't.
- **Safe to re-run:** every result is logged, completed rows are skipped, and the portal is searched before each venue is created, so nothing is ever created twice.
- **Guard rails:** results are backed up at the start of every run, and the run pauses after five failures in a row so a person can step in.
- **No stored credentials:** a person signs in by hand. For a faster hidden run, the signed-in session is carried into a headless browser and kept in memory only.

## What made it hard

- **An unfriendly UI to automate.** The portal is built on Vaadin, with no stable element IDs and pop-up windows that reuse the same field names as the page behind them. Every lookup had to be scoped to the right window, and a stray Escape key opens a blocking "unsaved data" dialog.
- **Hidden paging.** At scale, rooms started being logged as failed even though they existed. A read-only diagnostic showed the room list is paged 20 at a time, sorted by name. The lookup now steps through every page.
- **Proving it at scale before going live.** I tested in stages: dry runs that never save, a single venue, a 50-room venue with 100 reservations, then 10 venues in one run, timing each step to build a planning formula for the full rollout.

## Outcomes

- **10 venues, 120 rooms and 240 reservations** created in a single run with **zero failures**.
- A 50-room, 100-reservation venue created in one run with zero failures.
- Headless, full-speed mode is **29% faster**: about 3 minutes per typical venue, putting the full ~86-venue setup at around 4.4 hours of run time.
- A repeatable, auditable process: every record is validated before it's entered and logged after.

## What it shows

How I like to work on platform operations: find the manual toil, make it safe before making it fast, and prove it at scale before trusting it. It was also a practical test of AI-assisted delivery. I designed the approach and the safety rules and directed the build, with an AI coding assistant writing much of the code.
