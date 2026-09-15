# DAQO China Strategic Exposure Intelligence — V10 Compatible

This NLP application is designed to consume the Excel exports produced by the simplified DAQO Congressional RAG V10 workflow.

## Data input

The app supports either:

- the packaged V10 exports in `data/` (`114.xlsx` to `119.xlsx`), or
- **one or many newly uploaded V10 RAG Excel exports**.

Each workbook must contain at least:

- `All Results`
- `Evidence`

The standard V10 export also contains:

- `Relevant`
- `Not Relevant`
- `Failed Analysis`
- `Methodology`

## Main workflow

1. Load the packaged V10 exports or upload one or more V10 RAG exports.
2. Validate the workbook structure.
3. Merge actions and evidence.
4. Filter by Congress and Country.
5. Run evidence-first NLP.
6. Explore trends, themes, evidence phrases, and Congressional evidence.
7. Optionally generate an OpenAI Evidence Brief.
8. Export the merged NLP intelligence workbook.

## NLP focus

The NLP layer primarily analyzes **Evidence Quote** and **Why It Matters** text.

The application:

- accepts any number of V10 exports and merges them automatically;
- consolidates duplicate actions and duplicate evidence extracts;
- keeps failed analysis separate from Not Relevant;
- applies Congress and Country filtering;
- focuses NLP analysis on evidence rather than unsupported inference.

## Intelligence and visual analysis

The dashboard includes:

- China exclusion pressure by Congress
- risk/opportunity comparison by country
- restrictive-China policy mechanisms
- policy mechanism heatmap
- TF-IDF evidence language landscape
- exclusion signal distribution
- evidence explorer
- evidence-backed intelligence table
- Excel export

## OpenAI Evidence Brief

The application can optionally generate an OpenAI Evidence Brief using the filtered Congressional evidence.

For local use, create `.env` from `.env.example`:

```text
OPENAI_API_KEY=your_key_here
```

For Streamlit Cloud, add `OPENAI_API_KEY` under the application's **Secrets** settings.

Never commit your API key to GitHub.

## Run locally

Install the dependencies:

```powershell
pip install -r requirements.txt
```

Start the Streamlit application:

```powershell
streamlit run app.py
```

## Data security

`.env` is ignored by Git and must never be committed.

The application is designed so credentials remain outside the repository.