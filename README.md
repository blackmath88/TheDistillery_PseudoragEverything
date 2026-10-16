<!-- BEGIN public-repo-header -->
<div align="center">

# TheDistillery_PseudorigEverything

<a href="https://github.com/blackmath88/TheDistillery_PseudoragEverything"><img alt="Primary language: Python" src="https://img.shields.io/badge/language-Python-526078?style=flat"></a>
<a href="https://github.com/blackmath88/TheDistillery_PseudoragEverything#readme"><img alt="README" src="https://img.shields.io/badge/docs-readme-16796f?style=flat"></a>
<a href="https://github.com/blackmath88/TheDistillery_PseudoragEverything/commits/main"><img alt="Last commit" src="https://img.shields.io/github/last-commit/blackmath88/TheDistillery_PseudoragEverything?style=flat&amp;color=737373"></a>

</div>
<!-- END public-repo-header -->

Local-first distillation pipeline for turning raw notes, transcripts, and PDFs into structured project artifacts.

The repository includes:
- A CLI pipeline runner
- A minimal Flask web app wrapper
- File-based project storage under `projects/`

## Setup

1) Clone the repository

```bash
git clone https://github.com/blackmath88/TheDistillery_PseudorigEverything.git
cd TheDistillery_PseudorigEverything
```

2) (Optional) Create and activate a virtual environment

```bash
python -m venv .venv
# Windows PowerShell
.\.venv\Scripts\Activate.ps1
```

3) Install dependencies

```bash
pip install -r requirements.txt
```

## Run CLI

```bash
python scripts/ingest_project.py --project projects/example_project
```

## Run Web App

```bash
python app.py
```

Then open: `http://127.0.0.1:5000`

## Folder Structure

```text
projects/
	<project_id>/
		raw/                  # source files (.txt, .md, .pdf)
		processed/            # extraction + cleaning outputs
		output/               # final artifacts
		project_context.md    # free-form project context
		use_intent.json       # purpose/audience/output intent
```

## Outputs

Core pipeline outputs:
- `processed/extracted_text.json`
- `processed/cleaned_text.json`
- `output/project.json`
- `output/chunks.jsonl`
- `output/summary.md`

Packaging outputs:
- `output/llm_context_pack.md`
- `output/prompt_starter.md`
- `output/report.html`

## Example Workflow

1) Create or open a project (CLI path or web UI)
2) Add context in `project_context.md` and `use_intent.json`
3) Put source files into `raw/`
4) Run pipeline
5) Review generated files in `processed/` and `output/`

## Notes

- Local-first only (no database, no cloud dependency)
- Flask app is a thin wrapper over the same pipeline logic
