# AFL-CIO Legislative Scoreboards

<p align="left">
  <em>U.S. House legislative evaluations, 1980–2025</em>
</p>

---

This repository provides AFL-CIO legislative assessments of lawmaking in the U.S. House between 1980 and 2025. It includes information on the bills selected by the AFL-CIO for evaluation, together with code to score legislators’ behavior based on those votes.

> **Status:** Coverage currently spans 1980–2025 (House). Work is ongoing to extend the dataset to additional years and to the U.S. Senate.

---

## Overview

- **Unit of analysis:** Roll call vote  
- **Sources:** AFL-CIO scorecards + Voteview  
- **Output:** Clean vote-level dataset + legislator scoring  
- **Use cases:** Political economy, legislative behavior, labor politics  

---

## Data construction

The dataset was built in three steps:

1. AFL-CIO legislative scoreboards were collected and transcribed  
2. Each bill was matched to its corresponding Voteview roll call  
3. Legislators were evaluated based on AFL-CIO positions  

---

## Sources

The underlying documents come from:

- AFL-CIO website (including archived versions via Wayback Machine)  
- *AFL-CIO News* periodicals (Internet Archive)

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
(ii) Vote totals are based on official Clerk counts and may include non-voting delegates, which can generate small discrepancies relative to Voteview aggregates.  
(iii) Party vote counts are derived from Voteview (`party_vote_counts`; codes: 100 = Democrat, 200 = Republican, others = Independent).  
(iv) AFL-CIO positions are encoded as either *Y=Right; N=Wrong* or *Y=Wrong; N=Right*.

**Key identification distinction.**  
`rollcall` = Clerk numbering (resets yearly).  
`url` suffix = Voteview numbering (sequential by Congress).  
These systems do not coincide.

</sub>

---

## License and use

This repository is intended for **academic and non-commercial use**.

- The **dataset and code** are released for free use, reuse, and replication.  
- The **AFL-CIO source documents** are reproduced here for research and educational purposes only.  

> ⚠️ These materials are derived from AFL-CIO publications. This repository does not claim ownership over those original documents.  
> They are included in good faith under non-commercial, scholarly use.  

If you are a rights holder and would like any material removed, please open an issue.

---
