# Documentation Structure
This document explains how the SensorHub Cloud documentation is organized, what each folder contains, and how contributors should decide where new content belongs.

SensorHub Cloud is a fictional documentation project created for portfolio purposes. The structure is designed to demonstrate docs-as-code organization, information architecture, task-based documentation, API documentation, troubleshooting content, release notes, and documentation governance.

## Documentation goals
The documentation set is organized to help users:
- Learn what SensorHub Cloud does.
- Set up the product for the first time.
- Complete common administrator tasks.
- Connect gateways and sensor devices.
- Use the SensorHub API.
- Troubleshoot common problems.
- Understand product changes through release notes.

Each section supports a different user need. New content should be placed where users are most likely to look for it.

## Repository structure
```
docs-as-code-portfolio/

README.md
CONTRIBUTING.md
docs-structure.md
confidentiality-note.md

docs/
  index.md

  getting-started/
    overview.md
    quickstart.md
    connect-a-gateway.md

  admin/
    manage-users-and-roles.md
    configure-alert-rules.md

  api/
    api-overview.md
    authentication.md
    sensor-readings-endpoint.md
    error-codes.md

  troubleshooting/
    gateway-offline.md
    missing-sensor-data.md

  release-notes/
    2026-06-release-notes.md

openapi/
  sensorhub-api.yaml

style-guide/
  voice-and-tone.md
  procedure-template.md
  terminology.md

images/
  sensorhub-dashboard-wireframe.png
  gateway-connection-flow.png

.github/
  pull_request_template.md
```
## Root-level files
Root-level files explain the repository's purpose, structure, and contribution standards.

| File | Purpose |
| :--- | :--- |
| README.md | Introduces the portfolio project, explains what it demonstrates, and links to major sections. |
| CONTRIBUTING.md | Defines contribution standards, review expectations, and documentation workflow. |
| docs-structure.md | Explains how the documentation set is organized. |
| confidentiality-note.md | Explains that the project is fictional and contains no proprietary employer content. |

These files are written for hiring managers, reviewers, and contributors. They explain the documentation system behind the sample.
