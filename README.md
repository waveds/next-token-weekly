# Next Token Weekly

An 8-week newsletter on **Generative AI and Agentic AI** for data analytics learners. Each week has one issue (about 30 printed pages, with diagrams, real-world case studies, interview questions and a quiz) plus a hands-on industry project you can put on your resume.

## How to read the newsletter

Each issue is a single HTML file. Open it in any browser.

- **On your computer:** download the repo (green **Code** button → **Download ZIP**), unzip it, and double-click `week-XX-.../NextToken_WeekXX.html`.
- **Online:** open the GitHub Pages link shared by your instructor.

## Issues

| Week | Date | Issue | Project |
|---|---|---|---|
| [01](week-01-foundations/) | 30 Nov 2026 | How machines learned to write | ReviewLens: GenAI feedback analyser |

New issues are added here each week. The full 8-week schedule is in [PROGRAM_PLAN.md](PROGRAM_PLAN.md).

## Repository layout

```
next-token-weekly/
├── README.md                  ← you are here
├── PROGRAM_PLAN.md            ← the 8-week schedule
├── requirements.txt           ← Python packages for all projects
├── .env.example               ← template for your API keys (copy to .env)
├── .gitignore                 ← keeps .env and other private files out of GitHub
└── week-01-foundations/
    ├── NextToken_Week01.html  ← the newsletter issue
    ├── ReviewLens_Week1.ipynb ← the project notebook
    ├── README.md              ← how to run this week's project
    └── data/
        └── sample_reviews.csv ← 120 labelled sample reviews
```

## Setting up the projects (once)

1. Install Python 3.10 or newer, then install the packages:
   ```
   pip install -r requirements.txt
   ```
2. Get an API key. **Either one works:**
   - **Google Gemini (free):** go to [aistudio.google.com](https://aistudio.google.com) → **Get API key**. Needs a Google account, no card.
   - **OpenAI (paid):** [platform.openai.com](https://platform.openai.com/api-keys).
3. Copy `.env.example` to a new file called `.env` in the repo root and paste your key after `GEMINI_API_KEY=` (or `OPENAI_API_KEY=`).
4. Open a notebook with `jupyter notebook` and choose **Run → Run All Cells**.

The notebooks try **OpenAI first, then Gemini, then a simple rule-based fallback**, so they always run, even with no key.

> **Never commit your `.env` file or paste a key into a notebook.** `.env` is already listed in `.gitignore`. If a key is ever pushed by mistake, delete it in the provider's console and create a new one.

## Working on your own copy

Click **Fork** (top right on GitHub) to get your own copy, do the project there, and link your fork on your resume and LinkedIn. Each week's README has a resume bullet template.
