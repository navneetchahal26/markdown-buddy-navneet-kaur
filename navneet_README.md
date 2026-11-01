# Social Media Engagement Analyzer

*Turning synthetic Twitter-style activity logs into audience insight reports — entirely in R.*

---

What does a brand actually learn from 90 days of post data? Likes and retweets tell you what resonated. Posting time and content category tell you what conditions produced that resonance. This project connects those two halves using a reproducible R pipeline that any communications team member — not just a data scientist — can run from a single command.

---

## How to Use This Project

**Step 1 — Clone:**
```bash
git clone https://github.com/yourusername/markdown-buddy-navneet.git
```

**Step 2 — Open:** Double-click `social_engagement.Rproj` in RStudio. This sets the working directory automatically.

**Step 3 — Install dependencies (first run only):**
```r
renv::restore()
```
This project uses `renv` for dependency locking. All packages install at the exact versions tested.

**Step 4 — Run:**
```r
source("pipeline/run_all.R")
```
The full pipeline takes approximately 25 seconds on a standard laptop. Output reports are written to `reports/`.

---

## What's Inside

### The Data

`data/raw/posts_synthetic.csv` — 2,700 posts across 90 days, spanning six content categories (product announcements, community questions, team stories, event promotions, tips & tutorials, and reposts).

Each row represents one published post:

- `post_id` — unique identifier
- `published_at` — timestamp (UTC)
- `content_category` — one of the six categories above
- `platform` — `twitter_style` (all posts use the same synthetic platform)
- `likes`, `shares`, `comments`, `impressions` — numeric engagement counts
- `is_paid` — boolean flag for boosted posts

### The Scripts

```
pipeline/
├── run_all.R              ← single-file runner; calls everything below
├── load_clean.R           ← import, parse timestamps, flag anomalies  
├── compute_engagement.R   ← engagement rate = (likes+shares+comments)/impressions
├── segment_analysis.R     ← group and compare by category, hour, day-of-week
└── generate_report.R      ← renders reports/engagement_report.html via rmarkdown
```

### The Output

Running the pipeline produces:

1. `reports/engagement_report.html` — A self-contained HTML report with all charts
2. `data/processed/segment_summary.csv` — Aggregated stats per content category
3. `data/processed/hourly_means.csv` — Mean engagement rate by hour of day

---

## Selected Findings (Synthetic Data)

> *These figures come from the synthetic dataset and are not representative of any real platform's performance.*

- **Tips & tutorials** posts had the highest organic engagement rate (3.7% mean vs. 1.9% average across categories)
- Posts published **between 11am–1pm and 6pm–8pm** averaged 40% higher impression-to-engagement conversion
- Paid posts (`is_paid = TRUE`) had 3× higher impressions but only 1.3× higher engagement rate, suggesting the audience reached by boosting was less relevant
- Weekend posting volume was 28% lower, but weekend engagement rate was 15% higher per post

---

## Package Versions

Managed via `renv`. Key packages:

| Package | Version | Purpose |
|---------|---------|---------|
| `tidyverse` | 2.0.0 | Data wrangling and ggplot2 |
| `rmarkdown` | 2.25 | Report rendering |
| `lubridate` | 1.9.3 | Timestamp parsing |
| `scales` | 1.3.0 | Axis formatting in charts |
| `renv` | 1.0.3 | Package version locking |

Full lockfile: `renv.lock`

---

## Reproducing on a New Machine

If `renv::restore()` fails (network issues, CRAN mirror changes), install manually:
```r
install.packages(c("tidyverse", "rmarkdown", "lubridate", "scales"))
```
Then set `renv::settings$use.cache(FALSE)` and retry.

---

## Contributing

This is a course project — pull requests are not being accepted. However, you are welcome to fork the repository and adapt the pipeline for your own synthetic datasets under the terms of the MIT License.

---

## AI Assistance Disclosure

**AI tool:** Claude (Anthropic) | 2025

**Three-stage prompting used:**

*Stage 1 (seed):* "Explain what sections a good GitHub README for an R data analysis project should include." The AI listed eight sections including a changelog and citation guide — both removed as inapplicable to this context.

*Stage 2 (refinement):* "Revise the sections list so it's concise and uses Markdown headers and bullet formatting." The formatted list was used as the starting scaffold only; all content was replaced with project-specific information.

*Stage 3 (validation):* "Check the Markdown syntax for correctness and readability." The AI identified one issue: a code fence inside a blockquote that wasn't rendering correctly on GitHub. Rewritten as a regular code fence outside the blockquote.

**What I changed:** Replaced the AI's generic project description with the framing paragraph about connecting post conditions to engagement outcomes. Added the Selected Findings section entirely independently — AI had no information about the synthetic data outputs. Rewrote the "How to Use" section to reflect the `renv` workflow the AI wasn't aware of.

---

*Navneet Kaur | BDA400 Data Science Tools and Techniques*
