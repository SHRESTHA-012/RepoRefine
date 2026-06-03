# Contributing to RepoRefine

Thank you for your interest in contributing to **RepoRefine**! 🎉  
Whether you're fixing a bug, improving the docs, or building a new feature — all contributions are welcome.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Development Workflow](#development-workflow)
- [Making Changes](#making-changes)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Reporting Issues](#reporting-issues)
- [Feature Requests](#feature-requests)
- [Areas to Contribute](#areas-to-contribute)

---

## Code of Conduct

This project follows a simple rule: **be kind and constructive**. Harassment, discrimination, or disrespectful behavior of any kind will not be tolerated. Treat fellow contributors the way you'd want to be treated.

---

## Getting Started

### Prerequisites

- Node.js `>=18`
- npm or yarn
- A GitHub Personal Access Token (PAT) — [generate one here](https://github.com/settings/tokens) with `read:user` scope
- *(Optional)* A [Groq API key](https://console.groq.com/) for AI-powered review summaries

### Local Setup

```bash
# 1. Fork the repository on GitHub, then clone your fork
git clone https://github.com/<your-username>/RepoRefine.git
cd RepoRefine

# 2. Install dependencies
npm install

# 3. Create your environment file
cp .env.example .env.local
# Edit .env.local and add your tokens:
# GITHUB_TOKEN=your_github_pat_here
# GROQ_API_KEY=your_groq_api_key_here   (optional)

# 4. Start the development server
npm run dev
```

The app will be running at `http://localhost:3000`.

---

## Project Structure

```
RepoRefine/
├── app/                  # Next.js App Router pages and layouts
├── components/           # Reusable React components
│   ├── ui/               # Generic UI primitives
│   └── audit/            # Audit-specific components (cards, charts, meters)
├── lib/                  # Core logic
│   ├── github/           # GitHub GraphQL queries and response parsers
│   ├── scoring/          # Deterministic audit and scoring functions
│   └── groq/             # Groq AI integration (optional)
├── public/               # Static assets
└── .env.example          # Environment variable template
```

---

## Development Workflow

1. **Sync your fork** with the upstream `main` branch before starting work.

```bash
git remote add upstream https://github.com/Sushma-1706/RepoRefine.git
git fetch upstream
git checkout main
git merge upstream/main
```

2. **Create a feature branch** with a descriptive name.

```bash
git checkout -b feat/pdf-export
# or
git checkout -b fix/radar-chart-overflow
```

3. Make your changes, then **test locally** before opening a PR.

---

## Making Changes

### Coding Standards

- Use **TypeScript** for all new files where possible.
- Follow the existing code style (Prettier and ESLint configs are included — run `npm run lint` before committing).
- Keep components **small and focused**; split large components into sub-components.
- Avoid hardcoded strings for UI labels — add them to a constants or config file.

### Scoring Logic

RepoRefine's audit scoring is **deterministic by design**. If you're modifying scoring logic:

- Document the rationale for any weight or threshold changes in the PR description.
- Avoid making scores dependent on Groq output — AI summaries are supplementary, not authoritative.
- Add comments explaining what each metric measures.

### GitHub API Usage

- Batch GraphQL queries where possible to minimize rate limit consumption.
- Never expose `GITHUB_TOKEN` or `GROQ_API_KEY` to the client side.
- Handle `403` and rate-limit errors gracefully and surface a user-friendly message.

---

## Commit Guidelines

Use [Conventional Commits](https://www.conventionalcommits.org/) for clear, scannable history:

```
<type>(<scope>): <short description>

Examples:
feat(scoring): add documentation score breakdown
fix(radar): correct axis label overflow on mobile
docs(readme): update rate limit section
refactor(github): simplify GraphQL query builder
chore: upgrade recharts to v2.12
```

**Types:** `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

Keep the subject line under 72 characters. Use the body to explain *why*, not *what*.

---

## Pull Request Process

1. Ensure your branch is up to date with `upstream/main`.
2. Run `npm run lint` and fix any issues.
3. Open a PR against the `main` branch with a clear title and description:
   - **What** changed and **why**
   - Screenshots or screen recordings for UI changes
   - Any related issue numbers (`Closes #42`)
4. A maintainer will review your PR. Please be responsive to feedback — PRs with no activity for 14 days may be closed.
5. Once approved, a maintainer will merge it. Do not merge your own PRs.

---

## Reporting Issues

Before opening an issue, please **search existing issues** to avoid duplicates.

When filing a bug report, include:

- A clear, descriptive title
- Steps to reproduce the issue
- Expected vs actual behavior
- Browser, OS, and Node.js version
- Screenshots or error messages if applicable
- Whether you're using a `GITHUB_TOKEN` (without sharing the token itself)

[Open a bug report →](https://github.com/Sushma-1706/RepoRefine/issues/new?template=bug_report.md)

---

## Feature Requests

Have an idea? Open a **feature request issue** describing:

- The problem you're solving or the use case it addresses
- Your proposed solution (even roughly)
- Any alternatives you've considered

[Open a feature request →](https://github.com/Sushma-1706/RepoRefine/issues/new?template=feature_request.md)

---

## Areas to Contribute

Not sure where to start? Here are some good areas:

| Area | Examples |
|------|---------|
| 🐛 **Bug fixes** | UI glitches, incorrect scoring, broken API error handling |
| 📖 **Documentation** | Improve README, add JSDoc comments, write guides |
| ✨ **New features** | PDF export, before/after comparison, recruiter bulk mode |
| ♿ **Accessibility** | ARIA labels, keyboard navigation, color contrast |
| 🧪 **Tests** | Unit tests for scoring functions, integration tests for API routes |
| 🎨 **UI/UX** | Improve dashboard layout, mobile responsiveness, dark mode |

Issues tagged [`good first issue`](https://github.com/Sushma-1706/RepoRefine/issues?q=is%3Aissue+label%3A%22good+first+issue%22) are great entry points for new contributors.

---

## Questions?

If you're unsure about anything, open a [Discussion](https://github.com/Sushma-1706/RepoRefine/discussions) or drop a comment on the relevant issue. We're happy to help.

Happy contributing! 🚀
