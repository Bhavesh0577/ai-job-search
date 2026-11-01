# Search Queries for Job Scraper

<!-- SETUP: Run /setup to populate search queries based on your profile -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** Queries are in English unless your market expects otherwise.

## Search Sites

Primary:
- **[YOUR_JOB_BOARD]**
- **[YOUR_INDUSTRY_JOB_BOARD]**
- **linkedin.com/jobs** - LinkedIn job listings (filter: [YOUR_COUNTRY] / [YOUR_CITY])

Secondary:
- **[YOUR_ADDITIONAL_JOB_BOARD]**

## Query Categories

### Priority 1: [YOUR_PRIMARY_ROLE_TYPE]

```
site:[YOUR_JOB_BOARD] "[YOUR_PRIMARY_JOB_TITLE_1]" "[YOUR_CITY]"
site:linkedin.com/jobs "[YOUR_PRIMARY_JOB_TITLE_1]" "[YOUR_KEY_SKILL]" "[YOUR_CITY]"
site:[YOUR_JOB_BOARD] "[YOUR_PRIMARY_JOB_TITLE_2]" "[YOUR_CITY]"
site:linkedin.com/jobs "[YOUR_PRIMARY_JOB_TITLE_2]" "[YOUR_CITY]"
```

### Priority 2: [YOUR_DOMAIN_EXPERTISE]

```
site:[YOUR_JOB_BOARD] "[YOUR_DOMAIN_KEYWORD_1]" "[YOUR_PRIMARY_JOB_TITLE_1]"
site:linkedin.com/jobs "[YOUR_DOMAIN_KEYWORD_1]" "[YOUR_KEY_SKILL]" "[YOUR_CITY]"
site:[YOUR_JOB_BOARD] "[YOUR_DOMAIN_KEYWORD_2]" "[YOUR_KEY_SKILL]"
```

### Priority 3: [YOUR_ADJACENT_ROLE_TYPE]

```
site:[YOUR_JOB_BOARD] "[YOUR_ADJACENT_TITLE_1]" "[YOUR_CITY]"
site:linkedin.com/jobs "[YOUR_ADJACENT_TITLE_1]" "[YOUR_DOMAIN_KEYWORD_1]"
site:[YOUR_JOB_BOARD] "[YOUR_ADJACENT_TITLE_2]" "[YOUR_KEY_SKILL]"
```

### Priority 4: Broader Technical / Consulting

```
site:[YOUR_JOB_BOARD] "Consultant" "[YOUR_DOMAIN]" "[YOUR_CITY]"
site:linkedin.com/jobs "Technical Consultant" "[YOUR_KEY_SKILL]" "[YOUR_CITY]"
site:[YOUR_JOB_BOARD] "[YOUR_DOMAIN] Specialist"
```

## Location Filter

- Ideal: [YOUR_CITY]
- Acceptable: [ACCEPTABLE_AREA_1], [ACCEPTABLE_AREA_2]
- Borderline: [BORDERLINE_AREA]
- Too far: [TOO_FAR_AREA]

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed.
