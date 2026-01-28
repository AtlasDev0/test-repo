# Coding Notes - Elite Engineering Standards

*Authored by Atlas - World-Class Elite Engineering Architect*

---

## Core Principles

1. **Command Line First**
   - Always use CLI tools (`gh`, `git`, `brew`, etc.) over browser UI
   - Browser only when absolutely necessary (CAPTCHA, interactive auth)

2. **Repo Setup (Command Line)**
   ```bash
   # Create new repo on GitHub
   gh repo create AgentCall --public --description "AI Phone Call Agent"
   
   # Clone and work
   git clone git@github.com:AtlasDev0/AgentCall.git
   cd AgentCall
   
   # Push changes
   git add .
   git commit -m "Descriptive commit message"
   git push origin main
   ```

3. **Never Push Without Review**
   - Own repo? Direct commits OK
   - Collaborating? Feature branch → PR → merge

4. **Elite Architect Mindset**
   - Think before coding
   - Design first, implement second
   - Consider: scalability, security, maintainability
   - Write clean, documented code

5. **Automate Everything**
   - Scripts over manual steps
   - Configuration over convention
   - Infrastructure as code

---

## Quick Reference

### GitHub CLI Workflow
```bash
# Create repo
gh repo create <name> [--public|--private] --description "<desc>"

# Create from existing local repo
gh repo create --source=. --push

# Open PR
gh pr create --title "feat: description" --body "Details..."

# Check status
gh repo view --web
```

### Project Setup Template
```bash
mkdir new-project
cd new-project
git init
gh repo create --source=. --push --private
echo "# Project Name" > README.md
git add . && git commit -m "Initial commit"
git push
```

---

## Memory & References

- **Active Projects:** `MEMORY.md`
- **Daily Notes:** `memory/YYYY-MM-DD.md`
- **Coding Standards:** `codingNotes.md` (this file)
- **Tools:** `TOOLS.md`

---

*Updated: 2026-01-28*
