# Does Money Buy Wins in the NBA?

**Live Site:** [your-github-username.github.io/your-repo-name](#) ← update this link after deploying

**Original Story:** ["The Payroll and Competitive Balance Myth"](https://www.espn.com/blog/truehoop/post/_/id/32841/the-payroll-and-competitive-balance-myth) — Tom Haberstroh, ESPN TrueHoop

## Overview

This project remixes Tom Haberstroh (from ESPN Truehoop)'s 2011 argument that NBA payroll doesn't significantly predict team success. Using twelve years of payroll and win data since then (2014-2025), I look at whether that claim still holds in the modern era, and argue that the relationship between money and winning has strengthened significantly since the original piece was written.

## Making Of

### Story Selection

I chose to remix Haberstroh's "The Payroll and Competitive Balance Myth" because it makes an interesting, testable claim using data, which is the kind of argument that benefits from being revisited often with new numbers. The original piece was written in 2011, before the luxury tax fully took place and before superteams became dominant. I predicted that the story had changed, and my data confirmed it. My remix argues against the original article, using the scatter plot and champions bar chart to refute the author's argument for competitive balance with 2014–2025 data. Even though the original argument was true for its time, the NBA's financial outlook has changed in ways that make payroll a stronger predictor of success today.

### Data Collection

I used three data sources:

- **Payroll data:** Spotrac NBA Cap Tracker (2014–2025), collected season by season using the year parameter in the URL. I used the "Total Cap Allocations" column to represent total team spending.
- **Win totals:** Basketball Reference season standings pages, collected year by year.
- **Champion history:** Basketball Reference League Index, which lists the champion for each season in one table.

I collected the data manually into a Excel spreadsheet titled `payroll_wins.csv`, then converted from wide format (one row per team, one column per year) into long format (one row per team-season) using a Python script. I created a separate `champions.csv` file to cross-reference each champion's payroll rank within their season.

### Design Decisions

**Aesthetic and Layout:** I chose an editorial magazine style with a red/cream/dark blue palette. My goal was for my story to feel like a genuine data journalism piece, and also to reflect NBA colors.

**Visualization 1 — Bar Chart (Champions by Payroll Rank):**
This is the simplest visualization and I intentionally placed it first to get the reader's attention with a clean chart. I used Chart.js rather than D3 here because the data is static (12 data points) and Chart.js produces cleaner, easier-to-read bar charts. Color is used to represent the champion's spending tier: dark red for top-5 spenders, lighter red for top-10, and gray for outliers. This shows the key observation in the data: most champions spend heavily, but not all.

**Visualization 2 — Scatter Plot (Payroll vs. Wins):**
Built with D3 using our in-class workshop's scatterplot pattern (Parts 3–7). Each dot represents one team-season. Color is used to represent playoff status (red = playoffs, gray = missed). I added a year filter using clickable buttons so readers can observe single seasons and watch the trend over time. A regression trend line redraws with each time a filter is applied, emphasizing my argument visually. I added hover tooltips to follow our workshop's mousemove pattern.

**Visualization 3 — Multiline Chart (Payroll Over Time):**
Built with D3 using our in-class workshop's multiline graph pattern (Part 11). One line per team across all 12 seasons. The key design challenge was readability with 30 overlapping lines, which I addressed by making all lines semi-transparent by default and using a hover interaction (using our workshop's `.on("mouseover")` pattern) to highlight one team at a time while keeping others faded. This lets readers observe individual team trajectories without being overstimulated.

**Text integration:** Each visualization is introduced by short explanations of what to look for, followed by a caption, and followed by another short explanation that draws a conclusion. This structure ensures that the story works even without interacting with the charts.

### Technical Design

My story is in a single `index.html` file with embedded CSS and JavaScript files. I used D3 v6 for the scatter plot and line chart (using our workshop tutorial). I used Chart.js for the bar chart. I loaded the data from two CSV files in the `data/` folder using `d3.csv()`, and ran a local server (`python -m http.server`) during development.

I deployed this page via GitHub Pages.


## Data Sources

| Dataset | Source | URL |
|---|---|---|
| Team payrolls (2014–2025) | Spotrac NBA Cap Tracker | https://www.spotrac.com/nba/cap-tracker/ |
| Win totals & standings | Basketball Reference | https://www.basketball-reference.com/leagues/ |
| Championship history | Basketball Reference League Index | https://www.basketball-reference.com/leagues/ |

---

## AI Usage

Claude Sonnet 4 was used to assist with:
- Converting the payroll spreadsheet from wide to long CSV format (Python script)
- HTML/CSS debugging

All data collection, design decisions, visualization choices, and final edits are the author's own. The story argument and framing were developed independently.

## Original Authors Credit

Original story: **"The Payroll and Competitive Balance Myth"** by Tom Haberstroh from ESPN TrueHoop.
My remix updates and argues against parts of the original piece using data from 2014–2025.

## Extra Credit

### Live Deployment (1pt)
I deployed my story as a live webpage via GitHub Pages.
**Live link:** https://visdesignstudies.github.io/module-two-storytelling-remix-bhavikal/

### Counter-argument / Multiple Views (3pts)
My remix argues against Haberstroh's original piece. My conclusion
section directly addresses the original article's claim of competitive balance and uses
two visualizations — the scatter plot (payroll vs. wins, 2014–2025) and the champions
bar chart (payroll rank of each title winner) — to refute it with modern data. I explain both charts and how they contradict the original argument.