# Curiosity Atlas GitHub Profile Design

## Goal

Create a distinctive GitHub profile for Assem that communicates, within five seconds, that he is a Data Science & Artificial Intelligence student at Leiden University entering his second year. The profile should frame his breadth as disciplined technical curiosity rather than indecision or product-building ambition.

The profile must remain credible to employers and developers while avoiding common profile-README conventions: badge walls, generic statistics, typing animations, visitor counters, excessive icons, and long technology inventories.

## Audience

- Employers evaluating technical direction, judgment, and communication.
- Developers evaluating interests, public work, and intellectual seriousness.
- Peers who may want to discuss or collaborate on related technical questions.

## Core Concept

The profile is a **Curiosity Atlas** presented through an **Editorial Cartography** visual system. A single route crosses four active technical trails:

1. Machine Intelligence — models, reasoning, learning, and adaptation.
2. Data & Inference — patterns, uncertainty, evidence, and explanation.
3. Autonomous Systems — agents, decisions, algorithms, and feedback.
4. Human–AI Interaction — cognition, interfaces, usefulness, and trust.

The route represents an evolving course of inquiry, not a fixed career destination. Arabic language or culture will not be used as a profile theme.

## Opening Message

The profile opens with this factual positioning:

> **Data Science & AI student at Leiden University, entering year two.**  
> Interested in how intelligent systems learn, reason, act, and meet the people using them.

The hero artwork uses the line **“Follow the question.”** It avoids claims that Assem is primarily a builder, engineer, or finished specialist.

## Visual System

The signature visual is a wide, static SVG banner stored in the profile repository.

- Light theme: warm paper background, near-black typography, vermilion route, cobalt nodes.
- Dark theme: near-black background, warm-cream typography, coral route, periwinkle nodes.
- Typography: large system sans-serif headline with small monospaced-style labels rendered using SVG-safe system font stacks.
- Composition: asymmetrical route, four labelled stops, substantial negative space, and small cartographic metadata.
- Metadata: `ASSEM / CURIOSITY ATLAS`, `LEIDEN / YEAR 02 / FOUR ACTIVE TRAILS`, and Leiden coordinates.
- Motion: none. The artwork remains crisp, fast, accessible, and compatible with GitHub rendering.

GitHub's `<picture>` element selects `assets/atlas-dark.svg` or `assets/atlas-light.svg` according to the visitor's theme. The image includes meaningful alt text, and all essential information is repeated as readable Markdown below it.

## README Structure

### Hero

The theme-aware Curiosity Atlas SVG appears first, followed immediately by the two-line opening message.

### 01 / Current Coordinates

A compact two-column Markdown table presents the four active trails. Each description is one short phrase. On narrow screens, GitHub handles the table within the available width; no custom CSS or scripts are used.

### 02 / Questions in Motion

Three manually maintained questions provide the living element:

- When should an intelligent system explain itself?
- What separates useful autonomy from unnecessary automation?
- How do people calibrate trust in imperfect models?

These questions may be replaced later as Assem's studies evolve, but version one uses exactly this set.

### 03 / Field Notes

Two concise repository annotations connect curiosity to public evidence:

- `arabic-word-of-the-day`: described technically as an exploration of structured content, browser state, and human-centred interface decisions. It is not used to frame Assem's identity around Arabic language or culture.
- `AutoULCN-Firefox`: described cautiously as an exploration of browser automation for a repetitive university login flow. The profile will not claim that it is a security product or independently secure.

Each annotation includes one direct repository link and no technology badges. GitHub's native pinned repositories remain the primary portfolio surface below the README.

### Contact

Version one includes only Assem's GitHub identity and Leiden affiliation. No email, LinkedIn, or personal-site link is added without an explicitly supplied public URL.

## GitHub-Native Implementation

The public profile repository must be named exactly `Assem130` under the `Assem130` account. Its presentation files are deliberately minimal:

- `README.md`
- `assets/atlas-light.svg`
- `assets/atlas-dark.svg`

The design uses GitHub Flavored Markdown, a `<picture>` element, relative asset paths, and static SVG only. It adds no runtime dependencies, external image services, generated statistics, custom CSS, JavaScript, iframe, scheduled workflow, or GitHub Action.

## Reliability and Accessibility

- Essential profile information remains readable if either SVG fails to load.
- The banner receives descriptive alt text rather than decorative placeholder text.
- Both themes maintain strong text/background contrast.
- The SVGs use no external fonts, scripts, animation, remote images, or filters that depend on browser-specific behavior.
- Relative asset paths keep previews and branches portable.
- Repository descriptions are checked against the live public repositories before publication.

## Verification

Before publishing:

1. Validate both SVG files as XML and confirm their declared view boxes match.
2. Render both SVGs locally and inspect them at desktop and narrow widths.
3. Preview `README.md` using GitHub-compatible rendering.
4. Verify light- and dark-theme `<picture>` selection.
5. Check every link and confirm that project wording matches the public repositories.
6. Confirm the profile remains understandable with images disabled.
7. After publication, inspect the live GitHub profile in both themes and at mobile width.

## Out of Scope

- Artificial contribution activity, trophies, streaks, language statistics, or visitor counts.
- Games, guestbooks, issue-driven interactions, or scheduled profile updates.
- A separate portfolio website.
- Invented accomplishments, career titles, or unsupported security claims.
- Profile-picture replacement, private contact information, or changes to unrelated repositories.
