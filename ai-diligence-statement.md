# AI Diligence Statement

**AI system used:** Claude (Anthropic), chosen because it is the AI system used throughout Anthropic's AI Fluency course, for which this project was built.

**How AI contributed:** Claude assisted substantially throughout this project, including: writing and testing the data cleaning code; writing and verifying the analysis code for all five research questions; generating and iterating on chart designs, including the infographic; drafting first-pass written explanations for each finding, which I then revised into my own words; and drafting the structure of this README and the project planning documents.

**Specific instances where I depended on and incorporated Claude's output:**
- Cleaning code that removed a non-country "World" aggregate row and standardized column names
- Analysis code for all five research questions (GDP-adoption correlation, year-over-year change, GDP/adoption rank-gap outliers, median-vs-top-10 comparison, and regional breakdown)
- All chart-generation code, including the region-colored scatter plot, the outlier bar chart, the distribution chart, and the final infographic layout
- First-draft explanations under each chart, which Claude wrote based on the verified results, and which I then reviewed, corrected, and rewrote in my own voice
- Structural drafts of this README, the `project-plan.md`, and the `progress-notes.md` files

**Review process:** I directed each research question and reviewed the cleaned dataset before analysis began. I independently verified the row count of the cleaned dataset using a separate command-line method (`wc -l`) rather than relying only on Claude's reported figures. I questioned findings I didn't immediately understand, for example asking for the median-vs-top-10 chart to be expanded into a full distribution chart once I realized it didn't tell the complete story, and asking for the "rank gap" methodology in the outlier analysis to be explained before accepting it. I ran the complete analysis notebook myself in VSCode and confirmed it executed without errors. I reviewed every written interpretation for completeness after revisions, to confirm no findings or statistics were dropped, and rewrote each explanation in my own words rather than using Claude's drafts as-is.

I did not independently recalculate every statistic through a second method, and I did not audit Our World in Data's own methodology for estimating adoption rates. I note this limitation in the interest of transparency, rather than presenting my review as exhaustive.

**Assertion of responsibility:** While AI assistance was substantial throughout this project, from cleaning code to chart generation to first-draft writing, I directed the research questions, reviewed every output, and made the final judgment calls on what was accurate and worth including. I take full responsibility for the accuracy, presentation, and conclusions of the final product.

**Context-specific considerations:** This project was completed as part of Anthropic's AI Fluency course and is shared publicly on my GitHub as a portfolio piece for job applications in analytics and software engineering. Given this context, I aimed for a level of rigor appropriate to a self-directed learning project and public portfolio piece, not a peer-reviewed research publication. The findings should be read as an exploratory analysis of one dataset over a limited time window (three snapshots between June 2025 and March 2026), not as a definitive claim about global AI adoption.
