# Job Application Assistant for Zhanserik Kara-Murzin

<!-- SETUP: This file is populated by running /setup -->
<!-- After running /setup, all [PLACEHOLDER] tokens will be replaced with your actual information -->

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for Zhanserik Kara-Murzin, helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

<!-- This section is auto-populated by /setup. You can also fill it in manually. -->

### Identity
- **Name:** Zhanserik Kara-Murzin
- **Location:** Toyama, Japan (remote-only; requires visa sponsorship, so scope is Japan-based employers)
- **Languages:** Japanese (Basic), English (B2), Russian (Native), Kazakh (Native)
- **Status:** Employed full-time (Samuray Boeki) + concurrent contract (Kotomoto Consulting)
- **LinkedIn headline:** "PHP Fullstack Developer | Symfony, Laravel, Vue.js"

### Education
- **BSc in Computer Science** (2019-2023) - Almaty Technological University, Kazakhstan (GPA 3.52/4.0)
- **Advanced JavaScript, React, and TypeScript Course** (2023-2024) - Astana Hub, Remote

### Professional Experience
- **PHP Fullstack Developer** (June 2024 - Present) - **Samuray Boeki** (Toyama, Japan)
  - Refactored legacy PHP code into modular components, improving system performance
  - Implemented Redis-based caching to improve API response time
  - Optimized frontend performance with JavaScript and Vue.js
- **PHP Backend Developer (Contract)** (Dec 2025 - Present) - **Kotomoto Consulting** (Remote)
  - Built internal Kanban web system (PHP + REST APIs) serving 50+ users
  - Implemented OCR-based document processing at 95-98% accuracy
  - Designed and maintained PostgreSQL databases for internal tools
- **Database Engineer Intern (FinTech)** (Feb 2023 - May 2023) - **Otbasy Bank** (Almaty, Kazakhstan)
  - PostgreSQL database design, query optimization, data integrity

### Technical Skills
- **Primary:** PHP, Symfony, Laravel, Vue.js, JavaScript, SQL
- **Secondary:** React, TypeScript, AWS, Terraform, Docker
- **Domain:** Backend/API development, database design, fullstack web applications
- **Software:** PostgreSQL, MySQL, Redis, PHPStan, Sentry, Git

### Certifications
- **Advanced JavaScript, React, and TypeScript Course** - Astana Hub - completed 2024

### Publications
- None

### Awards
- None listed

### Behavioral Profile
<!-- No formal assessment - self-described -->
- **Team-oriented** - finds solo work draining, prefers collaborating with a team
- **Adaptive pace** - fast/pragmatic under urgency, deliberate otherwise
- **Strengths:** Adopts new technologies readily, motivated to ship new features
- **Growth areas:** [YOUR_GROWTH_AREAS]
- **Thrives in:** Remote, team-based environments with room to introduce new tools/tech, no weekend work expected

### What Excites You
- Working with new technologies and shipping new features
- Using AI-assisted development tools (e.g. Claude Code) to build faster

### Target Sectors
- Tech/e-commerce: Rakuten, Mercari, PayPay
- Big tech / mobility: Google (Japan), Woven (Woven by Toyota)

### Deal-breakers
- iGaming or Crypto industry
- Non-remote / office-required roles
- Roles outside Japan, requiring relocation, or requiring Japanese language proficiency
- Roles without visa sponsorship

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Job search CLI tools

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`

### ATS & keyword verification (CV)
ATS parsers read the PDF's embedded text layer, not the rendered page. Extract it with `pdftotext -layout` and verify what a parser sees. `pdftotext` (poppler) is optional - if missing, skip the parseability items with a warning and check keyword coverage from the visual PDF read instead.
- [ ] CV text layer extracts cleanly - no `(cid:*)` markers, `�` replacement characters, or text visible in the PDF but absent from the extraction
- [ ] Email and phone appear as **literal text** in the extraction (icon-glyph noise like `MOBILE-ALT`/`Envelope` is harmless, but a contact detail carried only by an icon or hyperlink is invisible to ATS)
- [ ] Reading order of the extracted text matches the visual order (single-column stock template is safe; multi-column custom templates are where this breaks)
- [ ] Posting keywords covered or honestly absent - synonym-only matches tightened to the posting's exact term where truthfully applicable, keywords the profile genuinely supports added to experience bullets, genuine gaps left visible and **never stuffed**
