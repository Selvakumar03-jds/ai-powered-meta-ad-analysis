# AI-Powered Meta Ad Creative Analysis & Ranking

An automated marketing analytics workflow built with **n8n, Apify, Google Gemini, and JavaScript** to analyse Meta Ad Library creatives for MySivi's Spoken English App.

## Project Overview

Manually collecting and comparing multilingual advertisements can be time-consuming. This project automates the collection and analysis process, evaluates advertising creatives against predefined criteria, and ranks unique text creatives using a weighted scoring framework.

## Workflow Architecture

1. **Manual Trigger** — starts the workflow on demand.
2. **Get Dataset Items** — retrieves advertisement records collected by Apify.
3. **Clean Data** — prepares relevant advertisement fields for analysis.
4. **Basic LLM Chain + Google Gemini** — analyses the creative messaging and assigns scores against five criteria.
5. **Parse AI Analysis** — parses the model response, validates scores, and restores original source fields.
6. **Creative Score Calculator** — calculates a weighted score out of 100.
7. **Rank Ads and Identify the Winner** — handles duplicate text creatives and ranks the unique creatives.
8. **Final Report Formatter** — prepares the final structured output.

## Technology Stack

- n8n — workflow orchestration
- Apify — advertisement data collection
- Google Gemini — AI-assisted creative analysis
- JavaScript — data cleaning, parsing, scoring, deduplication, and ranking
- Meta Ad Library — source of publicly available advertisement information

## Evaluation Methodology

Each creative is evaluated on a scale of 1–10 across five criteria:

| Criterion | Weight |
|---|---:|
| Hook strength | 25% |
| Pain-point relevance | 20% |
| Value proposition | 20% |
| CTA clarity | 15% |
| Differentiation | 20% |

**Weighted score:**

`(Hook × 2.5) + (Pain Point × 2) + (Value Proposition × 2) + (CTA × 1.5) + (Differentiation × 2)`

Maximum score: 100.

## Results

- Advertisement records processed: 10
- Unique text creatives after duplicate handling: 3
- Highest-ranked creative score: 80.5/100
- CTA in the highest-ranked creative: Install now

The score represents AI-assessed creative quality under the defined evaluation framework. It is not a measure of actual campaign performance.

## Limitations

- The analysis uses a limited sample of 10 advertisement records.
- AI-generated scores are evaluative estimates and may vary with the model or prompt.
- Actual campaign metrics such as impressions, clicks, installs, conversions, and ROAS were not available in the collected dataset.
- Therefore, the highest-ranked creative is not necessarily the best-performing advertisement in the real world.
- Duplicate handling is based on normalised headline and body text, not a complete assessment of visual creative similarity.

## Demo

Loom walkthrough: https://www.loom.com/share/517adfc110b54a1dbbdbe3cfb4bbfa15

## Disclaimer

This project was developed as a Growth Intern assignment. It demonstrates a proof of concept for automated creative analysis and ranking. The scoring weights are design choices for this implementation and have not been statistically validated against campaign outcomes.
