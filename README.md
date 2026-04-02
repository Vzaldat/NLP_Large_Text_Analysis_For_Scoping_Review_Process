# comp530-group-project

## PRISMA-ScR Automated Research Pipeline

This project provides an integrated, automated pipeline for conducting scoping reviews using the PRISMA-ScR methodology. The pipeline retrieves, screens, ranks, and summarizes research papers from multiple open-access databases, leveraging both traditional NLP models and state-of-the-art large language models (LLMs).

<img width="1082" height="442" alt="image" src="https://github.com/user-attachments/assets/0b27a094-9ca4-4b76-b672-c0b9e6024e6a" />

## Features
 **Automated Literature Search:** Searches Europe PMC, DOAJ, and Semantic Scholar for open-access research papers based on user-supplied keywords or research questions.
 **PDF Download:** Downloads available open-access PDFs for all retrieved papers.
 **Abstract Screening & Ranking:** Uses BM25, SBERT, SPLADE, and ensemble LLMs (Gemini, Mistral) to rank abstracts for relevance.
 **Ensemble Summarization:** Generates summaries of top-ranked papers using both Gemini and Mistral LLMs, and synthesizes a final ensemble summary.
 **Evaluation:** Optionally evaluates summaries using BERTScore against a reference summary.
 **Reproducible & Modular:** All steps are contained in a single notebook for easy modification and reproducibility.



## Requirements
 Python 3.8+
 Jupyter Notebook or Google Colab
 The following Python packages (install via pip if running locally):
  - `python-dotenv`
  - `requests`
  - `concurrent.futures` (standard library)
  - `beautifulsoup4`
  - `bert-score`
  - `mistralai`
  - `rank_bm25`
  - `sentence-transformers`
  - `transformers`
  - `torch`
  - `scikit-learn`

> **Tip:** The notebook will attempt to install missing packages automatically if run in Colab.


## Setup
1. **Clone or Download the Repository**
2. **API Keys:**
   - Obtain API keys for Gemini and Mistral LLMs.
   - Create a `.env` file (e.g., `Semantic_key.env`) in your working directory with the following format:
     ```
     GEMINI_API_KEY=your_gemini_api_key_here
     MISTRAL_API_KEY=your_mistral_api_key_here
     ```
   - If using Semantic Scholar API, add:
     ```
     API_KEY=your_semantic_scholar_api_key_here
     ```
3. **Open `IntegratedPipeline.ipynb` in Jupyter or Colab.**
4. **Upload your `.env` file** when prompted (if running in Colab).



## Usage
1. **Run all cells in `IntegratedPipeline.ipynb`.**
2. **When prompted, enter your research question or keywords.**
3. The pipeline will:
    Search databases and download papers
    Screen and rank abstracts
    Generate and display ensemble summaries
    Optionally evaluate summaries if a reference is provided
4. **Results** (rankings, summaries) are saved in the `results/` directory.



## Output
 **Ranked Abstracts:** JSON file with ranked papers and relevance scores
 **Summaries:** Model-specific and ensemble summaries for top papers
 **BERTScore Evaluation:** (Optional) Precision, recall, and F1 for summaries



## Notes
 The pipeline is designed for open-access literature and may not retrieve paywalled content.
 LLM API usage may incur costs and is subject to rate limits.
 For best results, use in Google Colab with GPU enabled.
