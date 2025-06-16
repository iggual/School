---
title: "Hugo Cheatsheet"
date: 2025-06-06T18:55:17+01:00
draft: false
tags: ['Hugo', 'CMS', 'WebSite', 'HowTo', 'All']
---
*A quick and dirty reference for Hugo static site generator commands, structure, and customization.*

---

# Hugo Cheatsheet

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
hugo new posts/sub-dir/my-post.md
  
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
---

## Useful Hugo commands params

## Site Creation and Management

- Create a new site: hugo new site <site-name> -f yml
- Create new content: hugo new <content-path>
- Build site: hugo
- Build site including draft content: hugo -D
- Serve site locally: hugo server
- Serve site with draft content: hugo server -D

## Content Management

- Add a new post: hugo new posts/<post-name>.md
- Add a new page: hugo new <page-name>.md

## Theme Management

- Add a theme: git submodule add <theme-repo-url> themes/<theme-name>
- Use a theme: Add theme = "<theme-name>" to config.toml

## Build Options

- Specify output directory: hugo -d <directory>
- Build with base URL: hugo -b <URL>
- Minify output: hugo --minify

## Server Options

- Specify port: hugo server -p <port-number>
- Bind to specific IP: hugo server --bind <ip-address>
- Watch for changes: hugo server -w
- Disable live reload: hugo server --disableLiveReload

Debugging


## Utility Commands

- Version check: hugo version
- List all pages: hugo list all
- Print site configuration: hugo config

Replace placeholders (enclosed in < >) with actual values when using these commands.

## Troubleshoot Step-By-Step:

#### 1. Check the Console (Terminal + Browser)
- **Hugo Server Output:** Run hugo server -D (includes drafts) and look for warnings/errors in the terminal. Common issues:
   - Missing partials (e.g., partial "header.html" not found)
   - Invalid front matter (YAML/TOML/JSON syntax)
   - Failed asset pipelines (SCSS/JS builds)
- **Browser Console:** Open DevTools (F12) → Console/Network tabs. Are CSS/JS assets failing to load? Are there 404s for pages/assets?

#### 2. The Usual Suspects
- **Theme Issues:**
   - Did you recently update or switch themes? Run git diff (if using version control) to spot breaking changes.
   - Check layouts/ folder: Are partials (headers, footers) correctly named and referenced?
- **Data Files (data/ folder):**
   - Is your site pulling data from .yaml, .json, or .toml files? A typo there can break everything silently.
- **Permalinks & URLs:**
   - Check config.toml for canonifyURLs or relativeURLs settings. Misconfigured URLs often cause broken links/assets.
- **Static Assets** (static/ folder):
   - Are images/CSS/JS files in static/ referenced correctly? Hugo serves them as-is (no processing).

#### 3. Template Debugging

Hugo’s Go templating can be finicky. Try this:

```
{{ printf "%#v" .Site.Data }} <!-- Dump all data for debugging -->
{{ partial "nonexistent-partial.html" . }} <!-- Test partial errors -->
```
If you see ERROR in the terminal when saving a file, you’ve found the culprit.

#### 4. Caching & Build Artifacts

- Run hugo --gc --cleanDestinationDir to force a clean build.
- Delete the public/ or dist/ folder manually (if your publishDir is customized).
- Clear browser cache (or test in incognito mode).

#### 5. Deployment Gotchas

- **Netlify/Vercel/etc:** Check the build logs for errors. Sometimes local builds work, but deployment fails due to Hugo version mismatches. Add HUGO_VERSION to your environment variables to lock it.
- **GitHub Pages:** Ensure you’re deploying the correct branch/folder (often public/ or docs/).

#### 6. Quick Wins

- **Update Hugo:** Run hugo version. If you’re not on the latest extended version, upgrade:
```
brew update && brew upgrade hugo # macOS/Linux
```
- **Test with a Default Theme:**
```bash
hugo new site temp-site
cd temp-site && git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo 'theme = "ananke"' >> config.toml
hugo server -D
```
If this works, the issue is in your current project’s config/code.

## Hugo Usage:
```
  hugo [flags]
  hugo [command]

Available Commands:
  build       Build your site
  completion  Generate the autocompletion script for the specified shell
  config      Display site configuration
  convert     Convert front matter to another format
  env         Display version and environment info
  gen         Generate documentation and syntax highlighting styles
  help        Help about any command
  import      Import a site from another system
  list        List content
  mod         Manage modules
  new         Create new content
  server      Start the embedded web server
  version     Display version

Flags:
  -b, --baseURL string             hostname (and path) to the root, e.g. https://spf13.com/
  -D, --buildDrafts                include content marked as draft
  -E, --buildExpired               include expired content
  -F, --buildFuture                include content with publishdate in the future
      --cacheDir string            filesystem path to cache directory
      --cleanDestinationDir        remove files from destination not found in static directories
      --clock string               set the clock used by Hugo- 
                                   e.g. --clock 2021-11-06T22:30:00.00+09:00
      --config string              config file (default is hugo.yaml|json|toml)
      --configDir string           config dir (default "config")
  -c, --contentDir string          filesystem path to content directory
  -d, --destination string         filesystem path to write files to
      --disableKinds strings       disable different kind of pages (home, RSS etc.)
      --enableGitInfo              add Git revision, date, author- 
                                   and CODEOWNERS info to the pages
  -e, --environment string         build environment
      --forceSyncStatic            copy all files when static is changed.
      --gc                         enable to run some cleanup tasks (remove unused cache files)- 
                                   after the build
      --ignoreCache                ignores the cache directory
      --ignoreVendorPaths string   ignores any _vendor for module paths matching the given- 
                                   Glob pattern
  -l, --layoutDir string           filesystem path to layout directory
      --logLevel string            log level (debug|info|warn|error)
      --minify                     minify any supported output format (HTML, XML etc.)
      --noBuildLock                don't create .hugo_build.lock file
      --noChmod                    don't sync permission mode of files
      --noTimes                    don't sync modification time of files
      --panicOnWarning             panic on first WARNING log
      --poll string                set this to a poll interval, e.g --poll 700ms, to use- 
                                   a poll based approach to watch for file system changes
      --printI18nWarnings          print missing translations
      --printMemoryUsage           print memory usage to screen at intervals
      --printPathWarnings          print warnings on duplicate target paths etc.
      --printUnusedTemplates       print warnings on unused templates.
      --quiet                      build in quiet mode
      --renderSegments strings     named segments to render (configured in the segments config)
  -M, --renderToMemory             render to memory (mostly useful when running the server)
  -s, --source string              filesystem path to read files relative from
      --templateMetrics            display metrics about template executions
      --templateMetricsHints       calculate some improvement hints when combined with- 
                                   --templateMetrics
  -t, --theme strings              themes to use (located in /themes/THEMENAME/)
      --themesDir string           filesystem path to themes directory
      --trace file                 write trace to file (not useful in general)
  -w, --watch                      watch filesystem for changes and recreate as needed
```

## Useful links

   > [Hugo Docs](https://gohugo.io/documentation/) || [Theme Showcase](https://themes.gohugo.io/)

---
---
