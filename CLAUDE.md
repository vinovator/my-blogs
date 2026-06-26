# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a **content/writing repository** — a vault of long-form blog posts written in Markdown, not a software project. There is no application code, no build system, no tests, and no `package.json`. Work here is almost always editing prose, frontmatter, or managing images, not running commands.

The repo holds **content only** — only the post `.md`, its images, and config files are tracked (`git ls-files` confirms). No site generator or tooling is installed in the working tree. The writings are planned to publish at **vinothhaldorai.com/thoughts**; the publishing pipeline is in flux, so keep changes to content and don't assume a particular generator. The `.gitignore` still lists some legacy build/vault paths (`public/`, `.quartz-cache/`, `node_modules/`, `.obsidian/`); these can be cleaned up as the publishing setup settles. Notably, it excludes binary office/PDF/zip files but **does commit images** (`.png` etc. under `Images/` are tracked).

### Git

- `origin` → `github.com/vinovator/my-blogs` (the source of truth). Default branch is `main`.
- An `upstream` remote may still point at a previous generator (Quartz) — it's legacy and slated for removal; don't push to it.

## Structure & conventions

Each blog post lives in **its own directory** named for the topic, containing:
- A single `.md` file (the post), named after the article's display title.
- An `Images/` subfolder holding the post's figures.

Example: `Enterprise Context Layer Building Blocks/The building blocks of the Enterprise Context Layer.md` with `Enterprise Context Layer Building Blocks/Images/*.png`.

### Frontmatter

Posts begin with YAML frontmatter consumed by the publisher. Match the existing shape when creating or editing posts:

```yaml
---
title: <Display Title>
description: "<one-sentence hook/summary>"
date: YYYY-MM-DD
tags:
  - <kebab-or-PascalCase tags>
aliases:
  - <url-slug>
---
```

### Image embeds

Images use Markdown embeds with **URL-encoded relative paths** and an optional leading width integer in the alt text:
- `![499](Images/Evolution%20of%20Context.png)` — the `499` sets display width.
- `![](Images/Enterprise%20Context%20Layer%20Stack.png)` — no width.

Spaces in filenames must be `%20`-encoded inside the embed even though the file on disk has real spaces.

### Prose style

- Section headings use bold-inside-heading: `### **Section Name**`.
- Dollar amounts are escaped: `\$700 Billion`.
- Posts end with a `### **References**` section: a bulleted list, each entry `Source, "Title" (Date). [url](url)`.

## Working notes

- Filenames intentionally contain spaces — always quote paths in shell commands.
