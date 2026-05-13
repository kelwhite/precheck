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

  Learning Goals

  This project teaches:
  1. Go Basics: packages, functions, error handling
  2. CLI Tools: flags, output formatting, user interaction
  3. Git Operations: running git commands, parsing output
  4. File I/O: reading configs, checking file existence
  5. Testing: writing unit tests for Go code
  6. Best Practices: project structure, documentation

  Development Sections

  Work through these in order:

  Section 1: Setup & Hello World ✓

  - Create repo
  - Initialize Go module
  - Create project structure
  - Write basic main.go

  Section 2: Check GPG Signatures

  - Write pkg/git/signatures.go
  - Integrate into main.go
  - Test with signed/unsigned commits

  Section 3: Check Email Match

  - Write pkg/git/email.go
  - Write pkg/gpg/keys.go
  - Compare commit email with GPG key email

  Section 4: Check Changelog Fragment

  - Write pkg/changelog/fragment.go
  - Detect repo type (kubevirt vs ovirt)
  - Look for changelog in correct location

  Section 5: Validate Commit Messages

  - Check for "WIP" in messages
  - Validate format (conventional commits?)
  - Check for sign-off (DCO)

  Section 6: Polish & Testing

  - Add colors to output (✓ green, ✗ red)
  - Write unit tests
  - Add CLI flags
  - Create installation instructions

  Installation (Future)

  go install github.com/kelwhite/prcheck@latest

  Contributing

  This is a learning project! Contributions welcome.

  License

  MIT

