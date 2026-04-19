# AFL-CIO Legislative Scoreboards


## Data structure

The main dataset provides vote-level information on AFL-CIO scorecard votes matched to official House roll calls and Voteview records.

| Variable | Description |
|----------|-------------|
| `congress` | U.S. Congress number |
| `year` | AFL-CIO scorecard year |
| `aflcio_num` | AFL-CIO vote number within scorecard |
| `rollcall` | Official House roll call number (Clerk) |
| `date` | Date of the vote |
| `chamber` | Legislative chamber (House) |
| `bill_type` | Bill type (e.g. H.R., H.J.Res.) |
| `bill_number` | Bill number |
| `bill_id` | Bill identifier (`bill_type` + `bill_number`) |
| `bill_title` | AFL-CIO vote title |
| `question` | Official vote question |
| `amendment_author` | Amendment sponsor (if applicable) |
| `vote_type` | Vote recording method |
| `result` | Outcome of the vote |
| `result_tally` | Official tally string |
| `vote_desc` | Voteview description |
| `yea_total` | Total yea votes |
| `nay_total` | Total nay votes |
| `nv_total` | Not voting / abstentions |
| `yea_R`, `nay_R`, `nv_R` | Republican vote counts |
| `yea_D`, `nay_D`, `nv_D` | Democratic vote counts |
| `yea_I`, `nay_I`, `nv_I` | Independent vote counts |
| `aflcio_position` | AFL-CIO position (Y/N) |
| `aflcio_label` | Mapping of Y/N to pro-labor position |
| `aflcio_topic` | AFL-CIO topic label |
| `aflcio_description` | Full AFL-CIO description |
| `subject_matter` | Voteview classification (if available) |
| `congress_url` | Link to Congress.gov (if available) |
| `url` | Voteview roll call URL |

<sub>

**Notes.**  
(i) Variables `aflcio_*` are transcribed from AFL-CIO legislative scorecards.  
(ii) Vote totals are based on official Clerk counts and may include non-voting delegates, which can generate small discrepancies relative to Voteview aggregates.  
(iii) Party vote counts are derived from Voteview (`party_vote_counts`; codes: 100 = Democrat, 200 = Republican, others = Independent).  
(iv) The AFL-CIO position is encoded using two formats: *Y=Right; N=Wrong* or *Y=Wrong; N=Right*, depending on the vote.

**Key identification distinction.**  
`rollcall` refers to the official Clerk of the House roll call number (resets every calendar year).  
The numeric suffix in `url` corresponds to Voteview’s roll number (sequential within each Congress).  
These are distinct numbering systems and do not coincide.

</sub>
