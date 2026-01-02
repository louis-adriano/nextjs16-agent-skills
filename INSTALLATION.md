# Installation Guide

This guide will help you install and configure the AI Agent Skills for use with VS Code and GitHub Copilot.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Methods](#installation-methods)
  - [Method 1: Clone Repository (Recommended)](#method-1-clone-repository-recommended)
  - [Method 2: Copy to Project](#method-2-copy-to-project)
  - [Method 3: Fork the Repository](#method-3-fork-the-repository)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before installing the Agent Skills, ensure you have:

- **VS Code** installed (latest version recommended)
- **GitHub Copilot** subscription and extension installed
  - Install from VS Code Extensions: Search for "GitHub Copilot"
  - Sign in with your GitHub account
- **Git** installed on your system (for cloning the repository)

---

## Installation Methods

### Method 1: Clone Repository (Recommended)

This method is ideal for accessing all skills globally across multiple projects.

#### Step 1: Clone the Repository

Open your terminal and run:

```bash
git clone https://github.com/gocallum/nextjs16-agent-skills.git
```

Or if you're using the forked version:

```bash
git clone https://github.com/louis-adriano/nextjs16-agent-skills.git
```

#### Step 2: Configure VS Code

**Option A: Using VS Code Settings UI**

1. Open VS Code
2. Go to Settings (`File` → `Preferences` → `Settings` or press `Cmd/Ctrl + ,`)
3. Search for "copilot" or "agent skills"
4. Look for settings related to GitHub Copilot skills or custom agent skills
5. Add the path to the `.claude` directory (exact setting name may vary by version)

**Option B: Using Settings JSON Directly (Recommended)**

This is the most reliable method across different VS Code versions.

1. Open Command Palette (`Cmd/Ctrl + Shift + P`)
2. Type "Preferences: Open User Settings (JSON)"
3. Add the following configuration:

```json
{
  "github.copilot.agent.skills": [
    "/absolute/path/to/nextjs16-agent-skills/.claude"
  ]
}
```

> **Note:** The setting name `github.copilot.agent.skills` is the most common configuration. If this doesn't work with your version, try placing the `.claude` folder directly in your project (see Method 2 below).

**Example paths:**

- **macOS/Linux:** `/Users/yourname/projects/nextjs16-agent-skills/.claude`
- **Windows:** `C:/Users/yourname/projects/nextjs16-agent-skills/.claude`

#### Step 3: Restart VS Code

Close and reopen VS Code for the changes to take effect.

---

### Method 2: Copy to Project

This method makes skills available only within a specific project.

#### Step 1: Download or Clone

First, get a copy of the repository (as shown in Method 1).

#### Step 2: Copy the `.claude` Folder

Copy the entire `.claude` folder from this repository into your project's root directory:

```bash
cp -r /path/to/nextjs16-agent-skills/.claude /path/to/your-project/
```

#### Step 3: Verify Structure

Your project should now have this structure:

```
your-project/
├── .claude/
│   └── skills/
│       ├── ai-agents-ui-skills/
│       ├── ai-sdk-6-skills/
│       ├── nextjs16-skills/
│       └── ... (other skills)
├── src/
└── ... (your other files)
```

VS Code will automatically detect the `.claude` folder in your project.

---

### Method 3: Fork the Repository

If you want to customize the skills or contribute back:

#### Step 1: Fork on GitHub

1. Go to https://github.com/gocallum/nextjs16-agent-skills
2. Click the "Fork" button in the top right
3. This creates a copy under your GitHub account

#### Step 2: Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/nextjs16-agent-skills.git
```

#### Step 3: Configure VS Code

Follow the same configuration steps as Method 1, using the path to your forked repository.

#### Step 4: Keep Updated

To sync with the original repository:

```bash
git remote add upstream https://github.com/gocallum/nextjs16-agent-skills.git
git fetch upstream
git merge upstream/main
```

---

## Verification

To verify the skills are installed correctly:

### Step 1: Open GitHub Copilot Chat

- Click the GitHub Copilot icon in the sidebar, or
- Press `Cmd/Ctrl + Shift + I` to open Copilot Chat

### Step 2: Test the Skills

Try asking questions related to the skills:

**Example queries:**

- "What are the breaking changes in Next.js 16?"
- "How do I set up Prisma v7 with ESM?"
- "Show me how to use AI SDK 6 with tool calling"
- "What's the best way to implement Upstash Vector DB?"

### Step 3: Check Responses

If the skills are working, Copilot will provide detailed, accurate responses based on the skill documentation.

---

## Troubleshooting

### Skills Not Loading

**Problem:** Copilot doesn't seem to use the skills.

**Solutions:**

1. **Check Path:** Ensure the path in settings.json is absolute and correct
2. **Restart VS Code:** Close and reopen VS Code completely
3. **Check Copilot Status:** Ensure GitHub Copilot is active (check status bar)
4. **Verify .claude Structure:** The `.claude/skills/` directory structure must be intact

### Invalid Path Error

**Problem:** VS Code shows an error about the skills path.

**Solutions:**

1. **Use Absolute Paths:** Don't use `~` or relative paths
2. **Escape Windows Paths:** Use forward slashes or escape backslashes
   - Good: `C:/Users/name/...` or `C:\\Users\\name\\...`
   - Bad: `C:\Users\name\...`

### Skills Not Updating

**Problem:** Changes to skills don't appear in Copilot.

**Solutions:**

1. **Restart VS Code:** Reload the window or restart completely
2. **Clear Copilot Cache:** Use Command Palette → "Developer: Reload Window"
3. **Pull Latest Changes:** If using cloned repository, run `git pull`

### Permissions Issues

**Problem:** Cannot access the `.claude` folder.

**Solutions:**

1. **Check File Permissions:** Ensure the folder is readable
   ```bash
   chmod -R 755 /path/to/nextjs16-agent-skills/.claude
   ```
2. **Check Ownership:** Ensure you own the files
   ```bash
   chown -R $USER /path/to/nextjs16-agent-skills/.claude
   ```

---

## Next Steps

Once installed, explore the available skills:

- Browse the [README.md](README.md) for an overview of all skills
- Check individual skill guides in `.claude/skills/`
- Start using Copilot with context-aware responses powered by these skills

---

## Additional Resources

- [VS Code Copilot Documentation](https://code.visualstudio.com/docs/copilot) - Official VS Code Copilot docs
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot) - GitHub's official Copilot documentation
- [GitHub Copilot Agent Skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) - Learn about agent skills
- [Repository Issues](https://github.com/gocallum/nextjs16-agent-skills/issues) - Report problems or ask questions

---

**Need help?** Open an issue on the [GitHub repository](https://github.com/gocallum/nextjs16-agent-skills/issues).
