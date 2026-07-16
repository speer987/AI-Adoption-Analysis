# GenAI Adoption vs. GDP: Is the Hype Real?

## Why I built this

*(Write here: your own motivation for this project. E.g., why the "is AI adoption really as widespread as advertising suggests" question caught your interest, and what you were hoping to find out.)*

## Diligence Statement
Creation Diligence:

    Which AI systems did you choose to work with and why?
    What data or information did you share with the AI?
    Were there any privacy, security, or ethical considerations in your choices?

Transparency Diligence:

    Who is the audience for your project output?
    What expectations might they have regarding AI disclosure?
    How specifically did AI contribute to different aspects of your work?

Deployment Diligence:

    What steps did you take to verify the accuracy and appropriateness of AI contributions?
    How did you ensure the final output meets your standards and requirements?
    What responsibility are you taking for the final product?

## The question

Is real-world Generative AI adoption really as widespread as advertising and media coverage suggest, and how does it relate to a country's GDP per capita?

## Data source

[Our World in Data: Generative AI vs. GDP per Capita](https://ourworldindata.org/) — CC BY license. Covers 147 countries across 3 time points (June 2025, December 2025, March 2026).

## Key findings

**1. GDP and adoption are strongly linked, but not perfectly (0.846 correlation).**
![GDP vs adoption by region](charts/q1_gdp_vs_adoption_by_region.png)

**2. Every single country grew. Not one declined.**
Between June 2025 and March 2026, all 147 countries analyzed increased their adoption rate — even the slowest (Ukraine) still grew by 0.3 percentage points.

**3. A handful of countries break the GDP-adoption pattern entirely.**
![GDP/adoption outliers](charts/q3_gdp_adoption_outliers.png)

**4. The "hype" reflects a small group of leaders, not the typical country.**
![Top 10 vs median](charts/q4_median_vs_top10.png)
![Full distribution](charts/q4_full_distribution.png)

**5. Regional patterns mostly track GDP, with a couple of exceptions.**
![Regional adoption](charts/q5_regional_adoption.png)

## Full analysis

See [`analysis.ipynb`](analysis.ipynb) for the complete code, charts, and write-up for each finding.

## Project plan & human-AI collaboration

This project was completed as part of Anthropic's AI Fluency course on Skilljar. See [`project-plan.md`](project-plan.md) for the full task-by-task breakdown of how work was divided between my judgment and Claude's assistance, and [`progress-notes.md`](progress-notes.md) for a running log of how each task actually went.

## Repo structure

```
├── README.md
├── analysis.ipynb
├── project-plan.md
├── progress-notes.md
├── data/
│   └── genai_adoption_clean_full.csv
└── charts/
    ├── infographic.png
    ├── q1_gdp_vs_adoption_by_region.png
    ├── q3_gdp_adoption_outliers.png
    ├── q4_median_vs_top10.png
    ├── q4_full_distribution.png
    └── q5_regional_adoption.png
```
