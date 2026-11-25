# Week 01 · How machines learned to write

**Phase 1: Begin the journey · Issue 01 · 30 Nov 2026**

## 1. Read the issue

Open [`NextToken_Week01.html`](NextToken_Week01.html) in a browser (download the repo first, because GitHub shows HTML files as code). It has 16 chapters:

AI family tree · Timeline 1950 to now · What an LLM is · Tokens · Embeddings · Attention and the Transformer · How models are trained (RLHF) · Temperature · Hallucination · The model landscape · From chatbot to agent · Six real-world case studies · 20 interview questions · 10-question quiz · The project · Glossary and cheat sheet

## 2. Do the project: ReviewLens

An online electronics retailer gets ~10,000 product reviews a month. Build a pipeline that tells the business **what customers are unhappy about, how urgent it is, and whether it is getting better or worse**.

| Step | What | Concept from the issue |
|---|---|---|
| 1 | Load and clean reviews | pandas |
| 2 | Token audit and cost projection | Ch 4 Tokens |
| 3 | Sentence embeddings and semantic search | Ch 5 Embeddings |
| 4 | Theme discovery (K-means + PCA map) | Ch 5 |
| 5 | LLM labelling in JSON at temperature 0 | Ch 3, 7, 8 |
| 6 | Validation, accuracy, confusion matrix | Ch 9 Hallucination |
| 7 | Insight dashboard | Analytics |
| 8 | Executive memo | GenAI summarisation |

### Run it

From the repo root (after the one-time setup in the main README):

```
cd week-01-foundations
jupyter notebook ReviewLens_Week1.ipynb
```

Then **Run → Run All Cells**. The setup cell prints which model it is using:

- `Provider: OPENAI`: your OpenAI key worked.
- `Provider: GEMINI`: using the free Gemini API (labels 20 reviews per request to stay inside the free limit).
- `Provider: RULES`: no working key; a simple rule-based labeller is used so the notebook still runs. The line above it explains why.

### Data

`data/sample_reviews.csv` has 120 sample reviews with gold labels (`gold_sentiment`, `gold_theme`, `gold_urgency`) so you can measure accuracy immediately.

For your submission, use real reviews (2,000 to 5,000 rows). Put the CSV in `data/` and change `DATA_PATH` in Step 1. It needs a `review` column, plus `date` for the weekly trend chart. Good sources:

- Amazon Reviews 2023 (McAuley Lab, Hugging Face)
- `amazon_polarity` (Hugging Face)
- Flipkart product reviews (Kaggle)
- Yelp Open Dataset

### Troubleshooting

| Message | Fix |
|---|---|
| `429` / `RESOURCE_EXHAUSTED` | Free-tier limit hit. The notebook retries on its own; if it keeps happening add `GEMINI_RPM=5` to `.env`, or set `GEMINI_MODEL=gemini-2.5-flash-lite` |
| `404` model not found | Google renamed the model. Check current names in AI Studio and set `GEMINI_MODEL=` in `.env` |
| `Provider: RULES` with a key set | Make sure the file is named `.env` (not `.env.txt`) and sits in the repo root or this folder |
| Slow Step 3 the first time | The embedding model (~90 MB) downloads once |

## 3. Deliverables

- [ ] Notebook runs top to bottom without errors
- [ ] Token and cost table for 10,000 reviews/month on two models
- [ ] 2D theme map with named clusters
- [ ] Accuracy + confusion matrix vs gold labels, and 3 errors explained
- [ ] 3 charts: theme × sentiment, urgency, weekly negative trend
- [ ] One-page executive memo with 3 recommendations
- [ ] Your fork of this repo with an updated README

## 4. Put it on your resume

Replace the brackets with **your own numbers** from the notebook:

> **ReviewLens: GenAI Customer Feedback Analytics Pipeline** · Python, pandas, Gemini/OpenAI API, sentence-transformers, scikit-learn, tiktoken
> - Built an end-to-end pipeline that classifies product reviews by sentiment, theme and urgency using an LLM with JSON-structured outputs, reaching **[X]%** agreement with human labels on a **[N]**-review test set.
> - Discovered **[K]** complaint themes in **[N]** reviews using sentence embeddings and K-means clustering; **[theme]** drove **[Y]%** of negative feedback.
> - Cut projected labelling cost to **[$Z]** per 10,000 reviews by auditing token usage and batching requests.
