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

## Files changed

Files and directories will be listed here after the local setup completes.

## Verification results

Verification results will be recorded here after copying, local validation, commit, and remote push.

## Problems, decisions, and follow-ups

- No blocking questions remain.
- Follow-ups will record any limitations of testing skill files without globally installing them.
