# 🗺️ EXECUTION PLAN - Step-by-Step Repository Optimization

## 1. Objective
Systematically remove bloat (pycache, large binaries, empty folders, ignored files) from the repository while maintaining functionality and committing after each atomic cleanup phase.

## 2. Strategic Analysis
- **First Principles:** Every change should be atomic and committed separately for clear history and rollback.
- **Approach:** Incremental cleanup starting with the most obvious bloat (`__pycache__`) and moving towards more complex audits (duplicated trees/ignored files).
- **Risks:** Accidentally deleting a binary needed for a demo (e.g., local SQLite DBs). Mitigation: Verify file type and context before deletion.

## 3. Design Specification
- **Step 1: Pycache Cleanup:** `find . -name "__pycache__" -type d -exec rm -rf {} +` followed by `git rm -r --cached .` for any tracked ones.
- **Step 2: Binary Removal:** Target identified `pacman` binary and others >5MB not clearly required for demos.
- **Step 3: Empty Folders:** `find . -type d -empty -delete`.
- **Step 4: Verification:** Execute `unittest` in `AIDA` and `go test` in `Tenkai`.
- **Step 5: Duplicate/Artifact Audit:** Investigate folder structures and common build outputs (e.g., `.egg-info`, `dist/`).
- **Step 6: Git Ignored Cleanup:** `git clean -fdX` (dry-run first) to remove files present in git but ignored.

## 4. Alternatives Considered
- **All-in-one Cleanup:** *Rejected. User explicitly requested step-by-step commits.*
- **Removing Empty Files:** *Skipped per user instruction.*

## 5. Implementation Roadmap
1. [x] **Phase 1: Pycache Cleanup**
   - Identify and remove all `__pycache__` directories.
   - Commit: `chore: cleanup __pycache__ artifacts`
2. [x] **Phase 2: Large Binary Cleanup**
   - Remove `languages/go/pacman/pacman` and `torch_compile_cache`.
   - Commit: `chore: remove large local binaries and torch compile cache`
3. [x] **Phase 3: Empty Folder Cleanup**
   - Remove structurally empty directories.
   - Commit: `chore: remove empty directories`
4. [x] **Phase 4: Verification & Validation**
   - Run tests in `agents/aida/` and `agents/tenkai/`. (Note: AIDA requires local DB setup, Tenkai passed).
5. [x] **Phase 5: Duplicate Tree & Artifact Audit**
   - Search for duplicated folder structures.
   - Identify other build artifacts (e.g., `build/`, `dist/`).
6. [x] **Phase 6: Ignored Files Cleanup**
   - Clean up files present in git but explicitly ignored.
   - Commit: `chore: cleanup git-ignored files`
7. [x] **Phase 7: Final Re-analysis**
   - Run bloat report again for incremental gains.
