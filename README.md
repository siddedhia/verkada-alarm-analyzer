# Verkada Alarm Analyzer

A client-side dashboard for analyzing Verkada Command alarm event CSV exports. Upload your CSV and instantly see which sites and devices are driving alarm volume — with actionable recommendations.

## Features

- **Summary cards** — total alarms, active sites, unique devices, dispatch rate
- **Top Sites** — ranked by alarm count with top device, type, and peak hour
- **Top Devices** — unique per site, filterable by site, with device type
- **Worst Offender Deep Dive** — detailed breakdown of the highest-volume site + device combo
- **Time Analysis** — hourly, day-of-week, daily trend, and heatmap views (filterable by site)
- **Actionable Suggestions** — rule-based recommendations derived from alarm patterns
- **Data Table** — searchable raw alarm records
- **Month Tabs** — filter the entire dashboard by month

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

- Self-Monitored
- Video Verification Only
- Standard
- Immediate Dispatch

## Usage

1. Open `verkada-alarm-analyzer.html` in a browser
2. Drag & drop or select your Verkada alarm CSV
3. Explore the dashboard

## Tech

- Pure HTML/CSS/JS — no build step, no backend
- [Chart.js](https://www.chartjs.org/) for visualizations
- [PapaParse](https://www.papaparse.com/) for CSV parsing
- All processing happens client-side — your data never leaves the browser
