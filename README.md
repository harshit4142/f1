# F1 Race Intelligence — Standardized SkillWallet Descriptions

**Purpose:** Copy-ready, professional text for the SkillWallet project sections shown in the screenshots. The wording is based on the supplied Excel workbook and the documented dashboard/story layout. Replace any claim that does not match the final workbook, and insert actual public links or measured timings where indicated.

## Verified data profile

| Sheet | Rows | Columns |
|---|---:|---:|
| race_results | 6,464 | 42 |
| qualifying_results | 3,130 | 16 |
| lap_intelligence | 3,814 | 14 |
| championship_standings | 311 | 10 |
| circuits | 29 | 9 |
| TOTAL | 13,748 | — |

Additional profile: 17 season values (2010–2026) in the season-bearing tables; 29 circuit records in the circuits reference sheet; 24 distinct circuit IDs in race_results; 10 teams and 19 driver names in race_results; 21 countries represented in race_results; 396 rows flagged as DNF.

**Data quality note:** The source file is an Excel workbook. Its historical accuracy has not been independently verified, and some driver-season combinations appear chronologically inconsistent. Describe it as the *provided project dataset* unless the underlying records have been audited against an authoritative source.

## 1. Data Collection & Extraction from Database

### Downloading the Dataset

The project uses the provided F1 Racing Project Dataset.xlsx workbook as its source file. It contains five sheets: race_results, qualifying_results, lap_intelligence, championship_standings, and circuits. Before analysis, the file and sheet names were checked and the workbook was retained as the source of record. The supplied source is an Excel workbook, not a live database extraction; the project description should not claim a live database connection unless one was actually used.

### Connect Dataset with Tableau

The Excel workbook was connected to Tableau Desktop through the Microsoft Excel connector. The five tabs were reviewed at their appropriate levels of detail before relationships were defined. The race_results sheet serves as the principal race-level analysis table; circuits can be related through circuit_id. qualifying_results and lap_intelligence contain race-level identifiers and should be related only on verified matching keys. championship_standings is a season/driver/team-level table and should not be joined indiscriminately to race rows, as that can duplicate values. Field types were reviewed so dates, numeric measures, flags, and categories are interpreted correctly.

## 2. Data Preparation

### Prepare the Data for Visualization

The workbook was profiled before chart creation. The provided data contains 13,748 rows across five sheets, including 6,464 rows and 42 columns in race_results. Missing finish positions are retained where a driver did not finish; DNF and dnf_reason fields are used to analyse retirements rather than treating those records as ordinary finishing positions. Numeric fields such as points, lap times, speeds, and temperature should be stored as measures, while fields such as driver, team, country, circuit type, tyre compound, and DNF reason should be dimensions. Date fields should be parsed as dates. Missing values are not automatically replaced with zero unless zero has a valid business meaning. Any relationship or join should be checked for duplicated rows and inflated totals.

## 3. Data Visualization

### Number of Unique Visualizations

The dashboard contains nine visualization components: (1) KPI summary cards, (2) a geographic view of race participation by country, (3) a stacked bar chart for driver reliability by DNF reason, (4) a driver performance leaderboard, (5) a horizontal team performance ranking, (6) a team championship performance chart, (7) a tyre-compound usage pie chart, (8) a country participation treemap/highlight view, and (9) a packed-bubble view of podium achievements by driver and team. Each view should have a clear title, readable labels, useful tooltips, and an appropriate aggregation. The KPI cards are grouped as one summary component when reporting the count of nine views.

## 4. Dashboard

### Responsive Design of Dashboard

The dashboard uses a Formula 1-inspired dark canvas with red and white accents, a clear title area, summary KPIs, global filters, and a structured grid of charts. The summary metrics shown are competing teams, seasons represented, race-result records, and circuits represented; the exact values should match the fields and filters in the published workbook. The DNF Reason filter, Year of Race Date filter, and Top N parameter are positioned so users can change the analysis without searching through individual worksheets. Chart titles, contrast, spacing, and label sizes should remain legible at the intended display size. Describe the dashboard as responsive only after checking Tableau device layouts or testing it at the target desktop/tablet/mobile sizes.

## 5. Story

### Number of Scenes in a Story

The Tableau Story contains nine scenes arranged as a guided explanation: global overview and KPIs; geographic race participation; driver reliability and DNF patterns; driver performance; team performance ranking; season-by-season championship performance; tyre-compound usage; country-wise event participation; and podium achievements by driver and team. Each scene should add a distinct analytical point rather than simply repeat the previous chart. Use a concise scene title and a short caption to explain what the viewer should notice. Confirm that all nine scenes are present and that navigation works before reporting the final count.

## 6. Performance Testing

### Amount of Data Rendered to Tableau

The supplied workbook contains 13,748 rows across five sheets. The primary race_results table contains 6,464 rows and 42 columns. The workbook covers season values from 2010 through 2026 in the supplied data, includes 29 rows in the circuits reference sheet, and represents 24 distinct circuit identifiers in race_results. These are dataset-profile figures, not claims that every row is an independently verified official Formula 1 result. Before submission, confirm that Tableau’s data source row counts match the source workbook and that relationships do not inflate measures.

### Utilization of Filters

Three dashboard-level controls are documented: DNF Reason, Year of Race Date, and Top N. Test each filter independently and in combination. Confirm that DNF Reason changes the reliability analysis and related race-result views as intended; the year control restricts results to the selected season or range; and Top N changes the number of drivers shown in the leaderboard. Also test the reset/clear state and check that titles, legends, tooltips, and KPI totals remain consistent with the applied filters. Report only tests that were actually completed.

### Number of Calculation Fields

The workbook is intended to use a small set of calculations and a parameter rather than duplicating data preparation inside Tableau. The documented calculation examples are a DNF Count measure and a Points Cumulative running total; the Top N control is a parameter, not a calculated field by itself. Verify the exact field names and formulas in the final workbook and update this description if the implementation differs. Avoid reporting a calculation count until the fields in the Data pane have been counted and checked.

### Number of Visualizations / Graphs

Nine visualization components are listed in the dashboard inventory: KPI summary, geographic participation map, driver reliability stacked bars, driver leaderboard, team ranking bars, team championship performance chart, tyre-compound pie chart, country participation treemap/highlight view, and podium packed bubbles. For a performance check, confirm that each view renders with the intended dataset, tooltips and labels display correctly, and filters do not produce blank or duplicated results. Record the measured initial load and filter-response times only if they were actually timed; do not use “fast” or “within acceptable limits” without a test result.

## 7. Web Integration

### Publishing Dashboard and Story to Tableau Public

The dashboard and Story can be shared through Tableau Public after the workbook has been checked for correct data, titles, filters, and view access. Before publishing, remove unused sheets and confirm that the workbook contains only data that is appropriate to make public. After publishing, open the public URL in a private/incognito browser window to confirm that viewers can access it without your desktop session. Add the actual Tableau Public dashboard and Story URLs to the SkillWallet resource fields; do not describe the publication as complete until those URLs have been verified.

### Web Integration of Dashboard and Story

The project web page presents the Formula 1 Race Intelligence project and embeds the published Tableau dashboard and Story so viewers can explore the visual analysis in a browser. In the documented implementation, Flask serves the application page and the Tableau Public embed provides the visualization experience. The embed should use the real published URL, fit the available page width, and preserve the available Tableau interactions. Verify the page on desktop and a narrower viewport, test both embedded views, and provide the actual deployed application URL and source repository URL. If the application only runs locally, label it as a local demo rather than a public deployment.

## 8. Project Demonstration & Documentation

### Project Demonstration and Documentation

The final submission should include the packaged Tableau workbook (.twbx), the original Excel dataset or an approved link to it, a README with setup and usage instructions, a dashboard preview image, the Tableau Public links if published, and the web application source and run instructions if web integration is part of the deliverable. The README should explain the five source sheets, the key relationships, the dashboard views, the filter controls, and any calculated fields or parameters. Include screenshots that show the actual final workbook and functioning filters. Remove credentials, personal access tokens, and other secrets before pushing source files to GitHub.

## Submission quality checklist

- [ ] Data row counts in Tableau match the workbook; relationships do not duplicate points or records.
- [ ] All nine dashboard components render and have descriptive titles/tooltips.
- [ ] DNF Reason, Year of Race Date, and Top N work separately and together.
- [ ] All nine Story scenes exist and can be navigated in sequence.
- [ ] Responsive/device-layout claims have been tested at the stated screen sizes.
- [ ] Any performance timings are measured and recorded, not estimated.
- [ ] Tableau Public and web-app links are real, accessible URLs.
- [ ] GitHub contains the workbook, README, preview image, and permitted source files; no secrets are committed.
