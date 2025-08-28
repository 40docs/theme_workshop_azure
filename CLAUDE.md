# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is the **theme** repository - a custom MkDocs Material theme for the 40docs platform. It provides Fortinet-branded styling, custom components, and interactive features for documentation sites across the ecosystem.

## Common Development Commands

### MkDocs Theme Development
```bash
# Test theme locally (from parent docs repository)
mkdocs serve                     # Serve with live reload
mkdocs build                     # Build static site

# Theme validation
yamllint mkdocs.yml             # Validate YAML configuration
```

## Architecture and Components

### Core Theme Structure
- **mkdocs.yml**: Main theme configuration with Material theme customizations
- **custom.js**: Interactive Pod IP replacement functionality
- **extra.css**: Fortinet brand styling and custom CSS overrides
- **partials/**: Custom HTML templates for navigation, content, and headers
- **covers/**: PDF export templates and styling

### Key Features

#### Dynamic Pod IP Replacement
The `custom.js` implements a client-side IP replacement system:
- Stores Pod IP in localStorage for persistence
- Replaces `{{pod_ip}}` placeholders throughout documentation
- Updates links dynamically when IP changes
- Provides form interface for IP input

#### Material Theme Customization
Configuration includes:
- **Dual logos**: Standard and dark mode variants (`fabric.svg`, `fabric-white.svg`)
- **Color scheme**: Automatic light/dark mode with Fortinet brand colors
- **Navigation**: Tabs, sticky navigation, auto-hide header
- **Content features**: Code copy, annotations, tooltips

#### Custom Admonitions
- **Forti admonition**: Custom branded callout boxes with Fortinet logo
- Uses Fortinet red color scheme (`rgb(218, 41, 28)`)

### Markdown Extensions and Plugins
- **PyMdown Extensions**: Enhanced markdown with syntax highlighting, tabbed content
- **Content Management**: Awesome pages, literate navigation, include markdown
- **Interactive Features**: Mark-as-read buttons, content tabs, asciinema player
- **Export**: PDF generation with custom covers and styling
- **Media**: Drawio diagrams, lightbox images, mermaid charts

### Styling Architecture
- **Grid cards**: Custom spacing and styling for card layouts
- **Navigation**: Hidden nav titles, custom logo sizing
- **Brand consistency**: Fortinet colors and typography (Inter font)

## Important Guidelines

### Theme Development
- **Environment variables**: Many settings use `!ENV` for runtime configuration
- **Custom directory**: Theme files are referenced from `docs/theme/` path
- **Asset organization**: Keep logos, icons, and media in root theme directory

### Configuration Management
- **YAML structure**: Follow existing indentation and structure in mkdocs.yml
- **Plugin dependencies**: Maintain plugin order for proper functionality
- **Feature flags**: Use environment variables for conditional features (PDF export)

### Brand Compliance
- **Logo usage**: Maintain dual logo system for light/dark modes
- **Color scheme**: Stick to Fortinet brand colors (red #da291c)
- **Typography**: Use Inter for text, Roboto Mono for code

### Interactive Features
- **Pod IP system**: Maintain localStorage functionality for lab environments
- **Form styling**: Use inline styles for form components to ensure consistency
- **Link updating**: Preserve dynamic link replacement functionality

## Integration Notes

### Parent Repository Integration
This theme is designed to be used by documentation repositories in the 40docs ecosystem:
- Referenced via `custom_dir: docs/theme` in consuming repositories
- Assets are included via relative paths
- Environment variables allow per-site customization

### PDF Export System
- Custom covers with Jinja2 templates
- SCSS styling for print media
- Aggregated PDF generation for complete documentation sets
- Environment-controlled enable/disable functionality

### Plugin Dependencies
Critical plugins that must remain configured:
- **awesome-pages**: Navigation structure management
- **mark-as-read**: Progress tracking functionality
- **content-tabs**: Tabbed content display
- **include-markdown**: Content inclusion across repositories
- **exporter**: PDF generation system