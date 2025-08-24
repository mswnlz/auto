# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a Chinese automation tools resource repository (`mswnlz/auto`) that serves as a curated collection of automation scripts, tools, and solutions. The repository includes:

- A simple GitHub Action for notifications (`auto-action`)
- Monthly resource files containing automation tools and scripts
- Multilingual README linking to related projects in the mswnlz ecosystem
- Workflow automation, DevOps tools, and productivity enhancers

## Architecture

### Repository Structure
- `index.js` - Main GitHub Action entry point using @actions/core
- `action.yml` - GitHub Action configuration file
- `package.json` - Node.js dependencies (minimal: only @actions/core)
- `202X0X.md` files - Monthly automation resource collections (format: YYYYMM.md)
- `README.md` - Multilingual project description with ecosystem links
- `.gitignore` - Standard gitignore for Node.js projects
- `WARP.md` - This configuration file

### Monthly Resource Files
Resource files follow a YYYYMM.md naming pattern and contain:
- Automation scripts and tools
- CI/CD pipeline configurations
- DevOps utilities and platforms
- Productivity automation solutions
- System administration tools

## Common Commands

### Development
```bash
# Install dependencies
npm install

# Test the action locally
node index.js
```

### Resource Management
```bash
# Create new monthly resource file
touch $(date +%Y%m).md

# View recent resource files
ls -la 2025*.md | head -5

# Search for automation topics
grep -r "自动化" *.md
grep -r "automation" *.md

# Count total resources
wc -l 2025*.md
```

## Content Guidelines

### Monthly Resource Files
- Use consistent formatting with descriptive titles
- Include proper attribution with "超过100T资料总站网站-doc.869hr.uk" suffix
- Organize resources by automation category (CI/CD, Testing, Deployment)
- Provide both Chinese and English descriptions where applicable
- Include installation and usage instructions

## Ecosystem Integration

This repository is part of a larger project ecosystem including:
- `tools` - General software tools and utilities
- `cross-border` - E-commerce resources
- `healthy` - Health and fitness resources
- `curriculum` - Educational materials
- `AIknowledge` - AI-related knowledge and tutorials
- `book` - Literature and reading materials
- `movies` - Entertainment and media content
- `self-media` - Social media resources
- `edu-knowledge` - Educational knowledge base
- `chinese-traditional` - Traditional culture content
