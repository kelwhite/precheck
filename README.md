# prcheck - PR Readiness Checker

  A CLI tool to validate your pull requests before pushing, ensuring they meet project requirements.

  ## What Problem Does This Solve?

  Manual PR preparation is error-prone. We often forget to:
  - Sign commits with GPG
  - Add changelog fragments
  - Use the correct email
  - Follow commit message conventions

  `prcheck` automates these checks so you catch issues **before** pushing.

  ## Features Roadmap

  ### Phase 1: Core Checks (MVP)
  - [ ] **Check 1: GPG Signatures** - Verify all commits are signed
  - [ ] **Check 2: Email Validation** - Ensure commit email matches GPG key
  - [ ] **Check 3: Changelog Fragment** - Check if changelog fragment exists
  - [ ] **Check 4: Commit Messages** - Validate commit message format (no WIP, proper format)

  ### Phase 2: Auto-Fix
  - [ ] Add `--fix` flag to auto-create missing changelog fragments
  - [ ] Suggest fixes for common issues

  ### Phase 3: Repo-Specific Rules
  - [ ] Support per-repo config files (.prcheck.yaml)
  - [ ] KubeVirt-specific checks (AI disclosure trailers)
  - [ ] oVirt-specific checks

  ### Phase 4: GitHub Integration
  - [ ] Check CI status
  - [ ] Check required reviewers
  - [ ] Validate PR description

  ## Project Structure
  prcheck/
  ├── main.go                  # Entry point - orchestrates all checks
  ├── go.mod                   # Go module dependencies
  ├── cmd/                     # Command implementations
  │   └── check.go            # Main check command
  ├── pkg/                     # Reusable packages
  │   ├── git/                # Git operations
  │   │   ├── signatures.go   # GPG signature checking
  │   │   ├── email.go        # Email validation
  │   │   └── log.go          # Git log parsing
  │   ├── changelog/          # Changelog validation
  │   │   └── fragment.go     # Check for changelog fragments
  │   └── gpg/                # GPG operations
  │       └── keys.go         # GPG key operations
  └── README.md               # This file

  ## Usage (Future)

  ```bash
  # Check current branch
  prcheck

  # Auto-fix issues
  prcheck --fix

  # Verbose output
  prcheck --verbose
  ```

  License
  MIT
