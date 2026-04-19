# AFL-CIO Legislative Scoreboards
<p align="left">
  <img src="https://img.shields.io/badge/Coverage-1980--2025-blue">
  <img src="https://img.shields.io/badge/Chamber-House-lightgrey">
  <img src="https://img.shields.io/badge/Votes-712-informational">
  <img src="https://img.shields.io/badge/Status-Active-success">
  <img src="https://img.shields.io/badge/Use-Academic%20%26%20Non--Commercial-orange">
</p>

---

This repository provides AFL-CIO **legislative scoreboards** of lawmaking in the U.S. House between 1980 and 2025. In particular, it provides (1) data on the bills highlighted by the AFL-CIO upon which legislators were assessed as well as (2) R code to score U.S. legislators' behavior on these bills.

> **Status:** Current coverage includes the U.S. House (1980–2025). Extension to additional years and the Senate is ongoing.

---

## Data Construction

The dataset is constructed in three steps:

1. AFL-CIO legislative scorecards are collected and transcribed
2. Each vote is matched to its corresponding VoteView roll call using official Clerk of the House records
3. Roll call metadata (tallies, party breakdowns, bill information) is retrieved from VoteView and verified programmatically across 14 fields per row

All 712 rows have been verified against VoteView roll call data. Verification covers: bill identity, vote date, yea/nay tallies, vote question, vote result, Clerk roll number, congress, and VoteView URL.

---

## Sources

Primary materials are drawn from:

- 📄 AFL-CIO publications (current and archived versions via the  
  👉 [Wayback Machine](https://web.archive.org/))
- 📰 Historical issues of *AFL-CIO News* available at the  
  👉 [Internet Archive AFL-CIO News collection](https://archive.org/search?query=creator%3A%22AFL-CIO%22+%22news%22)
- 🗳️ [Clerk of the House](https://clerk.house.gov) — official roll call records and tallies
- 📊 [VoteView](https://voteview.com) — roll call metadata, party breakdowns, ideological scores

PDF scans of source scorecards are included whenever available.

---

## Repository Structure

```
HOUSE/
├── 1980/aflcio_house_votes_1980.xlsx
├── 1981/aflcio_house_votes_1981.xlsx
│   ...
└── 2025/aflcio_house_votes_2025.xlsx
```

46 Excel files, one per scorecard year, covering the 96th through 119th Congresses (H096–H119).

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

The dataset provides vote-level information linking AFL-CIO scorecards to official House roll calls and VoteView records.

| Variable | Type | Description |
|---|---|---|
| `congress` | integer | U.S. Congress number (e.g. `96` = 96th Congress, 1979–1981). Formula: `floor((year − 1789) / 2) + 1` |
| `year` | integer | AFL-CIO scorecard year. Note: some votes in a scorecard year occurred in the prior calendar year |
| `aflcio_num` | integer | AFL-CIO sequential vote number within the annual scorecard |
| `rollcall` | integer | **Official Clerk of the House roll call number.** Resets to 1 each calendar year. Not the same as the VoteView rollnumber |
| `date` | date | Date the vote was held on the House floor |
| `chamber` | string | Chamber (`"House"` throughout) |
| `bill_type` | string | Official bill type: `H.R.`, `H.J.Res.`, `H.Con.Res.`, `H.Res.`, `S.`, `S.J.Res.`, `S.Con.Res.` |
| `bill_number` | string | Numeric part of the bill number (e.g. `800` for H.R. 800) |
| `bill_id` | string | Concatenation of `bill_type` + `bill_number` (e.g. `H.R.800`) |
| `bill_title` | string | AFL-CIO's descriptive title for this specific vote |
| `question` | string | Official Clerk vote question (e.g. `"On Passage"`, `"On Agreeing to the Amendment"`) |
| `amendment_author` | string | Amendment sponsor, if applicable (e.g. `"King of Iowa Amendment"`) |
| `vote_type` | string | Vote recording method (nearly always `"RECORDED VOTE"`) |
| `result` | string | Vote outcome: `"Passed"`, `"Failed"`, `"Agreed to"`, `"Passed — Veto Overridden"`, `"Failed — Veto Sustained"` |
| `result_tally` | string | Official result string from VoteView (e.g. `"220-208 (Passed)"`). Present for some years only |
| `vote_desc` | string | VoteView short description of the vote. Sparse for older congresses |
| `subject_matter` | string | VoteView subject matter classification (e.g. `"Social Welfare / Domestic Social Policy"`). Sparse |
| `yea_total` | integer | Total Yea votes (Clerk tally — see note on delegates below) |
| `nay_total` | integer | Total Nay votes (Clerk tally) |
| `nv_total` | integer | Total Not Voting / abstentions |
| `yea_R` / `nay_R` / `nv_R` | integer | Republican Yea / Nay / Not Voting |
| `yea_D` / `nay_D` / `nv_D` | integer | Democratic Yea / Nay / Not Voting |
| `yea_I` / `nay_I` / `nv_I` | integer | Independent / third-party Yea / Nay / Not Voting |
| `aflcio_position` | string | AFL-CIO official position on the vote: `Y` or `N`. Interpretation depends on `aflcio_label` |
| `aflcio_label` | string | Decodes the position: `"Y=Right; N=Wrong"` (Yea = pro-labor) or `"Y=Wrong; N=Right"` (Nay = pro-labor) |
| `aflcio_topic` | string | Short topic label as used in the AFL-CIO scorecard |
| `aflcio_description` | string | Full paragraph description transcribed from the AFL-CIO annual scorecard PDF, including policy context, vote outcome, and position rationale |
| `url` | string | Canonical VoteView URL: `https://voteview.com/rollcall/RH[congress 3-digit][rollnumber 4-digit]`. Verified correct for all 712 rows |

<sub>

**Notes.**

(i) Variables prefixed `aflcio_` are transcribed directly from AFL-CIO annual scorecard publications.

(ii) `yea_total`, `nay_total`, and `nv_total` follow official **Clerk of the House** counts, which include votes cast by House non-voting delegates (District of Columbia, Puerto Rico, Guam, U.S. Virgin Islands, American Samoa, Northern Mariana Islands) on amendment votes. VoteView excludes delegate votes. On amendment votes, totals may therefore exceed VoteView aggregates by up to 6.

(iii) Party vote counts (`yea_R`, `yea_D`, etc.) come from VoteView `party_vote_counts` (party codes: 100 = Democrat, 200 = Republican, all others = Independent).

(iv) AFL-CIO positions are encoded as either *Y=Right; N=Wrong* or *Y=Wrong; N=Right* depending on the direction of the pro-labor vote.

</sub>

---

## Key Technical Notes

### Scorecard Year vs. Vote Date

The AFL-CIO assigns votes to scorecards by publication cycle, not strictly by calendar year. Some votes in a given year's scorecard occurred in the prior calendar year — most commonly in the 1980–1989 files, where late-session votes from year *N*−1 appear in the year-*N* scorecard.

### 2025 URLs

VoteView ingests roll calls with a variable lag. The `url` values for 2025 are constructed from confirmed VoteView rollnumbers and are theoretically correct, but a small number may not yet resolve on the VoteView website while ingestion is ongoing.

---

## License and Use

This repository is intended for **academic and non-commercial use**.

- The **dataset and code** are freely available for research, replication, and teaching.
- The **AFL-CIO source materials** are included for scholarly use only.

> ⚠️ **Notice on source materials**
> Some documents originate from AFL-CIO publications. This repository does not claim ownership of those materials. They are reproduced in good faith for non-commercial academic purposes.

