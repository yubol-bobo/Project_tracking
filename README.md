# Project Tracking

A minimal, modern dashboard to track research projects and paper submissions. Built as a static site deployed via GitHub Pages.

**Live demo**: [yubol-bobo.github.io/Project_tracking](https://yubol-bobo.github.io/Project_tracking/)

## Features

- **Project progress bar** — click to expand and see individual steps (Idea Brainstorm, Experiment Design, Running Exp, Results, Paper Drafting)
- **Venue submission timeline** — auto-highlights current stage based on today's date
- **Optional links** — attach Overleaf, OpenReview, or any URL to steps and venues
- **Light/Dark mode** — toggle with persistence
- **Font size control** — A-/A+ buttons
- **Data-driven** — each project is a simple JSON file, no need to touch HTML

## Quick Start

1. Click **"Use this template"** to create your own repo
2. In your repo, go to **Settings > Pages > Source** and select **GitHub Actions**
3. Edit files in the `projects/` folder to add your own projects
4. Push — your site auto-deploys

## How to Add a Project

1. Create a new JSON file in `projects/` (e.g. `projects/my_paper.json`):

```json
{
  "name": "My Paper Title",
  "description": "A brief description of the project.",
  "steps": [
    { "label": "Idea Brainstorm",   "status": "done" },
    { "label": "Experiment Design", "status": "done" },
    { "label": "Running Exp",       "status": "current" },
    { "label": "Results",           "status": "pending" },
    { "label": "Paper Drafting",    "status": "pending", "link": "https://www.overleaf.com/project/xxx" }
  ],
  "venue": "NeurIPS 2026",
  "venueUrl": "https://openreview.net/group?id=NeurIPS.cc/2026/Conference",
  "timeline": [
    { "label": "Abstract Due",   "date": "2026-05-10" },
    { "label": "Full Paper Due", "date": "2026-05-17" },
    { "label": "Reviewing",      "date": "2026-06-01" },
    { "label": "Review Release", "date": "2026-07-15" },
    { "label": "Decision",       "date": "2026-08-01" }
  ]
}
```

2. Add the filename to `projects/index.json`:

```json
[
  "my_paper.json"
]
```

3. Push to `main` — the site updates automatically.

## Field Reference

### Steps

| Field    | Required | Description                                      |
|----------|----------|--------------------------------------------------|
| `label`  | Yes      | Step name                                        |
| `status` | Yes      | `"done"`, `"current"`, or `"pending"`            |
| `link`   | No       | URL (e.g. Overleaf link) — shows a link icon     |

Progress is auto-calculated: `done` = 1, `current` = 0.5, `pending` = 0.

### Venue

| Field      | Required | Description                                  |
|------------|----------|----------------------------------------------|
| `venue`    | Yes      | Venue name (e.g. "NeurIPS 2026")             |
| `venueUrl` | No       | Link to submission site (e.g. OpenReview)    |

### Timeline

| Field   | Required | Description                              |
|---------|----------|------------------------------------------|
| `label` | Yes      | Event name (e.g. "Abstract Due")         |
| `date`  | Yes      | Date in `YYYY-MM-DD` format              |

Timeline status updates automatically based on today's date.

## License

MIT
