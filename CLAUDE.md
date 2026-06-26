# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a **content/writing repository** — a vault of long-form blog posts written in Markdown, not a software project. There is no application code, no build system, no tests, and no `package.json`. Work here is almost always editing prose, frontmatter, or managing images, not running commands.

The repo is set up to publish via **Quartz** (the `upstream` remote points at `jackyzha0/quartz`) over an **Obsidian** vault, but no Quartz tooling is installed in the working tree yet — only content is tracked (`git ls-files` shows just `.gitignore`, the post `.md`, and its images). The `.gitignore` is pre-configured for the eventual Quartz build (`public/`, `.quartz-cache/`, `node_modules/`) and Obsidian (`.obsidian/`, `.trash/`). Notably, it excludes binary office/PDF/zip files but **does commit images** (`.png` etc. under `Images/` are tracked).

### Git

- `origin` → `github.com/vinovator/my-blogs` (your repo); `upstream` → Quartz (pull Quartz updates from here, never push). Default branch is `main`.
- Because `upstream` is the Quartz engine, keep commits to **content only** unless deliberately integrating Quartz; don't commit a half-applied Quartz scaffold.

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

### Image embeds (Obsidian/Quartz syntax)

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
