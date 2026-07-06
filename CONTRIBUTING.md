# 🤝 Contributing to Useful Skills Repo

Thank you for your interest in contributing to the **Useful Skills Repository**! 

The goal of this repository is to become a high-quality, reusable library of AI skills that can be injected into any IDE or AI assistant to improve consistency, architecture, and coding standards. 

Your contributions help make this repository more powerful for everyone!

---

## 🧠 What Makes a Good Skill?

Before adding or modifying a skill, please ensure it meets the following criteria:

- **Solves a real, recurring need:** Is this a pattern, rule, or workflow you actually use multiple times across different projects?
- **Actionable & Specific:** Avoid vague advice like "write good code." Instead, provide explicit rules: "Functions must be under 20 lines and typed."
- **Context-Aware:** Explain *when* this skill should be applied (e.g., "Use this when building Next.js App Router applications").
- **Checklists & Constraints:** AI models perform best when given explicit boundaries and checklists to validate their work against. Include these in your skill.

---

## 📁 How to Add a New Skill

There are two primary ways to format a skill depending on its complexity.

### 1. Simple Skills (Single File)

If your skill is straightforward, a single Markdown file is perfect.

1. Create a new Markdown file in the `skills/` directory.
2. Use a lowercase, hyphenated filename (e.g., `react-performance.md`).
3. Follow this recommended structure inside the file:
   - **Title & Description:** What the skill is and what it solves.
   - **Trigger / Context:** When the AI should apply these rules.
   - **Core Rules:** The actual constraints and instructions.
   - **Examples:** Code snippets showing the "Right" and "Wrong" ways.

```text
skills/
├── aave-liquid-glass.md
├── react-performance.md
└── (your-skill.md)
```

### 2. Advanced Skills (Folder Structure)

If your skill requires supporting files, reference documents, or multiple examples, create a folder for it inside the `skills/` directory.

1. Create a new folder (e.g., `advanced-architecture-patterns/`).
2. Inside the folder, place your main instruction file (e.g., `SKILL.md` or `skill-name.md`).
3. Add subdirectories for examples or references as needed.

```text
skills/
└── advanced-architecture-patterns/
    ├── SKILL.md
    ├── examples/
    │   └── example-implementation.ts
    └── references/
        └── architecture-diagram.mermaid
```

---

## 🔄 Pull Request Process

1. **Fork the repository.**
2. **Create a new branch** for your skill (`git checkout -b feature/new-skill-name`).
3. **Commit your changes.** Please use descriptive commit messages (e.g., `feat: add react performance optimization skill`).
4. **Push to the branch.**
5. **Open a Pull Request (PR).** 
   - In the PR description, briefly explain what the skill does and why it is useful.
   - Wait for review! We will merge it in as soon as possible.

---

Thank you for contributing! Let's build the ultimate AI coding library together. 🚀
