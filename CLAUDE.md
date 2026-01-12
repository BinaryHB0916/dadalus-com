# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Work Philosophy

- 知行合一，快速迭代 - "如果要对要错，让我自己来"
- 一人公司 / 独立开发者路线
- Repo 代码要简洁
- 有简洁的 README
- 不要过度工程化

## Collaboration Rules

1. **需求确认**：当用户描述需求时，先用自己的理解表达出来，让用户 double check 确认后，再进行代码变更
2. **自测验证**：每次代码变更后，自己验证效果（如读取网页确认更新是否生效），确保成功后再请用户做最终确认
3. **不做无效沟通**：避免多次沟通但实际没有生效的情况

## Site Design Rules

- **首页**（文章列表页，body.list）：有天气特效
  - 白天模式：太阳 + 金色尘埃粒子
  - 黑夜模式：下雨 + 闪电 + 蝙蝠
- **文章正文页**（非 list 页）：**完全没有天气特效**，只有白天/黑夜主题切换

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
