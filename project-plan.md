# Project Plan: GenAI Adoption vs. GDP Analysis

**Goal:** Determine whether real-world GenAI adoption matches the level implied by media/advertising, and whether adoption correlates with GDP.

**Info:** This project was completed as part of Anthropic's AI Fluency course on Skilljar. The plan below reflects how work was divided between myself and Claude throughout the project. This markdown file was drafted after conversing with Claude and specifying goals and what success looks like for this project.

**Dataset Attribution:** [Our World in Data — Generative AI vs. GDP per Capita](https://ourworldindata.org/) (CC BY)
---

## Task 1: Data Acquisition & Initial Exploration

**Skills/knowledge needed:** Evaluating whether a dataset's structure (columns, time range, granularity) can actually answer the research question; basic data literacy to spot issues early.

| Human Responsibilities | AI Responsibilities |
|---|---|
| Judge whether the data *means* what I think it means — e.g., recognizing that adoption % isn't the same as sentiment | Report row count, column types, missing values, and date range once a dataset is chosen |
| Reject datasets that look technically fine but don't match my actual research question | Flag structural issues early (e.g., "only 3 time points available") |
| Decide, together with AI, whether the dataset is a good fit before committing | Answer follow-up questions about the dataset's structure quickly |

**Best collaboration point:** Talking through whether a dataset fits the question *before* committing — this caught a mismatch (adoption ≠ sentiment) before any analysis was built on it.

---

## Task 2: Data Cleaning & Preparation

**Skills/knowledge needed:** Understanding common data issues (missing values, regional aggregates mixed into country-level rows, formatting inconsistencies).

| Human Responsibilities | AI Responsibilities |
|---|---|
| Sanity-check the cleaned output — does the row count look right, are real countries still present | Write the cleaning code — filter rows, handle nulls, standardize columns |
| Flag anything that looks wrong before analysis begins | Identify and remove non-country rows (e.g., "World," "Europe" aggregates) |

**Best collaboration point:** Reviewing the cleaned output together before analysis begins, so errors don't propagate downstream.

---

## Task 3: Analysis (Adoption Levels + GDP Correlation)

**Skills/knowledge needed:** Basic statistical reasoning (correlation vs. causation, what a small sample of time points can and can't support).

| Human Responsibilities | AI Responsibilities |
|---|---|
| Decide which results are actually meaningful versus noise | Write the analysis code — averages, spread, correlation, change over available dates |
| Judge whether a finding confirms or challenges my original assumption | Check whether a pattern is statistically meaningful given the limited data (only 3 time points) |

**Best collaboration point:** Interpreting results together — flagging what's surprising or expected, and checking whether it's a real pattern or likely coincidence.

---

## Task 4: Visualization

**Skills/knowledge needed:** Knowing which chart type best represents a given finding (bar for comparison, scatter for correlation, etc.).

| Human Responsibilities | AI Responsibilities |
|---|---|
| Select which charts actually belong in the final repo | Generate chart code quickly |
| Judge whether a chart clearly communicates the finding | Iterate on formatting/style based on feedback |

**Best collaboration point:** Iterating on a chart together until it clearly communicates the finding, not just displays the data.

---

## Task 5: Writing Interpretations

**Skills/knowledge needed:** Translating a statistical result into a plain-language takeaway without overstating what the data shows.

| Human Responsibilities | AI Responsibilities |
|---|---|
| Write the final explanation in my own voice | Draft a first-pass explanation to react to and revise |
| Ensure the takeaway is honest about limitations (e.g., "change" not "trend," given only 3 data points) | Suggest phrasing that avoids overstating statistical significance |

**Best collaboration point:** AI drafts, I correct tone/accuracy/emphasis — ensures the takeaway reflects my actual judgment, not a generic summary.

---

## Task 6: README & Infographic

**Skills/knowledge needed:** Structuring a repo so a stranger can understand the project in under a minute.

| Human Responsibilities | AI Responsibilities |
|---|---|
| Write the project's motivation/framing — why I cared about this question | Draft README structure/sections |
| Decide what stays, what's cut, and the final tone | Help design a simple infographic layout |

**Best collaboration point:** AI proposes structure, I decide what stays, what's cut, and what the framing/tone should be.

---

## Task 7: Publishing to GitHub

**Skills/knowledge needed:** Basic git/GitHub workflow (repo creation, commit, push).

| Human Responsibilities | AI Responsibilities |
|---|---|
| Create the repo and execute the publish — this has to happen under my own account | Provide command guidance and troubleshoot errors |
| Run the actual git commands | Write a `.gitignore` if needed |

**Best collaboration point:** Real-time troubleshooting if a git command fails or behaves unexpectedly.
