# Progress Notes: GenAI Adoption vs. GDP Analysis

Running log of decisions and outputs at each stage of the project, following the plan in `project-plan.md`.

---

### Task 1: Data Acquisition & Initial Exploration — ✅ Complete

**Dataset:** 

[Generative AI Adoption vs. GDP per Capita](https://ourworldindata.org/) — Our World in Data (CC BY)

[Microsoft (2026)Eurostat](https://github.com/microsoft/ai-diffusion-report), [OECD, IMF, and World Bank (2026)](https://data.worldbank.org/indicator/NY.GDP.PCAP.PP.KD) Our World in Data – with minor processing by Our World in Data


**AI-reported structure:**
- 444 rows, 6 columns, 148 unique countries
- 3 time points: June 30 2025, Dec 31 2025, March 31 2026
- Missing values: 18 rows missing GDP per capita, 3 rows missing world region
- Columns: `Entity`, `Code`, `Day`, `Estimated share of working-age adults who use generative AI`, `GDP per capita`, `World region according to OWID`

**Flagged limitations:**
- Only 3 time points available — trend claims should be framed as "change between dates," not statistical trend lines
- Each country has 3 rows (one per date) — analysis must account for this to avoid blending dates together

**Human judgment:**
- Confirmed "estimated share of working-age adults who use generative AI" reasonably captures the adoption question I'm asking, with the caveat that it's a modeled estimate, not a direct survey of every individual
- Defined research questions: (1) how has GenAI adoption changed across the 3 available time points, and which countries show the fastest/slowest adoption; (2) does adoption correlate with GDP per capita
- Considered a third angle — comparing adoption data against media/advertising claims of AI usage — but decided to keep scope small and exclude it, since it would require an added research/citation step beyond the dataset itself
- Confirmed adoption % is not the same as sentiment; the dataset measures usage, not opinion or trust, and the write-up will state this explicitly as a boundary rather than treat it as a gap to fix
- Reviewed dataset fit against the finalized research questions and confirmed it's a good match — approved to proceed

---

### Task 2: Data Cleaning & Preparation — ✅ Complete

**AI cleaning steps:**
- Standardized column names for easier use in code (e.g., `Estimated share of working-age adults who use generative AI` → `adoption_pct`, `GDP per capita` → `gdp_per_capita`)
- Identified and removed 1 non-country aggregate row (`World`, code `OWID_WRL`) that would have skewed country-level analysis
- Converted the `date` column to proper datetime format
- Produced two cleaned output files, since different research questions have different data needs:
  - `genai_adoption_clean_full.csv` — 441 rows, 147 countries — all countries, nulls in GDP retained. Use for the adoption-trend/fastest-slowest question, which doesn't depend on GDP.
  - `genai_adoption_clean_gdp.csv` — 423 rows, 141 countries — 18 rows with missing GDP dropped. Use for the GDP correlation question.

**Finalized research questions (refined for clarity and answerability):**
1. What is the correlation between GDP per capita and adoption rate, using March 2026 as a single snapshot?
2. Which countries had a lower adoption rate on March 2026 than on June 2025, and by how much did each decline?
3. Ranking countries by GDP and separately by adoption rate (March 2026), which countries show the largest gap between their two ranks (adoption much higher or lower than GDP would predict)?
4. As of March 2026, what is the median adoption rate across all countries, and how does it compare to the top 10 countries — is there a large gap between typical and top performers?
5. As of March 2026, what is the average adoption rate by world region, and does that regional ranking match or differ from the regional ranking by average GDP per capita?

**Human review:**
- Confirmed the row/country counts look correct after cleaning
- Verified row counts independently via command line (`wc -l genai_adoption_clean_gdp.csv`, subtracting 1 for the header row), since the chat file preview truncates display at 100 rows — confirmed 423 rows in the GDP-complete file
- **Decided to consolidate to a single clean file** (`genai_adoption_clean_full.csv`) rather than maintaining two separate CSVs. This decision came out of finalizing the research questions above: reviewing them together made it clear only questions 1, 3, and 5 require GDP, while questions 2 and 4 don't, so a permanent split wasn't necessary. Dropping GDP-null rows will instead be done inline within the specific notebook cells that need it — keeps the file structure simple and makes the filtering logic visible next to the question it supports

### Task 3: Analysis (Adoption Levels + GDP Correlation) — ✅ Complete

**AI analysis steps:** Wrote and ran code for all 5 finalized research questions, verified results before handing off.

**Findings and human/AI interpretation discussion:**

1. **GDP-adoption correlation: 0.846.** Strong, but not perfect. My original assumption was closer to a one-to-one relationship between GDP and adoption. The data mostly confirms that (most countries follow the wealth-adoption pattern, likely due to infrastructure, knowledge-work jobs, and English-language content availability), but the correlation isn't 1.0 — leaving room for the outliers found in Q3. Considered expected/not surprising on its own, but valuable as the baseline the other findings build on.

2. **Zero countries declined in adoption (June 2025 → March 2026).** Every one of 147 countries grew. Flagged as a real, notable pattern rather than a coincidence — with this many countries, some random decline would be expected by chance alone if growth weren't broadly consistent.

3. **Outliers from the GDP-adoption trend:** Jordan, Lebanon, and Vietnam show adoption far higher than their GDP rank would predict; Guyana and Russia show adoption far lower. Locked in as genuine outliers — specifically, "relationship outliers" (they break the general trend) rather than simple extreme-value outliers. This finding directly challenged my original 1:1 assumption about GDP and adoption. Caveat: with only one snapshot and 5 out of 141 countries showing large gaps, these are flagged as "worth investigating further" rather than explained with confidence — the data shows *that* they deviate, not *why*.

4. **Median adoption (14.8%) vs. top 10 average (49.2%) — 34.4 point gap.** This is the strongest and most direct answer to my original motivating question (is AI adoption really as high as advertising implies). Confirmed my original suspicion, with a nuance: the hype isn't false, it's just describing a small group of leading countries (UAE, Singapore, Norway, etc.) and getting generalized to the whole world, which is misleading for the typical country.

5. **Regional patterns:** Oceania and Europe lead in both adoption and GDP; Africa is lowest in both. Expected given the strength of the Q1 correlation. One nuance: North America and Asia don't rank identically for GDP vs. adoption, showing region alone doesn't perfectly track wealth either.



### Task 4: Visualization — ✅ Complete

**AI chart generation:** Drafted and tested 5 charts covering the strongest findings: GDP vs. adoption scatter (colored by region), the GDP/adoption rank-gap outlier chart, top-10-vs-median bar chart, full 147-country distribution chart, and average adoption by region. Iterated on style based on feedback (e.g., discussed whether to color by individual country vs. region, landed on region-based coloring since it encodes real information rather than adding visual noise).

**Human review and decisions:**
- Decided not to force a chart for every question. Q2 (zero declines) stays as a stated finding in text since a single fact doesn't need a visual; Q3 (outliers) got a chart since the pattern is easier to see than to read as a list.
- Questioned whether the original median-vs-top-10 chart told the full story, which led to adding the full-distribution chart alongside it rather than replacing it, so both the "how far ahead are leaders" and "what does the whole spread look like" angles are covered.
- Approved all 5 final charts for inclusion in the repo.



### Task 5: Writing Interpretations — ✅ Complete

**How this actually happened:** I wrote first-pass interpretations for all 5 findings myself. Claude reviewed them for accuracy (catching one place where I'd implied a statistic that wasn't actually calculated — a "15% of countries" framing that misstated what a correlation coefficient measures), fixed typos, and completed one unfinished thought in the Question 4 write-up based on context from our earlier discussion. I reviewed each revision and approved the final wording, then had Claude remove em dashes throughout to match my preferred style.

**Final responsibility split:**
- **Me:** Wrote the substance and structure of each interpretation, including which findings to emphasize and my own reactions to them (e.g., recognizing that Q3's outliers challenged my original assumption of a near 1:1 GDP-adoption relationship)
- **Claude:** Caught and corrected one accuracy issue (avoiding overstating statistical significance), fixed typos, completed one unfinished sentence, and synthesized the final summary paragraph by pulling together themes across all 5 of my individual write-ups
- **Together:** Reviewed each revision side by side before finalizing wording



### Task 6: README & Dot Plot Picture — ✅ Complete

### Task 7: Publishing to GitHub — ✅ Complete
