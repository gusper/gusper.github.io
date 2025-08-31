# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About This Site

This is a personal website built with Hugo static site generator, hosted on GitHub Pages at https://gusperez.com/. The site uses the Anatole theme and includes sections for blog posts, music, software projects, photography, art, and maker content.

## Development Commands

### Local Development
- `hugo server` - Start local development server at http://localhost:1313/
- `hugo server --buildDrafts` - Include draft posts in local development
- `hugo server --buildFuture` - Include future-dated posts (already enabled via config)

### Content Management
- `hugo new blog/YYYY-MM-DD_post-title.md` - Create new blog post in the blog section
- `hugo new posts/post-title.md` - Create new post in the posts section (alternative)
- `hugo new section/page-title.md` - Create new content in any section

### Building
- `hugo` - Build the site for production (outputs to `/public`)
- `hugo --minify` - Build with minification
- `hugo --gc` - Build with garbage collection to clean up unused cache files

## Site Architecture

### Theme and Configuration
- Uses the Anatole Hugo theme (github.com/lxndrblz/anatole v1.15.1)
- Theme is imported as a Hugo module via `go.mod`
- Main configuration in `config.toml`
- Custom CSS styling in `assets/css/custom.css`
- Custom fonts: Bricolage Grotesque and Carrois Gothic SC from Google Fonts
- `buildFuture = true` allows posts with future dates to be published

### Content Structure
- `content/blog/` - Blog posts with date-prefixed filenames (YYYY-MM-DD_title.md)
- `content/software/` - Software project pages
- `content/music/`, `content/photography/`, `content/art/`, `content/maker/` - Other content sections
- Images for blog posts go in `content/blog/images/`
- Static assets (favicons, profile images) in `static/`

### Layout Customization
- Custom layouts in `layouts/` override theme defaults
- Specialized layouts for software section in `layouts/software/`
- Custom head partial in `layouts/partials/head.html` with font loading optimizations
- Custom footer in `layouts/partials/footer.html`

### Styling Notes
- Inline code styling uses pastelly dark-ish blue colors (#4a6fa5 light, #7eb3d3 dark)
- Code backgrounds match page backgrounds (transparent)
- Dark theme uses #181818 background
- Custom mobile burger menu styling
- Responsive layout with custom breakpoints for large screens (1921px+)

### Content Front Matter
Blog posts typically include:
```yaml
title: "Post Title"
date: 2025-08-31T11:32:51-07:00
draft: false
```

Images in blog posts should use absolute paths: `/blog/images/filename.png`