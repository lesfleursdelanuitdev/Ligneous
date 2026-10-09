# Ligneous

Ligneous is a genealogy platform. It reads GEDCOM family-tree files, stores them in Postgres, and turns them into websites that families can browse, search and add stories to. It powers [gonsalvesfamily.com](https://gonsalvesfamily.com), a live family-history site with its own admin app.

This repository is the map of the project. The code lives in the repositories listed below.

## How the pieces fit

```
GEDCOM file
   │
   ▼
ligneous-gedcom-lib (Go)        parse, validate, enrich, export
   │
   ▼
ligneous-gedcom-lib-api (Go)    HTTP API over the library
   │
   ▼
Postgres  ◄── ligneous-gedcom-flask-api (Python)   research, statistics, natural-language search
   │
   ▼
Next.js sites                   the-gonsalves-family (public site)
                                the-gonsalves-family-admin (editors)
   ▲
   └── @ligneous/* React packages: tree and chart views, albums, story editor
```

## Repositories

### Core

| Repository | Language | What it does |
|---|---|---|
| [ligenous-gedcom-lib](https://github.com/lesfleursdelanuitdev/ligenous-gedcom-lib) | Go | GEDCOM parser, validator, enricher, exporter and record reconciliation, with command-line tools |
| [ligneous-gedcom-lib-api](https://github.com/lesfleursdelanuitdev/ligneous-gedcom-lib-api) | Go | HTTP API over the GEDCOM library, packaged with Docker |
| [ligneous-gedcom-flask-api](https://github.com/lesfleursdelanuitdev/ligneous-gedcom-flask-api) | Python | Research and analytics API (Flask): saved queries, statistics, reports, and natural-language search through an LLM |

### Front-end packages

| Repository | Language | What it does |
|---|---|---|
| [genealogy-visualization-engine](https://github.com/lesfleursdelanuitdev/genealogy-visualization-engine) | TypeScript | Family-tree and chart rendering |
| [ligneous-story-creator](https://github.com/lesfleursdelanuitdev/ligneous-story-creator) | TypeScript | React block-based editor and renderer for family stories |
| [ligneous-album-view](https://github.com/lesfleursdelanuitdev/ligneous-album-view) | TypeScript | Types and helpers for photo albums generated from GEDCOM data |
| [ligneous-album-generated-queries](https://github.com/lesfleursdelanuitdev/ligneous-album-generated-queries) | TypeScript | Prisma queries behind the generated albums |

### Applications

| Repository | Language | What it does |
|---|---|---|
| [the-gonsalves-family](https://github.com/lesfleursdelanuitdev/the-gonsalves-family) | TypeScript | The public family-history site (Next.js, Tailwind, TanStack Query, D3) |
| [the-gonsalves-family-admin](https://github.com/lesfleursdelanuitdev/the-gonsalves-family-admin) | TypeScript | The editors' app for people, events, media and stories |
| [ligneous-frontend](https://github.com/lesfleursdelanuitdev/ligneous-frontend) | JavaScript | The earlier Ligneous front end |

## Stack

Go, Python (Flask), TypeScript, React, Next.js, Prisma, Postgres, D3 and Tailwind. In production it runs as rootless Podman containers managed by systemd, behind nginx.

## Status

gonsalvesfamily.com is live. The libraries are used in production by that site and are still evolving.

[TODO: author line, e.g. "Built by <your name>", and how you'd like the AI-assistance credit worded here]
