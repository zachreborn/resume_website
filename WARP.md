# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

Resume website is a static HTML/CSS portfolio and resume site deployed to AWS S3 with CloudFront CDN. The site showcases professional background, skills, philosophy, and experience. There are no build steps, tests, or complex dependencies—this is a straightforward static site deployment.

## Architecture

**Tech Stack:**
- HTML5 for markup
- CSS3 for styling (custom stylesheet in `css/style.css`)
- Google Analytics for tracking
- Google Fonts (Fira Sans)
- FontAwesome for icons
- AWS S3 for hosting
- AWS CloudFront for CDN

**Structure:**
- `index.html`: Main resume and portfolio landing page
- `architecture.html`: Technical explanation of how this website is built and deployed
- `contact.html`: Contact information page
- `error.html`: Custom error page
- `css/style.css`: Centralized styling for all pages
- `media/`: Images (headshots, awards, screenshots) and PDFs (resume versions)
- `.github/workflows/`: CI/CD pipelines for testing and deployment

**Deployment:**
- `dev.yml`: Deploys to dev S3 bucket on pushes to non-main branches
- `main.yml`: Deploys to production S3 bucket and invalidates CloudFront cache on pushes to main
- `test.yml`: Runs Super Linter (code quality checks) on PRs and pushes to main

## Git & Commit Workflow

All commits must be signed. When creating PRs or pushing changes, ensure status checks pass. Use the pull request template in `.github/pull_request_template.md`.

## Common Commands

**View the website locally:**
```sh
# Open index.html in a browser
open index.html
```

**Linting:**
The project uses Super Linter via GitHub Actions on PRs and main branch pushes. To validate code locally before pushing:
```sh
# Code should follow markdown, HTML, CSS, and YAML standards
# Check for trailing whitespace, proper formatting in HTML/CSS/YAML files
```

**Deploy to Dev:**
Push to any branch except `main`, `master`, `production`, or `prod`. This triggers the dev deployment workflow which syncs to the dev S3 bucket.

**Deploy to Production:**
Push to the `main` branch. This triggers the production deployment workflow which syncs to the prod S3 bucket and invalidates CloudFront cache to ensure fresh content is served.

## Important Notes

- All CSS should be added to `css/style.css` to keep styling centralized
- Images should be organized in `media/images/`; PDFs in `media/pdfs/`
- When adding new HTML pages, ensure they link navigation consistently (see `index.html` header as reference)
- Google Analytics tag is included in `index.html` (tracking ID: G-5HRJ53HCZD)
- AWS credentials and CloudFront distribution ID are stored as secrets and variables in GitHub Actions
