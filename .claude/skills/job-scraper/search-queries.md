# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Search Sites

**Note:** The built-in job-scraper CLI tools in this framework target Danish portals (Jobindex, Jobbank, etc.) and do not apply here. Zhanserik is based in Japan and needs Japan-based, visa-sponsoring employers. Until a dedicated portal integration exists (see `/add-portal`), use Google `site:` searches and manual LinkedIn searches against these sites:

Primary (Japan job market):
- **linkedin.com/jobs** - filter: Japan, Remote
- **indeed.com** (Japan) - broad coverage, filter remote + visa sponsorship mentions
- **japan-dev.com** - English-friendly tech jobs in Japan, has remote/visa filters
- **daijob.com** - bilingual/foreign-friendly jobs in Japan

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for target companies (Rakuten, Mercari, PayPay, Google, Woven)

## Query Categories

Queries are grouped by priority. All roles must be **remote** and at a **Japan-based employer offering visa sponsorship** - filter out office-required, non-Japan, or Japanese-language-required postings regardless of category.

### Priority 1: Backend / PHP-Symfony Developer

Strongest and most desired career direction.

```
site:japan-dev.com "PHP" "Symfony" remote
site:linkedin.com/jobs "PHP Developer" Japan remote visa sponsorship
site:indeed.com "Symfony" OR "Laravel" developer Japan remote
```

### Priority 2: Fullstack / Web Developer

Matches core fullstack experience (PHP + Vue.js).

```
site:japan-dev.com "fullstack" OR "full stack" developer remote
site:linkedin.com/jobs "Web Developer" Japan remote visa sponsorship
site:daijob.com "fullstack developer" remote
```

### Priority 3: Frontend / Software Engineer

Adjacent roles to pivot into.

```
site:japan-dev.com "frontend" Vue.js OR React remote
site:linkedin.com/jobs "Software Engineer" Japan remote visa sponsorship
```

### Priority 4: Broader Technical

Wider net.

```
site:japan-dev.com PHP OR Symfony OR Vue.js remote visa
site:indeed.com "software engineer" remote Japan visa sponsorship
```

## Location Filter

Remote-only, Japan-based employer (for visa sponsorship). No commute distance applies:
- **Acceptable:** Fully remote, employer legally based in Japan, sponsors work visas, no Japanese language requirement
- **Too far / exclude:** Office-required roles, non-Japan employers, roles requiring Japanese proficiency, roles that don't sponsor visas

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
