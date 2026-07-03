# Redmine/GitLab Weekly Report Automation

## Problem

Weekly meeting reports were repetitive to write and easy to miss small fields such as dates, progress, or completion status. Commit activity also had to be checked separately from the report outline.

## Solution

I built a Python CLI that converts a simple Markdown outline into a Redmine wiki section. The tool validates missing status/date/progress fields before publishing and keeps preview, clipboard copy, file output, and API publish steps separate.

## Key Ideas

- Treat the report source as structured outline data.
- Validate missing fields before Redmine publish.
- Use environment variables for API keys.
- Avoid overwriting unrelated wiki sections.
- Use GitLab commits only as report candidates, not as automatic truth.

## Tech

- Python
- Redmine API
- GitLab API
- Markdown/CommonMark
- PowerShell

## What I Would Show In Interview

- Sample input outline
- Validation output
- Generated Redmine wiki body
- API publish safety flow
