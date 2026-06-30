# README Design

## Context

This repository is a small public library of reusable AI-agent skills. It currently contains one skill, `skills/aave-liquid-glass.md`, plus repository support metadata in `.github/FUNDING.yml`.

The README should serve two audiences:

- GitHub visitors who need to understand what the repository is and whether it is useful.
- Codex and AI-agent users who need enough structure to copy, invoke, adapt, or contribute skills.

## Recommended Approach

Use a hybrid README. Lead with a clear project overview for visitors, then provide concrete usage and authoring guidance for agent users.

This is stronger than a GitHub-only README because it explains how skills are meant to be consumed. It is stronger than an agent-only README because it remains approachable to someone browsing the repository for the first time.

## Content Structure

The README should include:

- A concise title, badges, and value proposition.
- A short explanation of what the repository stores.
- A "Who this is for" section covering developers, AI-agent users, and contributors.
- A "How to use a skill" section with practical copy/adapt/invoke guidance.
- A current skill catalog listing `aave-liquid-glass.md` and its purpose.
- Authoring standards for future skills.
- Repository structure and contribution guidance.
- Support and license sections.

## Skill Writing Standards

The README should reflect the Matt writing guidance without turning into a full essay. Skill authoring guidance should emphasize:

- Predictability: each skill should make the agent follow a repeatable process.
- Clear invocation: document when the skill should be used.
- Focus: one recurring development need per skill.
- Practicality: rules, workflows, examples, and validation checks should help execution.
- Pruning: avoid vague advice, duplication, and stale sections.
- Completion criteria: include checklists or gates when the skill needs a clear stopping point.

## Verification

The README is done when:

- A first-time GitHub visitor can explain the repository's purpose.
- An AI-agent user can understand how to use a skill from `skills/`.
- The current `aave-liquid-glass.md` skill is accurately represented.
- The contribution rules guide future additions without over-constraining the repository.
- The file contains no placeholders, contradictory guidance, or obsolete structure.
