# Contribution Guide

First of all, thank you for your interest in contributing! Please be nice and respect the maintainers' time. ❤️

> [!NOTE]
> Please read this whole thing. Most of this applies to any repo on GitHub. 🙏

## Types of Contributions

Code is not the only thing you can contribute. I truly appreciate contributions in the form of:

- Fixing typos.
- Improving docs.
- Triaging [issues](https://github.com/search?o=desc&q=user:claylo+user:lovelesslabs+user:madskilling+is:issue+is:open&s=updated&type=Issues).
- Reviewing [pull requests](https://github.com/search?o=desc&q=user:claylo+user:lovelesslabs+user:madskilling+is:pr+is:open&s=updated&type=Issues).
- Sharing your opinion on issues.

## Development Setup

Contributing code? Cool. At minimum, you'll need the following setup and working on your end:

- [cocogitto](https://docs.cocogitto.io/) (conventional commit checker, version bumper, hook manager)
- [just](https://just.systems/) (task runner, `make` for busy people)

### Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/YOUR_USERNAME/PROJECT_NAME.git`
3. Create a branch: `git checkout -b my-feature`
4. Install git commit hooks: `just install-hooks`
4. Make your changes
5. Run checks: `just check`
6. Commit using [Conventional Commits](https://www.conventionalcommits.org/) (using [cog commit](https://docs.cocogitto.io/guide/commit.html) if you like)
7. Push and open a Pull Request

> [!NOTE]
> Also check for a `CONTRIBUTING.md` in the repository's `docs/` directory that may contain project-specific instructions.

### Rust Project Details

<details open>

#### Additional requirements

- [cargo-nextest](https://nexte.st/) (test runner)
- [taplo-cli](https://taplo.tamasfe.dev/cli/introduction.html) (TOML toolkit)

#### Building

```bash
cargo build
```

#### Running Tests

```bash
just test        # Run tests with nextest
just doc-test    # Run documentation tests
just check       # Run fmt, clippy, and all tests
```

#### Code Style

- Run `just fmt` before committing
- Run `just clippy` to check for lints
- Follow existing code patterns and conventions
- Add tests for new functionality

#### Rust toolchain pinning + MSRV policy

This repo uses **two different version concepts on purpose**:

* **Pinned dev/CI toolchain:** `rust-toolchain.toml` defines the exact Rust toolchain we use for development and CI lint/format. This keeps `rustfmt`, `clippy`, and especially `cargo clippy --fix` output **stable and reproducible** across machines.
* **MSRV (Minimum Supported Rust Version):** `Cargo.toml` sets `[package].rust-version` to the **minimum** Rust version supported for building the crate.

These can differ (e.g. `rust-toolchain.toml = 1.92.0`, `Cargo.toml rust-version = 1.88.0`). The pin is about **consistent tooling**; MSRV is about **downstream compatibility**.

</details>

## Issues

- Before opening a new issue, look for existing issues (even closed ones).
- [Don't needlessly bump issues.](https://sindresorhus.com/blog/issue-bumping)
- If you're reporting a bug, include as much information as possible. Ideally, include a test case that reproduces the bug. Even better, submit a pull request with a failing test.

## Pull requests

### Prerequisites

- If the changes are large or breaking, open an issue discussing it first.
- Don't open a pull request if you don't plan to see it through. Maintainers waste a lot of time giving feedback on pull requests that eventually go stale.
- Don't do unrelated changes.
- Adhere to the existing code style.
- If relevant, add tests, check for typos, and add docs and types.
- Don't add editor-specific metafiles. Those should be added to your own [global gitignore](https://gist.github.com/subfuzion/db7f57fff2fb6998a16c).
- Don't be sloppy. I expect you to do your best.
- Squash your local commits into one commit before submitting the pull request, unless you have important atomic commits.
- Double-check your contribution by going over the diff of your changes before submitting a pull request. It's a good way to catch bugs/typos and find ways to improve the code.
- Do the pull request from a new branch in your fork. Never the default branch (`main`/`master`).

### Submissions

- Give the pull request a clear title and description. It's up to you to convince the maintainers why your changes should be merged.
- If the pull request fixes an issue, reference it in the pull request description using the syntax `Fixes #123`.
- Make sure the “Allow edits from maintainers” checkbox is checked. That way I can make certain minor changes myself, allowing your pull request to be merged sooner.

### Reviews

- Push new commits when **doing changes to** the pull request. Don't squash as it makes it hard to see what changed since the last review. I will squash when merging.
- It's better to present solutions than asking questions.
- Review the pull request diff after each new commit. It's better that you catch mistakes early than the maintainers pointing it out and having to go back and forth.
- Be patient. Maintainers often have a lot of pull requests to review. Feel free to bump the pull request if you haven't received a reply in a couple of weeks.
- And most importantly, have fun! 👌🎉

### Code of Conduct

Please be respectful and constructive in all interactions. For details, see [the policy.](CODE_OF_CONDUCT.md)

*Thanks to @sindresorhus for his [contributing guide](https://github.com/sindresorhus/.github/blob/main/contributing.md).*
