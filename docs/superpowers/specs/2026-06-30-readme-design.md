# README Design

## Context

This repository is a public library of reusable, customized AI-agent skills. The README should present the repository as a growing skills collection, not as documentation for any one existing skill.

The README should serve these audiences:

- GitHub visitors who need to understand why this skills library is useful.
- Developers who want reusable guidance they can bring into any IDE or AI coding environment.
- Codex and AI-agent users who need enough structure to copy, invoke, adapt, or contribute skills.

## Recommended Approach

Use a hybrid README. Lead with a clear project overview for visitors, then provide concrete usage guidance for popular IDEs and AI coding tools.

This is stronger than a GitHub-only README because it explains how skills are meant to be consumed in real projects. It is stronger than an agent-only README because it remains approachable to someone browsing the repository for the first time.

## Content Structure

The README should include:

- A concise title, badges, and value proposition.
- A short explanation that `skills/` contains various customized skills for development workflows, frontend systems, implementation rules, review workflows, prompts, and project-specific guidance.
- A "Why this is useful" section explaining that skills help agents behave with better context and repeatability across projects.
- A "Who this is for" section covering developers, AI-agent users, IDE users, and contributors.
- A "How to use these skills" section with practical copy/adapt/invoke guidance.
- Specific usage notes for popular environments such as Cursor, VS Code with AI extensions, Windsurf, GitHub Copilot Chat, Claude Code, and Codex.
- A project-level usage section explaining how a team can keep repo-specific skills alongside application code, or copy selected skills into an IDE or agent instruction system.
- A skill catalog that presents the collection broadly and lists available skills without making the README feel centered on one skill.
- Authoring standards for future skills.
- Repository structure and contribution guidance.
- Support and license sections.
- A funding section that points to Buy Me a Coffee and GitHub Sponsors.

## Skill Writing Standards

The README should reflect the Matt writing guidance without turning into a full essay. Skill authoring guidance should emphasize:

- Predictability: each skill should make the agent follow a repeatable process.
- Clear invocation: document when the skill should be used.
- Focus: one recurring development need per skill.
- Practicality: rules, workflows, examples, and validation checks should help execution.
- Pruning: avoid vague advice, duplication, and stale sections.
- Completion criteria: include checklists or gates when the skill needs a clear stopping point.

## Tone And Positioning

The README should be user-facing and useful to someone discovering the repository. It should not over-explain the repository inventory, because the main point is the broader skills library.

The README should position the skills as portable development assets:

- usable in many IDEs,
- adaptable to project-specific workflows,
- valuable for AI-assisted implementation, review, debugging, design, and frontend work,
- easy to copy into an agent instruction system or reference from a project.

## Verification

The README is done when:

- A first-time GitHub visitor can explain the repository's purpose.
- An AI-agent user can understand how to use a skill from `skills/`.
- A developer can understand how to use these skills in popular IDEs or project-level agent instructions.
- The available skills are represented accurately without making one skill dominate the page.
- The contribution rules guide future additions without over-constraining the repository.
- Funding links are present and easy to find.
- The file contains no placeholders, contradictory guidance, or obsolete structure.