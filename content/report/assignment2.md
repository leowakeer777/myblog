---
title: "Assignment2"
date: 2025-04-22
---

# Assignment 2 Report: Static Personal Blog Website

Name: liziao  
Student ID: ZY2457B15
Date: 2025/4/22

---

## 1. Website Setup & Tools

This static website was built using Hugo, a fast and flexible static site generator.  
The theme used is Ananke, which is lightweight and easy to customize.

The site consists of four assignment pages:

- assignment1.md
- assignment2.md
- assignment3.md
- assignment4.md

A custom homepage was created to display only four navigation links (Assignment 1 to Assignment 4), without any extra blog content.  
The homepage was manually configured via `_index.md` and a custom `index.html` layout to hide default post listings.

The output directory was changed from `public/` to `docs/` via the `publishDir = "docs"` setting in `config.toml`, enabling GitHub Pages deployment from the `main` branch.

---

## 2. Git Management Process

Version control was managed using Git with meaningful commits to reflect each step of development.  
The project was tracked using GitHub Desktop and pushed to GitHub.

### Commit History

| Commit # | Message                                                  | Description                                      |
|----------|----------------------------------------------------------|--------------------------------------------------|
| 1        | `Initial commit: created Hugo site`                      | Hugo project initialized with base structure     |
| 2        | `Added Ananke theme and updated config.toml`             | Theme added and configured in site config        |
| 3        | `Created assignment1–4 Markdown pages`                   | Four Markdown assignment pages created           |
| 4        | `Customized homepage layout and _index.md`               | Homepage shows only 4 assignment links           |
| 5        | `Switched publishDir to docs and deployed to GitHub`     | Configured deployment folder and pushed to main  |

---

## 3. Tools & Frameworks Used

- Hugo: Static site generator  
- Ananke: Hugo theme  
- Git + GitHub Desktop: Version control  
- Markdown: Content writing format  
- PowerShell: Command line environment  
- GitHub Pages: Deployment hosting

---

## 4. Deployment Plan

The site was deployed via GitHub Pages.

- Static files generated using `hugo -D`
- Output stored in `/docs` folder
- GitHub Pages configured to deploy from `main` branch, `/docs` folder

Deployed URL: https://leowakeer777.github.io/myblog/

---

## 5. Integration

Assignment 1 report was written in Markdown and included in the website as `content/report/assignment1.md`.  
It is linked from the homepage as one of the four main sections.

---

This report is part of the requirements for Assignment 2: Static Personal Blog Website.
