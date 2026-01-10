# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Work Philosophy

- 知行合一，快速迭代 - "如果要对要错，让我自己来"
- 一人公司 / 独立开发者路线
- Repo 代码要简洁
- 有简洁的 README
- 不要过度工程化

## Project Overview

Personal blog for dadalus.com built with Hugo and the PaperMod theme.

## Commands

```bash
# Development
hugo server -D       # Start dev server with drafts
hugo server          # Start dev server without drafts

# Build
hugo --gc --minify   # Production build (same as Vercel)
hugo                 # Basic build

# Create content
hugo new posts/my-post.md
```

## Tech Stack

- **Static Site Generator**: Hugo
- **Theme**: PaperMod (git submodule in `themes/PaperMod`, pinned to 7d061d5)
- **Language**: Chinese (zh-cn)

## Structure

- `content/posts/` - Blog posts in Markdown
- `hugo.toml` - Site configuration (base URL, theme, menu)
- `themes/PaperMod/` - Theme submodule

## Deployment

All projects deploy to **Vercel** (not GitHub Pages).

Configured via `vercel.json`:
- Hugo version: 0.146.0
- Git submodules enabled for theme
- Build uses `rm -f themes/PaperMod/go.mod` before Hugo build (PaperMod's go.mod triggers Hugo Module mode, which conflicts with submodule install)
