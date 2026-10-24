# AI Gurukul RJ777 — Master Prompt

Build a complete, offline, mobile-ready learning portal in one pass — and reuse the same prompt for any subject.

**Developed by Ravindra Jain** · *Learn, share, innovate — build together with AI*

## How to use this document

This document holds two prompts.

**Part A — the AI Gurukul RJ777 master prompt** rebuilds this AI learning portal: a single offline HTML file that teaches AI vocabulary, concepts, building and leadership, and coaches the learner every day.

**Part B — the universal master prompt** is the same blueprint with the subject, audience and goals turned into variables. Fill in the variable block and it produces a learning portal on any topic — cybersecurity, cloud, ITIL, data analytics, project management, or a team's own runbooks.

To use either prompt:

1. Paste the whole prompt into Claude (Opus or Sonnet recommended), in a chat or project with file creation turned on.
2. For Part B, fill in every `{{VARIABLE}}` first. Leave a line as `default` to accept the suggested value.
3. Let it build in stages: it will profile the topic, restate the plan, build, then test. Answer its single clarifying question if it asks one.
4. Use the follow-up prompts in Part C to extend it, one feature per message.
5. Check the result against the definition of done before sharing it.

> Tip: keep this Word document for reading and circulation, and the companion `.md` file for copying — markdown pastes cleanly into any AI chat.

## Part A — The AI Gurukul RJ777 master prompt

```
You are building AI GURUKUL RJ777 — an AI Learning Atlas: a single-file, offline,
mobile-ready learning portal that coaches an experienced IT professional (15+ years)
from AI fundamentals to building agents, leading AI initiatives and passing Claude
certifications.

1 · HARD CONSTRAINTS (override everything below)
- One self-contained index.html: all CSS, JS and data inline. No frameworks, no CDN
  dependencies except optional web fonts, no build step for the user.
- Works offline after first load (service worker sw.js, network-first for the page,
  cache-first for assets) and installs on phones (manifest.webmanifest + 192/512 icons).
- No backend, no login, no keys. Progress saves to localStorage under one key, with an
  in-memory fallback when storage is blocked. Export/Import progress as JSON.
- Never use innerHTML with untrusted text: escape everything. Only https links, opened
  with rel="noopener noreferrer" and referrerpolicy="no-referrer".
- Plain English, British spelling, no marketing tone. Every factual claim about
  products, prices or certifications is marked time-sensitive with a
  "verified <month>" badge.
- WCAG AA: text >= 4.5:1 in every theme, visible focus, keyboard operable, touch
  targets >= 40px on touch screens, no horizontal scroll at 320px.
- Credit: footer "AI Gurukul RJ777 — Developed by Ravindra Jain · © 2026" on every
  screen, plus a name tag at the top of every page; an
  About page with the full credit note, contact email (assembled at runtime, never
  plain in the source), licence CC BY-NC-SA 4.0 in plain English and a copyable
  attribution line; copyright comment, meta author and JSON-LD author in the file.

2 · THE DATA (all content as JS data arrays, rendered by one engine)
- DOMAINS (13): fundamentals, architecture, tokens, training, models, prompting,
  retrieval, agents, LLMOps, safety, roles, code, strategy & leadership.
- TERMS (~240): {id, t (name), d (domain), lv (1-3), s (one-line definition),
  a (analogy), x (example), dd (deep dive), say ("in a meeting" line),
  iq/ia (interview question/answer), r (related ids), f (flow id)}.
- FLOWS (~15): SVG step-by-step diagrams {nodes with x/y and linked term, edges,
  groups, steps with narration}: inference, RAG, agent loop, MCP, training, evals,
  orchestration, LSTM cell, AI initiative lifecycle, full-stack app, AIOps loop.
- GUIDES (~55) in groups: Understand, Build, Connect, Ship & secure, Careers & skills,
  AIOps track, App workshop, Projects. Blocks: p, steps (with remark + term chips),
  table, code (lang, caption, copy button, "run-tested" or "syntax-checked" label),
  flow embed, tip, download.
- LEAD sections (~11): starting point for experienced IT staff, initiative lifecycle,
  use-case discovery, business impact, building solutions, leading with confidence,
  governance toolkit, leadership preparation, 20+ real case studies (sourced, with
  lesson, leader takeaway, interview use), mock interviews, career guidance.
- SCENARIOS (~60 quiz questions), CERTS (Claude certification term maps), ROADMAP
  (5 phases of tasks), PATHS (6 guided paths), NEWS snapshot + official newsrooms.

3 · RULES AS DATA
- Spaced repetition: boxes 1-6, intervals 0,1,3,7,16,35,90 days. Again -> box 1
  (tomorrow); Good -> +1 box (a new card's first Good -> box 2, 3 days); Easy -> +2.
  "Known" = box >= 2. Wrong quiz answers send that term to tomorrow's review.
- Daily session = due cards (max 12) + up to 5 new cards from the active path + 1
  scenario question. Path steps auto-complete: terms when all known, guides and lead
  sections when marked complete, flows when walked to the last step, quizzes >= 70%.
- Section hues rotate 1,6,4,7,5,3,8,2,9,11,12,10 through 12 category colours.

4 · SECTIONS TO BUILD, in this order
Five areas with a second-row section bar:
- TODAY: Today (greeting, streak, session runner with flip + Again/Good/Easy and
  next-interval hints, path next step, notes, backup reminder, freshness list,
  what's new) · Paths (6 paths, step lists with status) · Latest in AI.
- LEARN: Atlas (layered stack + start-here story) · Map (mind map by domain) ·
  Cheat sheet · Flows (play, step, narration, tap nodes to open terms).
- PRACTISE: Flashcards (filters, path decks, swipe, keys) · Quiz (definitions,
  scenarios, mixed; history) · link to Mock interviews.
- BUILD: Build lab (grouped list + guide stage, prev/next, mark complete).
- GROW: Lead (with interactive use-case scorer on a value x feasibility matrix, ROI
  calculator with conservative/expected/optimistic cases, leadership self-assessment,
  case-study browser with filters, mock-interview trainer with 2-minute timer and a
  "copy grade-my-answer prompt" button) · Certification readiness · Roadmap.
Global: search everything (terms, guides, lead, cases, interview questions, flows,
paths, news, personal notes); a drill-down drawer for every term with notes box,
review status and freshness badge; theme picker; export/import/reset menu.

5 · INTERACTION CONTRACT
- Tapping any term anywhere opens its drill-down. Related terms, guides and lead
  sections cross-link both ways.
- The app resumes the last view, card, guide and lead section.
- Latest in AI: a Refresh button fetches, in parallel with 10s timeouts and no
  credentials, from browser-accessible public APIs only — Hacker News (Algolia),
  Hugging Face daily papers and trending models, GitHub repository search. No
  proxies. De-duplicate by URL and title. "Trusted sources only" toggle with a domain
  allow-list. Trend radar from headline keywords linked to terms. Results cached;
  offline shows saved results with a warning.

6 · DESIGN SYSTEM
- 13 themes as CSS-variable contracts (39 tokens: surfaces, borders, text x3,
  accents, signals, radii, shadows, fonts, display type, motion) plus --on-a1,
  --a1-ink and a 12-hue category palette tuned per theme (bright on dark, deep on
  light, purples-and-greys only for Accenture themes).
- Separation: page ground vs panel luminance ratio >= 1.15; nested panels step up a
  surface level.
- Colour coding: each domain, tab, guide group and path has a hue; inside long
  panels each section has its own hue across heading chip, table edge, header row,
  alternating rows, first-column names (ink = 85% hue + 15% text), step numbers
  and callouts.
- Mobile: five area tabs fit at 360px; compact header; search icon expands on tap.

7 · TRAPS ALREADY PAID FOR (avoid them)
| Symptom | Fix |
| Script stops when data contains </script> | Escape "</script" and "<!--" in data |
| Path terms never complete on day one | First "Good" on a new card must go to box 2 |
| Search icon swallows taps on phones | pointer-events:none on the icon |
| Colour coding silently overridden | Put coding CSS after component CSS |
| Theme switch reads wrong colours in tests | Wait for the transition before measuring |
| Duplicate news stories | De-duplicate by URL and normalised title |
| Coloured names unreadable on tinted rows | Use the 85% hue + 15% text ink |
| Header tabs overflow at 1280px | Group into five areas with a section row |

8 · WORKING METHOD
Restate the plan in 10 lines. Build the data model and engine first, then views in
the order of section 4, then design and colour, then Latest in AI. After each stage,
run it in a headless browser: no console errors, every view renders, storage
round-trips, phone width 390px has no horizontal scroll. Report what you tested and
what you could not test (for example live APIs without network).

9 · DEFINITION OF DONE
[ ] Single index.html opens offline; installs on Android and iPhone
[ ] Every term, flow, guide, lead section and path reference resolves
[ ] Daily session, paths, search, notes, export/import all work after reload
[ ] All 13 themes pass separation and contrast checks
[ ] Zero console errors on desktop and phone; no tap target < 40px on touch
[ ] Latest in AI handles success, partial failure, offline, and hostile links
Do not claim it works before every box is ticked.
```

### Why the prompt is shaped this way

- **Constraints first**, because they override everything and are the most expensive to fix later (single file, offline, no backend, accessibility).
- **Content as data** — one engine renders every term, guide and path, so adding a topic means adding data, not code.
- **Rules as numbers** — intervals, thresholds and rotation orders are stated exactly, so the result behaves predictably.
- **A traps table** — each row is a real bug from building the original; telling the model up front saves a round of fixing.
- **A definition of done** with checkboxes gives the model, and you, something concrete to verify against.

## Part B — The universal master prompt

Fill in the variable block, then paste the whole prompt. Every `{{VARIABLE}}` is used somewhere in the prompt body.

### The variables

| Variable | What to write | Example |
|---|---|---|
| `{{PORTAL_NAME}}` | A short, memorable name | Sentinel |
| `{{SUBJECT}}` | The field or topic | Cybersecurity operations |
| `{{AUDIENCE}}` | Who learns, and their starting level | SOC analysts, 2–10 years in IT |
| `{{OUTCOMES}}` | 3–5 things learners will be able to do | Triage alerts, write detection rules, lead incident response |
| `{{CERTIFICATION}}` | Exam or credential to map to, or `none` | CompTIA Security+ |
| `{{DOMAINS}}` | 6–13 knowledge areas | Threats, network security, identity, SIEM, incident response… |
| `{{TERM_COUNT}}` | How many terms | 150 |
| `{{FLOWS}}` | 6–12 processes to animate | Incident response lifecycle, phishing kill chain, SIEM pipeline |
| `{{HANDS_ON}}` | Labs or projects, and their technology | Write Sigma rules; build a phishing triage script in Python |
| `{{LEADERSHIP}}` | Include a leadership and career section? `yes` / `no` | yes |
| `{{CASE_STUDIES}}` | Number and kind of real cases | 15 public breaches with lessons |
| `{{PATHS}}` | Guided paths to offer | Foundations; Analyst; Detection engineer; Certification |
| `{{NEWS_SOURCES}}` | Live feeds or official sites for "Latest" | CISA advisories, vendor security blogs, Hacker News "security" |
| `{{BRAND}}` | Theme set or brand rules | Accenture Light and Dark plus 4 general themes |
| `{{LANGUAGE}}` | Language and spelling | English (UK) |
| `{{TIME_PER_DAY}}` | Daily study time to design for | 10 minutes |
| `{{AUTHOR_CREDIT}}` | Your credit line, licence and contact for the About page | Developed by Ravindra Jain · CC BY-NC-SA 4.0 · email on About page |

### The prompt

```
You are building {{PORTAL_NAME}} — a single-file, offline, mobile-ready learning portal
that coaches {{AUDIENCE}} in {{SUBJECT}} every day, so that they can: {{OUTCOMES}}.

1 · HARD CONSTRAINTS
- One self-contained index.html (inline CSS, JS, data); no frameworks or backend;
  offline via sw.js; installable via manifest.webmanifest and two icons.
- Progress in localStorage (one key, in-memory fallback), with Export/Import JSON.
- Escape all text; https-only links with noopener/noreferrer.
- Written in {{LANGUAGE}}, plain and practical. Time-sensitive facts carry a
  "verified <month>" badge. WCAG AA in every theme; touch targets >= 40px.
- Credit: {{AUTHOR_CREDIT}} — the name in the footer of every screen; full details,
  licence and a copyable attribution line on one About page; author in file metadata.

2 · CONTENT AS DATA
- DOMAINS: {{DOMAINS}}.
- About {{TERM_COUNT}} TERMS, each with: definition, analogy, example, deep dive,
  "say it in a meeting" line, interview question and answer, related terms, level 1-3.
- FLOWS (animated step-by-step SVG diagrams): {{FLOWS}}.
- GUIDES grouped Understand / Build / Practise-at-work / Projects, with steps, tables,
  code or command blocks labelled "tested" or "untested", and term chips.
  Hands-on content: {{HANDS_ON}}.
- If {{LEADERSHIP}} = yes: a Lead area with use-case discovery, business-impact
  calculator, leading change, a self-assessment, {{CASE_STUDIES}} (each sourced, with
  lesson and interview use), mock interviews with a timer and grading prompt, and
  career guidance for {{AUDIENCE}}.
- QUIZ: about 60 scenario questions linked to terms. CERTIFICATION map:
  {{CERTIFICATION}} (skip if none). ROADMAP: 4-5 phases of tasks.
- PATHS: {{PATHS}} — ordered steps of term sets, guides, flows and checkpoint quizzes.

3 · RULES
- Spaced repetition boxes 1-6, intervals 0,1,3,7,16,35,90 days; Again -> tomorrow;
  a new card's first Good -> 3 days; Easy skips a box; known = box >= 2.
- Daily session sized for {{TIME_PER_DAY}}: due cards + up to 5 new from the active
  path + 1 scenario question. Path steps tick themselves off.

4 · SECTIONS (five areas, each with a section row)
Today (session, paths, latest) · Learn (atlas, map, cheat sheet, flows) ·
Practise (flashcards, quiz, mock interviews) · Build (guides and projects) ·
Grow (lead if enabled, certification, roadmap). Global search across everything
including personal notes; a drill-down drawer for every term with a notes box.

5 · LATEST
A Refresh button that fetches from browser-accessible public APIs or feeds only
({{NEWS_SOURCES}}), with timeouts, no credentials, no proxies, de-duplication, a
trusted-domain toggle, a trend radar linking headlines to terms, cached results for
offline, plus a dated snapshot and a list of official sources.

6 · DESIGN
Themes: {{BRAND}}. Each theme is a CSS-variable contract with a 12-hue category
palette. Page ground and panels visibly separated (luminance ratio >= 1.15). Every
domain, area, guide group and path has a hue; inside long panels each section gets
its own hue across heading, table header, alternating rows, first-column names
(85% hue + 15% text) and callouts.

7 · TRAPS TO AVOID
Escape "</script" in embedded data. A new card's first Good must count as learned.
Put colour-coding CSS after component CSS. Make search icons ignore taps.
De-duplicate feed items by URL and title. Test colours only after theme transitions.

8 · METHOD
Restate the plan in 10 lines, then ask at most one clarifying question. Build data
and engine, then views, then design, then Latest. Test each stage in a headless
browser at desktop and 390px phone width. Report what was and wasn't tested.

9 · DONE WHEN
Offline and installable; every reference resolves; session, paths, search, notes and
export/import survive a reload; all themes pass contrast; no console errors; Latest
handles success, partial failure, offline and hostile links. Don't claim it works
before all of these pass.
```

### Worked examples — variable sets for other subjects

Each row shows values for `{{AUDIENCE}}`, `{{DOMAINS}}`, `{{CERTIFICATION}}` and `{{HANDS_ON}}`.

| Subject | Audience | Domains (sample) | Certification | Hands-on |
|---|---|---|---|---|
| Cybersecurity operations | SOC analysts | Threats, identity, network, SIEM, detection, incident response, cloud security | CompTIA Security+ | Sigma rules, log triage scripts |
| Cloud architecture | Infrastructure engineers | Compute, storage, networking, IAM, cost, resilience, IaC | AWS Solutions Architect – Associate | Terraform labs, a three-tier deployment |
| IT service management | Service desk and NOC staff | Service value system, incident, problem, change, SLAs, CMDB, continual improvement | ITIL 4 Foundation | Write a major-incident runbook; design an SLA dashboard |
| Data analytics | Analysts moving from Excel | Data types, SQL, pandas, visualisation, statistics, storytelling | Microsoft PL-300 | SQL exercises, a pandas notebook, a dashboard |
| Networking | Junior network engineers | OSI, IP and subnetting, routing, switching, wireless, security, automation | Cisco CCNA | Subnetting drills, Python network automation |
| Project management | Team leads | Scope, schedule, cost, risk, stakeholders, agile, governance | PMP | A project charter, a risk register |
| Team onboarding | New joiners in one team | Our systems, tools, runbooks, escalation, culture | none | Shadow-a-shift checklist, first-week tasks |

> Tip: for onboarding or internal topics, paste your team's runbooks or wiki pages after the prompt and add: "Build TERMS and GUIDES only from the attached material; mark anything not in it as [to verify]."

## Part C — Follow-up prompts

Use one per message once the first build works.

| Goal | Prompt |
|---|---|
| Add a topic | Add 15 terms on `<topic>` to the `<domain>` domain with every field filled, link them to existing terms, and add them to the `<path>` path. |
| Add a flow | Add an animated flow showing `<process>` in 6–8 steps, with each node linked to a term, and embed it in the `<guide>` guide. |
| Add a guide | Add a Build-lab guide on `<task>` with steps, one table, one code block and term chips. Label the code as untested unless you ran it. |
| Add case studies | Add 5 real, publicly reported case studies on `<theme>`, each with a source, lesson, leader takeaway and interview use. Don't invent figures. |
| Refresh facts | List every item marked time-sensitive, check each against current official sources, and update the ones that changed with a new verified date. |
| Re-theme | Add a theme matching `<brand>` rules, keep all contrast checks passing, and show it in the theme picker. |
| Audit | Review the whole portal for broken references, contrast failures, touch targets under 40px and console errors at 390px and 1440px. Fix and report. |

## Part D — Checklist before sharing

- [ ] Opens from `index.html` with no internet after the first visit
- [ ] Installs on a phone and keeps progress after closing
- [ ] Today session, paths, search and notes work, and survive a reload
- [ ] Export, then Import on another browser, restores progress
- [ ] Every theme is readable; sections inside panels show different colours
- [ ] No console errors on desktop or phone
- [ ] Time-sensitive facts carry a verified date; code blocks are labelled
- [ ] Public hosting reviewed for personal or confidential content
- [ ] Author credit in the footer, About page and file metadata; licence file in the repository

## Credits and licence

**Developed by Ravindra Jain.**
*Learn, share, innovate — build together with AI.* Thank you.

© 2026 Ravindra Jain. This document is licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/). You may share and adapt it for non-commercial purposes with credit to "Ravindra Jain", sharing adaptations under the same licence.

