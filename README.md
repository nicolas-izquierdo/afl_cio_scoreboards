# AFL-CIO Legislative Scoreboards

<p align="left">
  <em>U.S. House legislative evaluations, 1980–2025</em>
</p>

<p align="left">
  <img src="https://img.shields.io/badge/Coverage-1980--2025-blue">
  <img src="https://img.shields.io/badge/Chamber-House-lightgrey">
  <img src="https://img.shields.io/badge/Status-Active-success">
  <img src="https://img.shields.io/badge/Use-Academic%20%26%20Non--Commercial-orange">
</p>

---

This repository provides AFL-CIO legislative assessments of lawmaking in the U.S. House between 1980 and 2025. It combines historical AFL-CIO scorecards with roll call data to evaluate legislators’ behavior on key labor-related votes.

> **Status:** Current coverage includes the U.S. House (1980–2025). Extension to additional years and the Senate is ongoing.

---

## Overview

- **Unit of analysis:** Roll call vote  
- **Core sources:** AFL-CIO scorecards + Voteview  
- **Output:** Clean vote-level dataset + legislator scores  
- **Applications:** Political economy, legislative behavior, labor politics  

---

## Data construction

The dataset is constructed in three steps:

1. AFL-CIO legislative scorecards are collected and transcribed  
2. Each vote is matched to its corresponding Voteview roll call  
3. Legislators are scored based on AFL-CIO positions  

---

## Sources

Primary materials are drawn from:

- 📄 AFL-CIO publications (current and archived versions via the  
  👉 [Wayback Machine](https://web.archive.org/)  
- 📰 Historical issues of *AFL-CIO News* available at the  
  👉 [Internet Archive AFL-CIO News collection](https://archive.org/search?query=creator%3A%22AFL-CIO%22+%22news%22)

PDF scans are included whenever available.

---

## Data structure

The dataset provides vote-level information linking AFL-CIO scorecards to official House roll calls and Voteview records.

| Variable | Description |
|----------|-------------|
| `congress` | U.S. Congress number |
| `year` | AFL-CIO scorecard year |
| `aflcio_num` | AFL-CIO vote number |
| `rollcall` | Clerk roll call number |
| `date` | Vote date |
| `chamber` | Chamber (House) |
| `bill_type` | Bill type (e.g. H.R., H.J.Res.) |
| `bill_number` | Bill number |
| `bill_id` | Bill identifier |
| `bill_title` | AFL-CIO vote title |
| `question` | Official vote question |
| `amendment_author` | Amendment sponsor |
| `vote_type` | Vote recording type |
| `result` | Vote outcome |
| `result_tally` | Official tally string |
| `vote_desc` | Voteview description |
| `yea_total` | Total yea votes |
| `nay_total` | Total nay votes |
| `nv_total` | Not voting |
| `yea_R`, `nay_R`, `nv_R` | Republican votes |
| `yea_D`, `nay_D`, `nv_D` | Democratic votes |
| `yea_I`, `nay_I`, `nv_I` | Independent votes |
| `aflcio_position` | AFL-CIO position |
| `aflcio_label` | Mapping of Y/N |
| `aflcio_topic` | Topic label |
| `aflcio_description` | Full description |
| `subject_matter` | Voteview classification |
| `congress_url` | Congress.gov link |
| `url` | Voteview URL |

<sub>

**Notes.**  
(i) Variables `aflcio_*` are transcribed from AFL-CIO scorecards.  
(ii) Vote totals are based on official Clerk counts and may include non-voting delegates, generating small discrepancies relative to Voteview aggregates.  
(iii) Party vote counts come from Voteview (`party_vote_counts`; codes: 100 = Democrat, 200 = Republican, others = Independent).  
(iv) AFL-CIO positions are encoded as either *Y=Right; N=Wrong* or *Y=Wrong; N=Right*.

**Key identification distinction.**  
`rollcall` = Clerk numbering (resets yearly).  
`url` suffix = Voteview numbering (sequential by Congress).  
These systems do not coincide.

</sub>

---

## License and use

This repository is intended for **academic and non-commercial use**.

- The **dataset and code** are freely available for research, replication, and teaching.  
- The **AFL-CIO source materials** are included for scholarly use only.

> ⚠️ **Notice on source materials**  
> Some documents originate from AFL-CIO publications. This repository does not claim ownership of those materials.  
> They are reproduced in good faith for non-commercial academic purposes.

If you are a rights holder and would like any material removed, please open an issue.

---
