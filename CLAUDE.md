# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo static site for mise-en-place.dev, a personal blog focused on engineering, design, and career topics. The site uses Hugo with Tailwind CSS v4 and follows a minimal architecture pattern.

## Common Commands

### Development
```bash
hugo server          # Start development server
hugo server -D       # Start server including draft posts
```

### Building
```bash
hugo                 # Build the site (output to public/)
```

### Styling
```bash
npx @tailwindcss/cli # Process Tailwind CSS (though Hugo handles this automatically)
```

## Architecture

### Site Structure
- **Content**: Blog posts in `content/posts/` as Markdown files with frontmatter
- **Theme**: Custom theme "vibe" in `themes/vibe/` with overrides in root `layouts/`
- **Styling**: Tailwind CSS v4 with Hugo Pipes integration via `assets/css/main.css`
- **Configuration**: Hugo config in `hugo.toml`, site deployed to mise-en-place.dev

### CSS Architecture
The site uses a two-layer CSS approach:
1. **Hugo Pipes**: Main CSS processing through `layouts/partials/css.html` which processes `assets/css/main.css`
2. **Theme fallback**: Static CSS files in `themes/vibe/` for direct linking

The main CSS file uses Tailwind v4 syntax:
- `@import "tailwindcss"` for base framework
- `@plugin "@tailwindcss/typography"` for prose styling
- `@source "hugo_stats.json"` for class extraction

### Template Hierarchy
- Base template: `layouts/_default/baseof.html` (overrides theme)
- Theme base: `themes/vibe/layouts/_default/baseof.html`
- Partials: Mix of root `layouts/partials/` and theme partials

### Key Features
- **Dark mode**: Automatic detection with localStorage persistence
- **Typography**: Tailwind Typography plugin for content styling
- **Build optimization**: Hugo stats extraction for CSS purging, fingerprinting in production

### Content Management
Posts use standard Hugo frontmatter with title, date, and tags. The site supports both published and draft content via Hugo's draft system.