# Implementation Plan

## Understanding

The request is to set up the skills from the referenced public GitHub repository/category for testing with the user's setup, and to create a GitHub repository for that test project. The referenced path is `Orchestra-Research/AI-Research-SKILLs/tree/main/20-ml-paper-writing`; it contains four skill directories: `academic-plotting`, `ml-paper-writing`, `presenting-conference-talks`, and `systems-paper-writing`.

The current working folder is `D:\projects\my-chiffon-nguyen\mnemonic\AI-Research-SKILLS`. It currently contains only this planning note and is not a Git repository. The skills will be copied into this repository under `20-ml-paper-writing/`; they will not be installed into the global Codex skills directory. The public GitHub test repository will be `christian-hoang-04/ai-research-skills-test`.

## Success criteria

- The exact skill scope and local test destination are clearly identified before implementation begins.
- The local test project is initialized without touching unrelated files.
- The requested GitHub repository is created with the intended owner, name, visibility, and contents.
- Only files and behavior necessary for that requested change are modified.
- `implementation-plan.md` remains the planning record.
- `implementation-process.md` records execution commands, changed files, verification results, problems, decisions, and follow-ups after implementation starts.
- Verification is performed and reported for the requested change.

## Assumptions

- The current working folder is the intended local test project folder.
- The two documentation files requested in the prompt are permitted changes.
- The linked category's four child directories are the intended skill set.
- “Test without installing” means validate the skill files in this repository without copying them into the global Codex skills directory.
- The authenticated GitHub account `christian-hoang-04` is the intended owner.
- The repository name `ai-research-skills-test` and public visibility are acceptable because the user delegated the choice.

## Blocking questions

None. The user confirmed the four skills under `20-ml-paper-writing`, requested local testing without global installation, delegated the repository name, and selected public visibility.

## Intended files or commands

Implementation files and commands:

- Create/update: `implementation-process.md`.
- Copy the four source skill directories into `20-ml-paper-writing/` using the reviewed skill-installer helper with an explicit local destination.
- Validate that each skill has `SKILL.md` and that referenced files are present.
- Initialize Git, commit the scoped files, create the public GitHub repository, add `origin`, and push the commit.

After the requested change is clarified, I will update this plan if needed, create or update `implementation-process.md`, modify only the necessary project files, and run focused verification commands.

## Verification approach

- Confirm the working-tree/project state and GitHub authentication before implementation.
- Confirm the selected source skill paths and destination layout.
- Verify the requested behavior or artifact with the narrowest relevant checks available in the project.
- Verify no global Codex skill directories were modified.
- Review the final file list/diff and remote repository state to ensure no unrelated changes were made.
- Record commands, results, problems, decisions, and follow-ups in `implementation-process.md`.

## Follow-up test plan

The follow-up request is to actually test the four local skills. No blocking questions remain. I assume “test” means representative smoke tests of the executable workflows and included templates, using synthetic inputs and temporary files outside the repository. Credentialed or paid services will not be invoked without configured credentials; missing dependencies will be tested in an isolated temporary environment rather than installed globally.

- Academic plotting: generate a grouped chart in PDF and PNG.
- ML paper writing: compile the included NeurIPS template and exercise citation lookup/BibTeX paths.
- Conference talks: compile a minimal Beamer presentation and create a minimal PPTX.
- Systems paper writing: compile the included OSDI template and validate local references.
- Record all results, warnings, limitations, and cleanup status in `implementation-process.md`.
