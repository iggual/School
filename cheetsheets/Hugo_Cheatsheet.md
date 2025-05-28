---
title: "Hugo Cheatsheet"
date: 2025-05-27T22:00:39+01:00
draft: false
tags: ['Hugo', 'CMS', 'WebSite']
---

# Hugo CMS Cheatsheet  
*A quick reference for Hugo static site generator commands, structure, and customization.*

---
## 1. Installation  

```bash

# Linux (Debian/Ubuntu)
sudo apt-get install hugo

# macOS (Homebrew)
brew install hugo

# Windows (Chocolatey)
choco install hugo -confirm

# Verify installation
hugo version
  
```

## 2. Basic Commands

```bash
  
# Create a new site
hugo new site my-site

# Add a theme (e.g., Ananke)
cd my-site
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke

# Start local server (http://localhost:1313)
hugo server

# Build static files (output in /public)
hugo

# Create a new post/page
hugo new posts/my-post.md
  
```

## 3. Directory Structure

```perl

my-site/
├── archetypes/    # Templates for new content
├── content/       # Markdown files (e.g., posts/, pages/)
├── data/          # YAML/JSON/TOML data files
├── layouts/       # Templates (HTML files)
├── static/        # Static assets (CSS, JS, images)
├── themes/        # Theme repositories
├── config.toml    # Site configuration

```

## 4. Configuration (config.toml)

```toml
  
baseURL = "https://example.com"
languageCode = "en-us"
title = "My Hugo Site"
theme = "ananke"

[params]
  description = "A concise cheatsheet for Hugo CMS"

[menu.main]
  [[menu.main]]
    name = "Home"
    url = "/"
  [[menu.main]]
    name = "About"
    url = "/about/"
  
```

## 5. Templates & Shortcodes

```bash

Base Template: layouts/_default/baseof.html

Blocks:

{{ block "main" . }}
  <h1>Hello World</h1>
{{ end }}

Partials:

{{ partial "header.html" . }}

```

## 6. Content Organization

```bash
Front Matter:

title: "My Post"
date: 2023-10-01
draft: false
categories:
  - "Tech"
tags:
  - "Hugo"

Markdown Syntax:

# Heading
[Link](url) | **Bold** | *Italic*

```

## 7. Deployment

```bash
# Build to /public
hugo --minify

# Deploy to GitHub Pages
hugo --baseUrl="https://username.github.io/repo/"
git add .
git commit -m "Update site"
git push origin main

```
## 8. Customization Tips
```bash
Hugo Modules:

hugo mod init github.com/username/mysite
Debugging:
Use {{ printf "%#v" . }} to inspect variables.
Performance:
Enable caching: hugo --enableGitInfo
```
## 9. Common Issues
```bash
Theme Not Loading: Check config.toml theme name and submodule path.
404 Errors: Run hugo server --disableFastRender to debug.
SCSS/SASS Errors: Use the extended Hugo version.
```
## Quick Reference
```
Task			Command/Location
Local Server		hugo server
Build Static Site	hugo
Configuration		config.toml
Themes			themes/ directory
Content			content/ directory
```

---

   > [Hugo Docs](https://gohugo.io/documentation/) || [Theme Showcase](https://themes.gohugo.io/)

---
---

