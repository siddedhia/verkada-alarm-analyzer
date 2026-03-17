# Verkada Alarm Analyzer `v0.1`

A client-side dashboard for analyzing Verkada Command alarm event CSV exports. Upload your CSV and instantly see which sites and devices are driving alarm volume — with enforcement risk tracking and actionable recommendations.

## Features

- **Month Tabs** — filter the entire dashboard by month (defaults to latest)
- **Summary Cards** — total alarms, active sites, unique devices, dispatch rate
- **Enforcement Risk Monitor** — tracks the 15 alarm/site/month limit, excludes self-monitored alarms, shows consecutive months over limit with per-month status (No Risk, Over 1st, Over 2nd, Enforced, Avoided)
- **Top Alarming Sites** — ranked by alarm count with top device, device type, and peak hour
- **Top Alarming Devices (Cameras & Sensors)** — unique per site, filterable by site, with device type
- **Time Analysis** — hourly distribution, day-of-week, daily trend (with zero-fill), and heatmap — all filterable by site
- **Actionable Suggestions** — root-cause-aligned recommendations filterable by site, based on the Verkada Alarm Limit Enforcement framework:
  - Camera Misconfiguration
  - Authorized Activity
  - Schedule & Arm/Disarm Hygiene
  - Perimeter / Outdoor Monitoring
  - Noisy Sensors
  - Testing Activity
  - Response Level Mismatch
- **Data Table** — searchable raw alarm records
- **Responsive** — works on desktop, tablet, and mobile

## Expected CSV Format

The CSV should contain these columns from a Verkada Command alarm events export:

| Column | Example |
|---|---|
| Date | `3/15/2026, 2:30:00 PM` |
| Site | `CA Some Location Name` |
| Partition | `Exterior` |
| Device Name | `Front Entrance Camera` |
| Device Type | `Camera` |
| Alarm Response | `Self-Monitored` |
| Dispatch Requested | `Yes` / `No` |

### Alarm Response Types

- Self-Monitored (excluded from enforcement count)
- Video Verification Only
- Standard
- Immediate Dispatch

## Enforcement Logic

Based on Verkada's Alarm Limit Enforcement policy:

- **15 alarms/site/month** limit (self-monitored excluded)
- **3 consecutive months** over limit before enforcement
- **1 month** under limit resets the streak
- Enforcement = site goes to self-monitoring for the rest of that month

## Usage

1. Visit the deployed site or open `index.html` in a browser
2. Drag & drop or select your Verkada alarm CSV
3. Explore the dashboard — use month tabs and site pickers to drill down

## Deployment

Hosted on Cloudflare Pages with auto-deploy from GitHub on every push to `main`.

## Tech

- Pure HTML/CSS/JS — no build step, no backend
- [Chart.js](https://www.chartjs.org/) for visualizations
- [PapaParse](https://www.papaparse.com/) for CSV parsing
- All processing happens client-side — your data never leaves the browser
