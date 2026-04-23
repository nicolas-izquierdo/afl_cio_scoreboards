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

For each year, the repository provides a bill-level `.xlsx` dataset and, when available, the corresponding AFL-CIO scorecard `.pdf`.

### Full dataset

| File | Description | Download |
|---|---|---|
| `bills.xlsx` | Complete pooled House dataset for all available AFL-CIO scoreboards, 1980–2025. | [Download](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/bills.xlsx) |

### Yearly dataset

<details open>
<summary><strong>1980s</strong></summary>

| Year | Dataset | Scorecard |
|---|---|---|
| 1980 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1980/aflcio_house_votes_1980.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1980/scoreboard_1980.pdf) |
| 1981 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1981/aflcio_house_votes_1981.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1981/scoreboard_1981.pdf) |
| 1982 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1982/aflcio_house_votes_1982.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1982/scoreboard_1982.pdf) |
| 1983 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1983/aflcio_house_votes_1983.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1983/scoreboard_1983.pdf) |
| 1984 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1984/aflcio_house_votes_1984.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1984/scoreboard_1984.pdf) |
| 1985 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1985/aflcio_house_votes_1985.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1985/scoreboard_1985.pdf) |
| 1986 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1986/aflcio_house_votes_1986.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1986/scoreboard_1986.pdf) |
| 1987 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1987/aflcio_house_votes_1987.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1987/scoreboard_1987.pdf) |
| 1988 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1988/aflcio_house_votes_1988.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1988/scoreboard_1988.pdf) |
| 1989 | [XLSX](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1989/aflcio_house_votes_1989.xlsx) | [PDF](https://raw.githubusercontent.com/nicolas-izquierdo/afl_cio_scoreboards/main/HOUSE/1989/scoreboard_1989.pdf) |

</details>

---

## Data Construction

The dataset is constructed in three steps:

1. AFL-CIO legislative scorecards are collected and transcribed using Claude Code  
2. Each vote is matched to its corresponding VoteView roll call  
3. Roll call metadata are retrieved from VoteView  

---

## Sources

Relevant data are drawn from:

- 📄 AFL-CIO publications (current and archived versions via the [Wayback Machine](https://web.archive.org/))  
- 📰 Historical issues of *AFL-CIO News* available at the [Internet Archive AFL-CIO News collection](https://archive.org/search?query=creator%3A%22AFL-CIO%22+%22news%22)  
- 🗳️ [Clerk of the House](https://clerk.house.gov)  
- 📊 [VoteView](https://voteview.com)  

---

## Coverage

| Period | Congresses | Files | Votes |
|---|---|---|---|
| 1980–1989 | H096–H101 | 10 | 157 |
| 1990–1999 | H101–H106 | 10 | 107 |
| 2000–2009 | H106–H111 | 10 | 140 |
| 2010–2019 | H111–H116 | 10 | 178 |
| 2020–2025 | H116–H119 | 6 | 130 |
| **Total** | **H096–H119** | **46** | **712** |

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
