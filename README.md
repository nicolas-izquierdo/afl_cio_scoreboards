# AFL-CIO Legislative Scoreboards

<p align="left">
  <img src="https://img.shields.io/badge/Coverage-1980--2025-blue">
  <img src="https://img.shields.io/badge/Chamber-House-lightgrey">
  <img src="https://img.shields.io/badge/Status-Active-success">
  <img src="https://img.shields.io/badge/Use-Academic%20%26%20Non--Commercial-orange">
</p>

<p align="center">
  <img src="screenshot.png" alt="AFL-CIO Scoreboard Example" width="85%">
</p>

<p align="center">
  <em>Example AFL-CIO legislative scoreboard (archival scan)</em>
</p>

---

This repository provides AFL-CIO **legislative scoreboards** of the U.S. House between 1980 and 2025. In particular, it provides (1) data on AFL-CIO–selected bills and (2) R code to score legislators’ behavior on those votes.

> **Status:** Extension to additional years and the U.S. Senate is ongoing.

---

## Download

| File | Description | Download |
|---|---|---|
| `bills.xlsx` | Complete pooled House dataset for all available AFL-CIO scoreboards, 1980–2025. | [Download](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/bills.xlsx) |

---

## Sources

Relevant data are drawn from:

- 📄 AFL-CIO publications (current and archived versions via the [Wayback Machine](https://web.archive.org/))  
- 📰 Historical issues of *AFL-CIO News* available at the [Internet Archive AFL-CIO News collection](https://archive.org/search?query=creator%3A%22AFL-CIO%22+%22news%22)  
- 🗳️ [Clerk of the House](https://clerk.house.gov)  
- 📊 [VoteView](https://voteview.com)  

---

## Data Structure

The dataset provides bill-level information linking AFL-CIO scorecards to VoteView records.

| Variable | Type | Description |
|---|---|---|
| `congress` | integer | U.S. Congress number |
| `year` | integer | AFL-CIO scorecard year |
| `aflcio_num` | integer | AFL-CIO vote number |
| `rollcall` | integer | Clerk roll call number |
| `vv_rollnumber` | integer | VoteView roll call |
| `date` | datetime | Vote date |
| `chamber` | string | House or Senate |
| `bill_type` | string | Type (H.R., etc.) |
| `bill_number` | string | Bill number |
| `bill_title` | string | AFL-CIO title |
| `bill_id` | string | Combined ID |
| `question` | string | Vote description |
| `result` | string | Outcome |
| `yea_total` | integer | Yes votes |
| `nay_total` | integer | No votes |
| `nv_total` | integer | Not voting |
| `aflcio_position` | string | AFL-CIO stance |
| `aflcio_label` | string | Label meaning |
| `aflcio_topic` | string | Topic |
| `aflcio_description` | string | Full description |
| `url` | string | VoteView link |

---

## License and Use

This repository is intended for **academic and non-commercial use**.

- The **dataset and code** are freely available for research, replication, and teaching.  
- The **AFL-CIO source materials** are included for scholarly use only.  

> ⚠️ **Notice on source materials**  
> Some documents originate from AFL-CIO publications. This repository does not claim ownership of those materials. They are reproduced in good faith for non-commercial academic purposes.
