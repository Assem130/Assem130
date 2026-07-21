# Curiosity Atlas GitHub Profile Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a theme-aware Editorial Cartography profile README for `github.com/Assem130` that presents Assem as a second-year Leiden Data Science & AI student guided by technical curiosity.

**Architecture:** A public GitHub profile repository named `Assem130` contains one `README.md` and two static SVG assets. GitHub's `<picture>` element switches the banner between light and dark themes; all essential content remains in native Markdown below it.

**Tech Stack:** GitHub Flavored Markdown, static SVG 1.1, Git, GitHub CLI, PowerShell validation.

## Global Constraints

- Use exactly three presentation files: `README.md`, `assets/atlas-light.svg`, and `assets/atlas-dark.svg`.
- Add no runtime dependency, external image service, generated statistic, CSS, JavaScript, iframe, workflow, or GitHub Action.
- Do not use badges, typing animations, visitor counters, trophies, streaks, technology walls, or excessive icons.
- Present Assem as a Data Science & AI student at Leiden University entering year two; do not claim that he is already an engineer, specialist, or product builder.
- Keep the four branches exactly: Machine Intelligence, Data & Inference, Autonomous Systems, and Human-AI Interaction.
- Keep Arabic language and culture out of the profile's identity and visual theme.
- Use no unsupported security claim for `AutoULCN-Firefox`.
- Essential information must remain readable without the SVG banner.
- Do not modify unrelated repositories, the avatar, or private contact information.

---

## File Map

- `assets/atlas-light.svg` — warm-paper Editorial Cartography banner for GitHub light themes.
- `assets/atlas-dark.svg` — dark Editorial Cartography banner with identical geometry and content.
- `README.md` — theme selection, factual introduction, four technical trails, three current questions, and two cautiously described public repositories.
- `docs/superpowers/specs/2026-07-21-curiosity-atlas-profile-design.md` — approved design source; no implementation edits expected.
- `docs/superpowers/plans/2026-07-21-curiosity-atlas-profile.md` — this implementation plan.

### Task 1: Create and validate the theme-aware atlas assets

**Files:**
- Create: `assets/atlas-light.svg`
- Create: `assets/atlas-dark.svg`

**Interfaces:**
- Consumes: the approved Editorial Cartography colors, copy, and four trail names.
- Produces: two SVG files with identical `viewBox="0 0 1200 390"` geometry for use by `README.md`.

- [ ] **Step 1: Create the light-theme SVG**

Create `assets/atlas-light.svg` with exactly this content:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 390" role="img" aria-labelledby="title description">
  <title id="title">Assem's Curiosity Atlas</title>
  <desc id="description">A route connecting machine intelligence, data and inference, autonomous systems, and human-AI interaction.</desc>
  <rect width="1200" height="390" fill="#f5f0e6"/>
  <path d="M-40 295C145 55 335 360 545 157S910 67 1240 282" fill="none" stroke="#ed4b2f" stroke-width="16"/>
  <g fill="#1447d5" stroke="#f5f0e6" stroke-width="5">
    <circle cx="169" cy="153" r="13"/>
    <circle cx="432" cy="243" r="13"/>
    <circle cx="714" cy="94" r="13"/>
    <circle cx="1008" cy="180" r="13"/>
  </g>
  <g font-family="Arial, Helvetica, sans-serif" fill="#181818">
    <text x="38" y="42" font-size="13" letter-spacing="3">ASSEM / CURIOSITY ATLAS</text>
    <text x="38" y="110" font-size="58" font-weight="700">FOLLOW THE QUESTION.</text>
    <text x="169" y="133" font-size="12" text-anchor="middle">01 / MACHINE INTELLIGENCE</text>
    <text x="432" y="277" font-size="12" text-anchor="middle">02 / DATA &amp; INFERENCE</text>
    <text x="714" y="74" font-size="12" text-anchor="middle">03 / AUTONOMOUS SYSTEMS</text>
    <text x="1008" y="214" font-size="12" text-anchor="middle">04 / HUMAN-AI INTERACTION</text>
    <text x="38" y="354" font-size="11" letter-spacing="2">LEIDEN / YEAR 02 / FOUR ACTIVE TRAILS</text>
    <text x="1162" y="354" font-size="11" text-anchor="end">52.1601 N / 4.4970 E</text>
  </g>
</svg>
```

- [ ] **Step 2: Create the dark-theme SVG**

Create `assets/atlas-dark.svg` with exactly this content:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 390" role="img" aria-labelledby="title description">
  <title id="title">Assem's Curiosity Atlas</title>
  <desc id="description">A route connecting machine intelligence, data and inference, autonomous systems, and human-AI interaction.</desc>
  <rect width="1200" height="390" fill="#11110f"/>
  <path d="M-40 295C145 55 335 360 545 157S910 67 1240 282" fill="none" stroke="#ff6745" stroke-width="16"/>
  <g fill="#8ca2ff" stroke="#11110f" stroke-width="5">
    <circle cx="169" cy="153" r="13"/>
    <circle cx="432" cy="243" r="13"/>
    <circle cx="714" cy="94" r="13"/>
    <circle cx="1008" cy="180" r="13"/>
  </g>
  <g font-family="Arial, Helvetica, sans-serif" fill="#f3ecdc">
    <text x="38" y="42" font-size="13" letter-spacing="3">ASSEM / CURIOSITY ATLAS</text>
    <text x="38" y="110" font-size="58" font-weight="700">FOLLOW THE QUESTION.</text>
    <text x="169" y="133" font-size="12" text-anchor="middle">01 / MACHINE INTELLIGENCE</text>
    <text x="432" y="277" font-size="12" text-anchor="middle">02 / DATA &amp; INFERENCE</text>
    <text x="714" y="74" font-size="12" text-anchor="middle">03 / AUTONOMOUS SYSTEMS</text>
    <text x="1008" y="214" font-size="12" text-anchor="middle">04 / HUMAN-AI INTERACTION</text>
    <text x="38" y="354" font-size="11" letter-spacing="2">LEIDEN / YEAR 02 / FOUR ACTIVE TRAILS</text>
    <text x="1162" y="354" font-size="11" text-anchor="end">52.1601 N / 4.4970 E</text>
  </g>
</svg>
```

- [ ] **Step 3: Validate both SVG files**

Run:

```powershell
$files = 'assets/atlas-light.svg','assets/atlas-dark.svg'
$documents = $files | ForEach-Object { [xml](Get-Content -Raw $_) }
if (($documents.DocumentElement.viewBox | Select-Object -Unique).Count -ne 1) { throw 'SVG viewBoxes differ' }
if (Select-String -Path $files -Pattern '<script|<animate|https?://' -Quiet) { throw 'SVG contains forbidden dynamic or remote content' }
'SVG validation passed'
```

Expected: `SVG validation passed`.

- [ ] **Step 4: Inspect both renderings**

Open both local SVG files with the image-viewing tool at original detail. Confirm that all four labels fit inside the canvas, the route is visible, text has strong contrast, and no element is clipped.

- [ ] **Step 5: Commit the assets**

Run:

```powershell
git add assets/atlas-light.svg assets/atlas-dark.svg
git commit -m "feat: add Curiosity Atlas artwork"
```

Expected: one commit creating both assets.

### Task 2: Create and validate the profile README

**Files:**
- Create: `README.md`
- Read: `assets/atlas-light.svg`
- Read: `assets/atlas-dark.svg`

**Interfaces:**
- Consumes: `assets/atlas-light.svg` and `assets/atlas-dark.svg` through relative paths.
- Produces: the complete GitHub profile surface shown above native pinned repositories.

- [ ] **Step 1: Write the README**

Create `README.md` with exactly this content:

```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/atlas-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/atlas-light.svg">
  <img alt="Assem's Curiosity Atlas connecting machine intelligence, data and inference, autonomous systems, and human-AI interaction." src="assets/atlas-light.svg">
</picture>

**Data Science & AI student at Leiden University, entering year two.**  
Interested in how intelligent systems learn, reason, act, and meet the people using them.

## `01 / CURRENT COORDINATES`

| Active trail | Following |
| --- | --- |
| **Machine intelligence** | Models, reasoning, learning, adaptation. |
| **Data & inference** | Patterns, uncertainty, evidence, explanation. |
| **Autonomous systems** | Agents, decisions, algorithms, feedback. |
| **Human-AI interaction** | Cognition, interfaces, usefulness, trust. |

## `02 / QUESTIONS IN MOTION`

↗ When should an intelligent system explain itself?  
↗ What separates useful autonomy from unnecessary automation?  
↗ How do people calibrate trust in imperfect models?

## `03 / FIELD NOTES`

### [Structured learning interface](https://github.com/Assem130/arabic-word-of-the-day)

Exploring structured content, browser state, and human-centred interface decisions.

### [University authentication automation](https://github.com/Assem130/AutoULCN-Firefox)

A public fork exploring browser and scripting approaches to a repetitive university login flow.

---

*Following questions, not a fixed destination.*
```

- [ ] **Step 2: Run structural checks**

Run:

```powershell
$readme = Get-Content -Raw README.md
$required = 'assets/atlas-dark.svg','assets/atlas-light.svg','Machine intelligence','Data & inference','Autonomous systems','Human-AI interaction','Leiden University','entering year two'
$missing = $required | Where-Object { -not $readme.Contains($_) }
if ($missing) { throw "README missing: $($missing -join ', ')" }
if ($readme -match 'shields\.io|github-readme-stats|visitor|typing-svg|trophy') { throw 'README contains a forbidden profile widget' }
if (-not (Test-Path assets/atlas-light.svg) -or -not (Test-Path assets/atlas-dark.svg)) { throw 'README asset missing' }
'README validation passed'
```

Expected: `README validation passed`.

- [ ] **Step 3: Verify links without mutating GitHub**

Run:

```powershell
$urls = Select-String -Path README.md -Pattern 'https://github\.com/Assem130/[^)]+' -AllMatches | ForEach-Object Matches | ForEach-Object Value
if ($urls.Count -ne 2) { throw "Expected 2 repository links, found $($urls.Count)" }
$urls
```

Expected: exactly the two `Assem130` repository URLs.

- [ ] **Step 4: Review the rendered hierarchy**

Preview `README.md` with a GitHub-compatible renderer or a temporary GitHub draft. Confirm the SVG appears first, the factual position is visible without scrolling, the table is readable at narrow width, and the questions and field notes remain concise.

- [ ] **Step 5: Commit the README**

Run:

```powershell
git add README.md
git commit -m "feat: add Curiosity Atlas profile README"
```

Expected: one commit creating `README.md`.

### Task 3: Publish and verify the live profile

**Files:**
- Read: `README.md`
- Read: `assets/atlas-light.svg`
- Read: `assets/atlas-dark.svg`

**Interfaces:**
- Consumes: the committed local repository and authenticated GitHub CLI session.
- Produces: public repository `https://github.com/Assem130/Assem130` and a visible GitHub profile README at `https://github.com/Assem130`.

- [ ] **Step 1: Confirm the local repository is clean**

Run:

```powershell
git status --short
git log --oneline -3
```

Expected: no status output. Recent history includes the design spec, implementation plan, atlas artwork, and profile README commits.

- [ ] **Step 2: Confirm GitHub authentication and remote absence**

Run:

```powershell
gh auth status
gh repo view Assem130/Assem130 --json nameWithOwner,visibility,defaultBranchRef
```

Expected: authentication as `Assem130`; `gh repo view` reports that the repository does not exist. If it exists, stop before pushing and inspect its branches and files so no remote content is overwritten.

- [ ] **Step 3: Rename the local branch and create the profile repository**

Run:

```powershell
git branch -M main
gh repo create Assem130/Assem130 --public --source=. --remote=origin --push --description "Curiosity Atlas — Data Science & AI at Leiden University"
```

Expected: the public repository is created, `origin` points to it, and `main` is pushed.

- [ ] **Step 4: Verify the remote contents**

Run:

```powershell
gh repo view Assem130/Assem130 --json nameWithOwner,visibility,defaultBranchRef,url
gh api repos/Assem130/Assem130/contents/README.md --jq '.name + " " + .sha'
gh api repos/Assem130/Assem130/contents/assets/atlas-light.svg --jq '.name + " " + .sha'
gh api repos/Assem130/Assem130/contents/assets/atlas-dark.svg --jq '.name + " " + .sha'
```

Expected: public `Assem130/Assem130`, default branch `main`, and all three presentation files present.

- [ ] **Step 5: Perform live browser QA**

Open `https://github.com/Assem130` in the user's browser and verify the live page rather than relying only on API output:

1. The profile README appears above pinned repositories.
2. The dark banner loads in dark mode and the light banner loads in light mode.
3. All headline and node text is legible at desktop width.
4. At mobile width, the SVG scales without clipping and the Markdown table remains usable.
5. Both field-note links navigate to the intended repositories.
6. No badge, statistics widget, broken image, or unsupported HTML appears.

- [ ] **Step 6: Record final verification**

Run:

```powershell
git status --short
git log --oneline -4
```

Expected: clean working tree with the design, plan, artwork, and README commits visible.
