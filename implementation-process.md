# Implementation Process

## Scope and decisions

- Source: `Orchestra-Research/AI-Research-SKILLs`, path `20-ml-paper-writing`.
- Skills in scope: `academic-plotting`, `ml-paper-writing`, `presenting-conference-talks`, and `systems-paper-writing`.
- Local destination: `20-ml-paper-writing/` in this working folder.
- Global Codex installation: intentionally skipped; testing is local.
- GitHub destination: public `christian-hoang-04/ai-research-skills-test`.

## Commands and execution notes

1. `gh auth status; git config --global user.name; git config --global user.email; Get-ChildItem -Force`
   - Result: GitHub CLI is authenticated as `christian-hoang-04`; the working folder contained only `implementation-plan.md`; no Git repository existed.
2. `gh repo view christian-hoang-04/ai-research-skills-test --json nameWithOwner,isPrivate,url`
   - Result: the repository did not exist, so the chosen name was available.
3. `gh api repos/Orchestra-Research/AI-Research-SKILLs/git/trees/main?recursive=1`
   - Result: confirmed the four requested skill directories and their references/templates.
4. `python C:\Users\THINKPAD\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py --repo Orchestra-Research/AI-Research-SKILLs --path 20-ml-paper-writing/academic-plotting 20-ml-paper-writing/ml-paper-writing 20-ml-paper-writing/presenting-conference-talks 20-ml-paper-writing/systems-paper-writing --dest D:\projects\my-chiffon-nguyen\mnemonic\AI-Research-SKILLS\20-ml-paper-writing --method auto`
   - Result: successfully copied all four skills to the explicit local destination. Global Codex installation was not used.
5. PowerShell validation of the four expected directories and their `SKILL.md` frontmatter.
   - Result: 4 skill directories and 73 copied files; validation passed.
6. `git init -b main; git add implementation-plan.md implementation-process.md 20-ml-paper-writing; git commit -m "Set up ML paper writing skills for testing"`
   - Result: initialized the local repository and created root commit `3c65971`.
   - Problem: Git reported normal LF-to-CRLF working-copy warnings on Windows; the commit completed successfully.
7. `gh repo create christian-hoang-04/ai-research-skills-test --public --source . --remote origin --push`
   - Result: created the public repository and pushed `main` to `https://github.com/christian-hoang-04/ai-research-skills-test`.
8. Remote verification with `gh api repos/christian-hoang-04/ai-research-skills-test` and local Git status/log checks.
   - Result: remote is public, uses `main`, contains all four expected `SKILL.md` entrypoints, and matches local `HEAD` at `387ac0a`.
   - Result: working tree is clean.
9. `git add implementation-process.md; git commit -m "Record final repository verification"; git push origin main`
   - Result: recorded the completed verification in commit `a2f8a23` and pushed it to `origin/main`.

## Files changed

- `implementation-plan.md`: updated scope, assumptions, commands, and verification plan.
- `implementation-process.md`: recorded execution notes and results.
- `20-ml-paper-writing/academic-plotting/`: copied skill and references.
- `20-ml-paper-writing/ml-paper-writing/`: copied skill, references, and paper templates.
- `20-ml-paper-writing/presenting-conference-talks/`: copied skill and references.
- `20-ml-paper-writing/systems-paper-writing/`: copied skill, references, and paper templates.
- `.git/`: initialized local Git metadata and configured `origin` for the new public repository.

## Verification results

- Local validation passed: all four scoped skill directories contain `SKILL.md` with frontmatter.
- Local file count: 73 skill files, plus the two requested implementation notes.
- Remote creation and initial push succeeded on `main`.
- Remote tree contains all four expected skill entrypoints.
- Local `HEAD` and `origin/main` both resolve to `387ac0afd0147b3415c129e0f17a0901b90346ad`.
- Working tree is clean.

## Problems, decisions, and follow-ups

- No blocking questions remain.
- Follow-ups will record any limitations of testing skill files without globally installing them.
- Limitation: local validation confirms structure and frontmatter only; it does not activate the skills in the Codex runtime because global installation was intentionally skipped.

## Runtime smoke-test phase

### Test assumptions

- “Actually test” means exercise representative, executable paths described by each skill using synthetic inputs and temporary files outside this repository.
- Tests must not install the skills globally or add generated artifacts to the repository.
- External citation/API checks are read-only and use one known paper identifier.
- Missing optional dependencies are recorded as findings; they are not installed without an explicit request.

### Planned smoke tests

- `academic-plotting`: generate a grouped bar chart as PDF and PNG using the documented Matplotlib/Seaborn workflow.
- `ml-paper-writing`: compile the included NeurIPS template and exercise the documented citation verification endpoints.
- `presenting-conference-talks`: compile a minimal Beamer talk and execute the documented PPTX import path.
- `systems-paper-writing`: compile the included OSDI template and validate its required reference/template links.

### Smoke-test commands and results

10. Markdown-link resolver over all local `.md` files under `20-ml-paper-writing/`.
    - Result: passed; every relative Markdown link resolved to an existing local file or directory.
11. Inline Matplotlib/Seaborn grouped-bar smoke test using the documented three-method/two-benchmark pattern.
    - Result: passed; generated non-empty `fig_smoke.png` (45,078 bytes) and `fig_smoke.pdf` (13,396 bytes) in the temporary test directory.
    - Warning: Seaborn reported that the installed SciPy/NumPy versions are outside its preferred compatibility range; output generation still succeeded.
12. `latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex` against a temporary copy of `ml-paper-writing/templates/neurips2025`.
    - Result: passed with exit code 0; produced a 21,704-byte PDF.
13. `latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex` against a temporary copy of `systems-paper-writing/templates/osdi2026`.
    - Result: passed with exit code 0; produced a 91,417-byte PDF.
    - Warning: the OSDI placeholder template emits expected undefined citation/reference warnings because its example content is intentionally incomplete.
14. `latexmk -pdf -interaction=nonstopmode -halt-on-error slides.tex` on a temporary Beamer talk containing title, problem, summary, and speaker notes.
    - Result: passed with exit code 0; produced a 34,953-byte PDF.
    - Problem: the first attempt used malformed PowerShell here-string syntax and did not execute the test. The command was corrected and rerun successfully; no repository files were affected.
15. Isolated temporary virtual environment smoke test with `python-pptx`, `semanticscholar`, `arxiv`, `habanero`, and `requests`.
    - Result: `python-pptx` created a 28,104-byte PPTX; arXiv lookup succeeded; Semantic Scholar lookup succeeded with `ARXIV:1706.03762`.
    - Result: DOI-to-BibTeX via `requests` and `doi.org` returned HTTP 200 with BibTeX.
    - Finding: the documented Semantic Scholar `DOI:10.48550/arXiv.1706.03762` form returned not-found, while the equivalent `ARXIV:1706.03762` form passed.
    - Finding: Habanero `Crossref().works(ids=..., select='title,DOI')` returned HTTP 400 in the installed client; the same lookup without `select` passed.
16. `python -c "from google import genai; ..."` and environment-presence check.
    - Result: Google GenAI import passed. `GEMINI_API_KEY` is absent, so the paid/credentialed Gemini image-generation path was not invoked.

### Test cleanup and final state

- All generated test artifacts and the temporary virtual environment were outside the repository. The explicit recursive cleanup command was rejected by the shell safety policy, so the temporary directory remains at `%TEMP%\ai-research-skills-smoke-20261004-1`; it is not part of the Git repository and can be removed separately.
- No skill files or generated outputs were added to the working tree by the smoke tests.
- The PPTX and citation dependency tests used an isolated virtual environment; the global Python environment was not modified.
- Cleanup attempt used an explicit temporary-directory target and was rejected by the shell safety policy; no project files or source skill files were touched by cleanup.
