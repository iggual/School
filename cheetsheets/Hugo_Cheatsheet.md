---
title: "Hugo Cheatsheet"
date: 2025-05-27T22:00:00+01:00
draft: false
tags: ['Hugo', 'CMS', 'WebSite']
---

# Hugo CMS Cheatsheet  
*A quick and dirty reference for Hugo static site generator commands, structure, and customization.*

---
## Installation & Setup

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

## Basic Commands

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

## Directory Structure

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

## Configuration (config.toml)

```toml
  
baseURL = "https://example.com"
languageCode = "en-us"
title = "My Hugo Site"
theme = "ananke"

[params]
  description = "A concise cheatsheet for Hugo CMS"

Menu Configuration

  [[menu.main]]
    name = "Home"
    url = "/"
  [[menu.main]]
    name = "About"
    url = "/about/"
  
```

## Navigation Template (layouts/partials/nav.html)

```bash
<nav class="main-menu">
  <ul class="menu-list">
    {{ $currentPage := . }}
    {{ range .Site.Menus.main.ByWeight }}
      {{ $base := path.Base .URL }}
      {{ if not (in $.Site.Params.excludeFromNav $base) }}
        <li class="menu-item">
          <a href="{{ .URL }}" class="menu-link
            {{ if $currentPage.IsPage }}
              {{ $sec := $currentPage.Page.Section }}
              {{ $file := $currentPage.File.TranslationBaseName }}
              {{ if or (eq $sec $base) (eq $file $base) 
                  (and (eq $sec "") (eq $file "_index") (eq $base "/")) }}
                active
              {{ end }}
            {{ end }}"
          >
            {{ .Name }}
          </a>
        </li>
      {{ end }}
    {{ end }}
  </ul>
</nav>

```

## Templates & Shortcodes

```bash

Base Template: layouts/_default/baseof.html

Blocks:

{{ block "main" . }}
  <h1>Hello World</h1>
{{ end }}

Partials:

{{ partial "header.html" . }}

```

## Content Organization

```bash
Front Matter:

---
title: "My Post"
date: 2023-10-01
draft: false
tags: 'Hugo', 'CMS'
---

Markdown Syntax:

# Heading
[Link](url) | **Bold** | *Italic*

```

## Content Customization
### README.md in Every Section

```
---
title: "Timeless Guide"
list: false  # Prevent listing in recent posts
sitemap_exclude: true
rss_exclude: true
---

Welcome to the Timeless section! This content appears at the top of the section.

```
### Section Homepage Template (layouts/_default/list.html)

```bash
{{ define "main" }}
  <!-- Section README -->
  {{ if .IsSection }}
    {{ $readmePath := printf "%s/README.md" .Section }}
    {{ with .Site.GetPage $readmePath }}
      <div class="section-readme">
        {{ .Content }}
      </div>
    {{ end }}
  {{ end }}

  <!-- Recent Articles -->
  <div class="recent-posts">
    <ul>
      {{ if or (eq .Kind "section") (eq .Kind "home") }}
        {{ $pages := where .Site.RegularPages "Params.list" "!=" false }}
        {{ $filtered := where $pages "Section" "==" .Section }}
        {{ range first 5 (sort $filtered "Date" "desc") }}
          <li><a href="{{ .RelPermalink }}">{{ .Title }}</a></li>
        {{ end }}
      {{ else if eq .Kind "term" }}
        {{ range first 5 .Data.Pages }}
          <li><a href="{{ .RelPermalink }}">{{ .Title }}</a></li>
        {{ end }}
      {{ end }}
    </ul>
  </div>
{{ end }}

```


## Deployment

```bash
# Build to /public
hugo --minify

# Deploy to GitHub Pages
hugo --baseUrl="https://username.github.io/repo/"
git add .
git commit -m "Update site"
git push origin main

```

## CSS 


### Adding Custom CSS
- Create CSS file in `/static/css/` (e.g., `styles.css`)
- Link CSS in HTML template header:

```html
  <link rel="stylesheet" href="/css/styles.css">
```

### Background Images

   - Place images in /static/images/
   - Use relative paths in CSS:

```css
body {
  background-image: url("/images/your-image.jpg");
  background-size: cover;
}
```
For Hugo Pipes asset processing, use /assets/images/ and resources.Get


### Tiled Background Example

- Place tile image in /static/images/ (e.g., pattern.png)
- Basic tiling CSS:

```css
body {
  background-image: url("/images/pattern.png");
  background-repeat: repeat; /* Repeats both directions */
}
Common variations:

/* Repeat horizontally only */
background-repeat: repeat-x;

/* Repeat vertically only */
background-repeat: repeat-y;

/* No repeat (single image) */
background-repeat: no-repeat;
With Hugo Pipes asset processing:

{{ $pattern := resources.Get "images/pattern.png" }}
body {
  background-image: url("{{ $pattern.RelPermalink }}");
  background-repeat: repeat;
}
```

Add background-color as fallback:
```css
background-color: #f0f0f0; /* Matches tile base color */
```

## Menus 

### 1. Configuration (TOML/YAML)

Define menus in config.toml or config.yaml:

- Format	Example Configuration
   - TOML	

toml<br>[[menu.main]]<br> name = "Home"<br> url = "/"<br> weight = 1<br>[[menu.main]]<br> name = "About"<br> url = "/about"<br> weight = 2

   - YAML	

yaml<br>menu:<br> main:<br> - name: "Home"<br> url: "/"<br> weight: 1<br> - name: "About"<br> url: "/about"<br> weight: 2

### 2. Rendering in Templates

Basic menu rendering in HTML templates:

```css
<ul>
  {{ range .Site.Menus.main }}
  <li>
    <a href="{{ .URL }}" 
       class="{{ if .IsMenuCurrent "main" . }}active{{ end }}">
      {{ .Name }}
    </a>
  </li>
  {{ end }}
</ul>
```

### 3. Styling Menus with CSS

Horizontal Menu:

```css
ul {
  list-style: none;
  display: flex;
  gap: 1rem;
}
Vertical Menu:


ul {
  list-style: none;
  display: block;
}
ul li {
  margin: 0.5rem 0;
}
Active Link Style:


.active {
  color: #ff4081;
  font-weight: bold;
}

```
### 🏷️ Tag Styling
### Centered Tags with Bullets (taglist.html)

```bash

<p class="taglist">
  Tags: 
  {{ range $i, $e := .Params.tags }}
    {{ if gt $i 0 }} · {{ end }}
    <a href="/tags/{{ $e | urlize }}">{{ $e }}</a>
  {{ end }}
</p>


CSS:

/* Center tags with bullet separators */
.taglist {
  text-align: center;
  margin: 2rem 0;
}

.taglist a {
  margin: 0 0.5rem;
  padding: 0 0.5rem;
  position: relative;
}

.taglist a:not(:last-child)::after {
  content: "·";
  position: absolute;
  right: -0.25rem;
  top: 50%;
  transform: translateY(-50%);
  color: #666;
}

```
## CSS & Layout
### Background Images

```bash

body {
  background-image: url("/images/pattern.png");
  background-repeat: repeat;
  background-color: #f0f0f0; /* Fallback */
}

```

### Responsive Container

```bash
.content-wrapper {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem 1rem;
}
```

## Templates & Partials
### Base Template Structure (baseof.html)

```html

<body>
  {{ partial "nav.html" . }}
  <div class="page-container">
    <div class="content-wrapper">
      {{ block "main" . }}{{ end }}
    </div>
  </div>
</body>
```
### Debugging Variables

```html
<pre>{{ printf "%#v" . }}</pre>
```

## Customization Tips

```bash
Hugo Modules:

hugo mod init github.com/username/mysite
Debugging:
Use {{ printf "%#v" . }} to inspect variables.
Performance:
Enable caching: hugo --enableGitInfo
```
## Common Issues
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
