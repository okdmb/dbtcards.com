# DBT Skills Flashcard Trainer — Project Specification Document

**Version:** 1.0
**Status:** Living Document
**Classification:** Internal / Product
**Prepared by:** AI-assisted specification from full build history
**Date:** June 2026

---

# Table of Contents

1. Executive Summary
2. Project Context
3. Stakeholders
4. User Research and Personas
5. Functional Requirements
6. Non-Functional Requirements
7. System Architecture
8. Technical Design
9. Data Model
10. User Experience Specification
11. Accessibility Specification
12. API Specification
13. Security Specification
14. Infrastructure and Operations
15. Testing Strategy
16. Analytics and Metrics
17. Risks and Constraints
18. Open Questions and Unknowns
19. Future Roadmap
20. Assumptions Register
21. Glossary
22. Appendices
23. Clarification Questions

---

# 1. Executive Summary

## Project Overview

The DBT Skills Flashcard Trainer is a self-contained, single-page web application designed to help users study and memorise all four modules of Dialectical Behavior Therapy (DBT) skills through an interactive flashcard system. The application is distributed as a single HTML file requiring no server, no backend, and no installation.

## Purpose

DBT is a clinically validated therapeutic framework developed by Dr. Marsha Linehan. Its skills are taught across four modules: Mindfulness, Distress Tolerance, Emotion Regulation, and Interpersonal Effectiveness. Learning these skills requires repeated exposure and recall practice. This application provides a structured, engaging, and accessible mechanism for that practice.

## Vision

To be the most comprehensive, accessible, and polished self-contained DBT skills study tool available — requiring no account, no internet connection beyond initial font loading, and no technical expertise to use.

## Strategic Goals

- Provide complete coverage of all 50 canonical DBT skills across all four modules
- Deliver a mobile-first experience that functions equally well on desktop
- Meet WCAG 2.1 AA accessibility standards throughout
- Achieve Google Lighthouse scores of 100 across all four audit categories (Performance, Accessibility, Best Practices, SEO)
- Remain permanently free, ad-free, and self-hostable
- Operate as a single distributable file with zero runtime dependencies

## Success Criteria

| Criterion | Target |
|---|---|
| Google Lighthouse Performance | 100 |
| Google Lighthouse Accessibility | 100 |
| Google Lighthouse Best Practices | 100 |
| Google Lighthouse SEO | 100 |
| Total card coverage | 50 cards across 4 modules |
| Keyboard navigable | 100% of interactions |
| Screen reader compatible | Full semantic support |
| Mobile usable | All core interactions touch-accessible |
| File distribution | Single .html file |

## Business Value

- Zero hosting cost — distributable via email, file share, or any static host
- No maintenance burden of a backend system
- Accessible to therapists, patients, students, and educators without technical friction
- Supports clinical and educational settings with no data privacy concerns (no data leaves the device)

## User Value

Users gain a structured, self-paced tool to memorise, understand, and revisit every DBT skill with rich contextual explanations, progress tracking within a session, and a satisfying learning feedback loop.

## Key Differentiators

- All 50 DBT skills with full expanded definitions, clinical purpose descriptions, and inter-skill relationship mapping
- Zero dependency distribution model
- Purpose-built animations designed to reinforce the learning interaction
- Confetti celebration on mastery completion
- Comprehensive accessibility implementation including screen reader announcements on every card change

---

# 2. Project Context

## Problem Statement

DBT skills training materials are often presented in dense workbook format. Digital alternatives are either generic flashcard apps requiring manual card creation, poorly accessible, locked behind subscriptions, or dependent on account creation. There is no widely available, free, complete, accessible, self-contained digital DBT skills study tool.

## Existing Solutions

| Tool | Limitations |
|---|---|
| Anki | Requires account or manual card creation; not DBT-specific |
| Quizlet | Account required; subscription for full features; not tailored |
| PDF workbooks | Not interactive; no recall testing |
| General therapy apps | Incomplete skill coverage; account required; not offline-capable |

## Market Context

DBT is used clinically for borderline personality disorder, depression, anxiety, eating disorders, and substance use. Its skills are increasingly taught in non-clinical wellness contexts. The study tool serves both clinical populations (under therapist guidance) and self-directed learners.

## Historical Decisions

The following key decisions were made during the iterative development of this project:

1. **Single HTML file architecture** — chosen for zero-friction distribution and hosting
2. **Dark mode only** — light mode was implemented and subsequently removed as the primary audience preference and visual design were optimised for dark mode; removing light mode reduced complexity, eliminated a class of contrast compliance issues, and improved focus on polish of the primary experience
3. **No localStorage persistence** — considered and removed; session-only progress tracking avoids privacy concerns and reduces code complexity
4. **No swipe-to-mark gestures** — swipe left/right for Still Learning/Got It was implemented and subsequently removed after UX evaluation; dot-row navigation was retained and enhanced instead
5. **Counter badge replaced dot-row** — attempted and reversed; users preferred the spatial dot-row as a navigation primitive over an abstract count badge
6. **Dot-row drag-to-scrub** — added after dot-row restoration as a mobile-friendly enhancement to the tap-individual-dot interaction
7. **Expanded panel seamless connection** — the "More Info" expansion panel was redesigned multiple times before settling on a seamlessly-connected card extension aesthetic using shared borders, corner radius removal, and a roll-up animation on close

## Project Background

The project was developed iteratively through a conversational AI-assisted build process, with each feature, animation, and accessibility improvement applied incrementally. The build history constitutes a detailed change log covering every decision from initial creation to current state.

## Origin of Requirements

Requirements originated from:
- Clinical DBT curriculum (Linehan, 2015 Skills Training Manual)
- Accessibility standards (WCAG 2.1)
- Google Lighthouse audit tooling
- Iterative UX feedback through the build process
- Mobile-first design principles

---

# 3. Stakeholders

## Stakeholder Groups

| Group | Role | Interest |
|---|---|---|
| Patients / Service Users | Primary end users | Learning and practising DBT skills |
| Therapists / Clinicians | Secondary users / recommenders | Recommending tool to clients |
| DBT Skills Trainers | Secondary users | Teaching aid and homework support |
| General Wellness Learners | Primary end users | Self-directed DBT study |
| Accessibility Specialists | Compliance reviewers | WCAG conformance |
| Developers / Maintainers | Technical owners | Maintainability and extensibility |
| Clinical Educators | Curriculum reviewers | Clinical accuracy of skill content |

## Decision Makers

**Assumption:** A single product owner or lead developer holds decision authority over this project. No formal governance structure has been established.

## Technical Ownership

The application is a single HTML file. Technical ownership is held by whoever controls the canonical file and any hosting environment. No multi-contributor workflow is currently defined.

---

# 4. User Research and Personas

## Target Audiences

### Persona 1: Current DBT Patient — "Mia"
- Age: 24
- Context: Attending weekly DBT group skills training
- Device: iPhone, primarily mobile
- Goal: Review skills learned in session and practise recall before next week
- Pain points: Workbooks are bulky; apps require accounts; hard to study on the bus
- Accessibility needs: None identified; moderate tech literacy
- Key journeys: Filter to current module → flip through cards → mark known/studying → review studying pile

### Persona 2: Therapist — "Dr. James"
- Age: 41
- Context: Facilitates DBT group sessions; wants to recommend homework tools
- Device: Desktop and iPad
- Goal: Share a single tool that covers all four modules accurately without requiring client accounts
- Pain points: App stores require installation; subscription tools create equity barriers
- Key journeys: Preview card content for clinical accuracy → share file with clients → confirm no data collection

### Persona 3: Self-Directed Learner — "Sam"
- Age: 32
- Context: No formal DBT training; working through Marsha Linehan's workbook independently
- Device: Android phone and desktop
- Goal: Reinforce workbook reading with active recall
- Pain points: Passive reading isn't helping retention; no structured recall tool
- Key journeys: All Skills → work through full deck → use expanded panel for deep explanations → review related skills

### Persona 4: DBT Skills Trainer / Educator
- Age: 38
- Context: Teaching DBT in a hospital outpatient programme
- Device: Desktop, projector display
- Goal: Display specific skill cards during group sessions
- Pain points: PDF slides don't allow interactive navigation
- Key journeys: Filter by module → navigate to specific card → expand for group discussion

## Accessibility Considerations

The application must serve users who:
- Navigate exclusively by keyboard (motor disability)
- Use screen readers (visual disability): NVDA, JAWS, VoiceOver, TalkBack
- Have cognitive disabilities requiring clear, predictable interaction patterns
- Have low vision requiring sufficient colour contrast
- Prefer reduced motion (vestibular disorders)

---

# 5. Functional Requirements

## FR-01: Flashcard Display

**Feature Name:** Flashcard Display
**Priority:** P0 (Core)
**Purpose:** Present each DBT skill as an interactive flashcard with a front face (skill name/acronym) and a back face (definition and breakdown).

**Description:** A card component rendered in 3D CSS space. The front face shows the skill acronym, full title, and a subtitle. The back face shows the category tag, full definition, and a breakdown of acronym components where applicable.

**User Story:** As a user, I want to see a skill presented with its name on one side and its definition on the other, so I can test my recall before revealing the answer.

**Acceptance Criteria:**
- Card front displays: category tag (top-left), skill acronym (large, centred), full skill title, subtitle/hint text
- Card back displays: category tag (top-left), "More Info" chevron (bottom-centre), skill name label, definition paragraph, breakdown pills
- "tap to reveal" hint appears at bottom-right of front face
- "tap to flip" hint appears at bottom-right of back face
- Card maintains aspect ratio of approximately 16:9 using padding-top: 56% technique
- Card is constrained to max-width: 680px, centred on all screens
- Card has rounded corners (--card-radius: 20px)
- Each category has a distinct accent colour applied via CSS custom property `--accent-color`

**Category Accent Colours:**

| Category | Colour Variable | Hex |
|---|---|---|
| Mindfulness | --violet | #c084fc |
| Distress Tolerance | --coral | #f87171 |
| Emotion Regulation | --amber | #fbbf24 |
| Interpersonal Effectiveness | --teal | #3dd6c0 |

**Business Rules:**
- Category colour is applied to: card accent line (::before pseudo-element), category tag text and background, acronym text colour
- Accent line appears at top of both card faces

**Edge Cases:**
- Long acronyms (e.g., "DEAR MAN", "ACCEPTS") must not overflow the card face; font scales via clamp()
- Long definitions must not overflow the card back; back-content has overflow-y: auto
- Cards with no breakdown items must not render empty breakdown area

**Error Conditions:** Not applicable (static content, no network dependency for card data).

**Dependencies:** Font loading (Plus Jakarta Sans) affects visual rendering but not functional correctness.

---

## FR-02: Card Flip Animation

**Feature Name:** Card Flip Animation
**Priority:** P0 (Core)
**Purpose:** Simulate a physical card flip to reveal the definition.

**Description:** A CSS 3D transform animation using `rotateY` on `.card-inner` with `transform-style: preserve-3d` and `perspective: 1200px` on the parent `.card-stage`. Both faces use `backface-visibility: hidden`.

**User Story:** As a user, I want the card to flip when I tap it, so the interaction feels physical and reinforces the reveal experience.

**Interaction Triggers:**
- Click or tap anywhere on the card stage
- Keyboard: Space or Enter when card stage is focused
- Programmatic: `flipCard()` function call

**Animation Specification:**
- Duration: 0.55s
- Easing: `cubic-bezier(0.4, 0, 0.2, 1)`
- Front → Back: `rotateY(0deg)` → `rotateY(180deg)` (right edge swings backward)
- Back → Front: `rotateY(180deg)` → `rotateY(0deg)` (right edge swings forward)
- `will-change: transform` applied for GPU compositing

**Acceptance Criteria:**
- Flip triggers on tap/click/keyboard
- Both directions animate correctly
- `prefers-reduced-motion: reduce` disables animation (instant switch)
- Card does not flip when the More Info chevron button is tapped (stopPropagation)
- Card does not flip when result controls (Got It/Still Learning) are tapped

**Edge Cases:**
- Rapid double-tap must not cause visual jank; `_markBusy` flag prevents double-mark; flip itself has no debounce (intentional)
- Flip called while expanded panel is open triggers roll-up-then-flip sequence (see FR-09)

---

## FR-03: Card Navigation

**Feature Name:** Card Navigation
**Priority:** P0 (Core)
**Purpose:** Allow users to move forward and backward through the card deck.

**Description:** Previous (`<`) and Next (`>`) navigation buttons, plus keyboard arrow key support, advance or retreat through the current deck. Navigation wraps around (circular).

**Navigation Logic:** `nextCard()` and `prevCard()` skip cards marked as "Got It" (`known` Set). If all remaining cards are in `known`, navigation wraps to the first non-known card. If all cards are known, the complete state is shown.

**Acceptance Criteria:**
- Previous button navigates to previous non-known card
- Next button navigates to next non-known card
- Known cards are skipped in both directions
- Navigation wraps at deck boundaries
- Card resets to front face (unflipped) on navigation
- Expanded panel closes on navigation
- Dot-row updates to reflect new current position
- Card announcer aria-live region announces new card to screen readers

**Keyboard Shortcuts:**
- `ArrowRight` — next card
- `ArrowLeft` — previous card
- `Space` / `Enter` (on card stage) — flip card
- `G` — mark Got It
- `S` — mark Still Learning
- `Escape` — close modal or expanded panel

**Edge Cases:**
- All cards known → complete state shown, navigation not applicable
- Single card in filtered deck → prev/next return to same card

---

## FR-04: Got It / Still Learning Marking

**Feature Name:** Card Marking System
**Priority:** P0 (Core)
**Purpose:** Allow users to categorise each card as mastered (Got It) or requiring more study (Still Learning), driving progress tracking and navigation logic.

**Description:** Two buttons — "Still Learning" (amber, left) and "Got It" (green, right) — appear below the card. Marking a card advances to the next unreviewed card after a 180ms delay.

**State Model:**

| State | Set | Visual |
|---|---|---|
| Unseen | Neither | Grey dot |
| Got It | `known` | Green dot |
| Still Learning | `learning` | Amber dot |

**Business Rules:**
- A card can be in only one state at a time
- Marking a card that was previously in the other state transitions it (no history kept)
- Known cards are skipped during navigation
- The progress bar fills based on `known.size / deck.length`
- Complete state triggers only when `known.size === deck.length`

**Debounce Mechanism:**
- `_markBusy` flag prevents multiple marks during the 180ms advance delay
- `_markTimer` stores the pending setTimeout, cancelled if called again
- Index captured at click time (`markedIndex = currentIndex`) to prevent race conditions

**Acceptance Criteria:**
- Still Learning button marks card as learning, advances to next unreviewed card
- Got It button marks card as known, advances to next unreviewed card
- Stats bar updates immediately on mark
- Dot row updates immediately on mark
- Progress bar updates immediately on mark
- Cards remain in their marked state when navigated back to
- Marking respects `_markBusy` — rapid clicks do not stack

**Keyboard:** `G` = Got It, `S` = Still Learning (global keydown listener).

---

## FR-05: Category Filtering

**Feature Name:** Module Filter
**Priority:** P1 (High)
**Purpose:** Allow users to study a single DBT module in isolation.

**Description:** Five filter pills at the top of the page allow selection of All Skills, Mindfulness, Distress Tolerance, Emotion Regulation, or Interpersonal Effectiveness. Selecting a filter rebuilds the deck with only cards from that module.

**Acceptance Criteria:**
- "All Skills" is selected by default on page load
- Selecting a filter clears Known and Still Learning sets for the filtered deck
- Active filter pill shows: dim background, coloured border, coloured text matching category accent
- Inactive pills show: muted text, default border
- `aria-pressed="true"` is set on the active filter; `aria-pressed="false"` on all others
- Filter pills are wrapped in `<nav>` with `aria-label="Filter cards by DBT module"`
- When screen is small and card is flipped, filter pills collapse (see FR-13)
- Filter pills are centred horizontally via `justify-content: center`

**Pill-to-Category Mapping:**

| Pill | Category Key | Accent |
|---|---|---|
| All Skills | all | --text (white) |
| Mindfulness | mindfulness | --violet |
| Distress Tolerance | distress | --coral |
| Emotion Regulation | emotion | --amber |
| Interpersonal Effectiveness | interpersonal | --teal |

**Edge Cases:**
- Switching filter while on complete state resets to card view
- Single-card filtered decks function correctly

---

## FR-06: Progress Tracking

**Feature Name:** Session Progress Tracking
**Priority:** P1 (High)
**Purpose:** Provide users with real-time feedback on their mastery progress within a session.

**Description:** Four stat pills (Cards, Current, Got It, Studying) display session statistics. A progress bar beneath them fills proportionally to cards mastered. A text label shows "X card(s) remaining" (where remaining = `deck.length - known.size`).

**Stats Pill Definitions:**

| Pill | Value | Click Action |
|---|---|---|
| Cards | `deck.length` | Opens "All Cards" modal |
| Current | `currentIndex + 1` | Opens "Unreviewed" modal |
| Got It | `known.size` | Opens "Got It" modal |
| Studying | `learning.size` | Opens "Studying" modal |

**Progress Bar:**
- Width = `(known.size / deck.length) * 100%`
- Colour: `--teal` (#3dd6c0)
- Transition: 0.4s cubic-bezier
- Text label: `"X card remaining"` (singular) or `"X cards remaining"` (plural)
- Percentage display at right end of label row

**Acceptance Criteria:**
- All four stat values update immediately on mark, navigation, or filter change
- Progress bar fills correctly at 0%, partial, and 100%
- "0 cards remaining" displays on round complete
- Singular/plural handled correctly

**Note:** Progress resets when filter changes or deck is restarted. No cross-session persistence.

---

## FR-07: Grid Modal

**Feature Name:** Card Grid Modal
**Priority:** P1 (High)
**Purpose:** Allow users to browse all cards in a filtered view and jump directly to any card.

**Description:** A full-screen overlay modal containing a responsive grid of card thumbnails. Each thumbnail shows: category label, acronym, title, and status badge (✓ Got It, ~ Studying, or · Unseen). Clicking a thumbnail navigates to that card and closes the modal.

**Filter Options:**

| Source | Filter | Title |
|---|---|---|
| Cards pill | all | "All Cards" |
| Current pill | unreviewed | "Unreviewed" |
| Got It pill | known | "✓ Got It" (green) |
| Studying pill | learning | "~ Studying" (amber, with icon) |

**Modal Behaviour:**
- Opened by clicking stat pills
- Closed by: ✕ button, clicking overlay, Escape key
- Focus trapped inside modal when open (first focusable element receives focus on open)
- Focus returned to triggering element on close
- `role="dialog"`, `aria-modal="true"`, `aria-labelledby="modalTitle"`
- Body scroll locked while open
- `aria-live="polite"` on modal body for dynamic content

**Grid Card Thumbnail Specification:**
- Category colour applied as accent line (::before) and tag text
- Acronym in bold
- Full skill title in small muted text
- Status badge: green for known, amber for learning, muted for unseen
- `--gc-color` CSS custom property set per card

**Empty State:** "No cards in this group yet." message when filtered set is empty.

**Acceptance Criteria:**
- Clicking any thumbnail navigates to that card and closes modal
- Category accent colour applied correctly per thumbnail
- Modal title colour matches filter type
- Escape key closes modal
- Focus management correct on open and close
- Grid is responsive: `repeat(auto-fill, minmax(170px, 1fr))`

---

## FR-08: Expanded Information Panel

**Feature Name:** More Info Expanded Panel
**Priority:** P1 (High)
**Purpose:** Provide deeper clinical explanations of each skill beyond the flashcard definition.

**Description:** A chevron-down button at the top-right of the card back (visible only on the back face) triggers an expanded panel that slides open below the card. The panel contains three sections: In Depth, Purpose, and Related Skills.

**Panel Sections:**

| Section | Content |
|---|---|
| In Depth | Comprehensive clinical explanation of the skill, nuances, examples |
| Purpose | Why the skill exists; what clinical problem it solves |
| Related Skills | Pill tags listing skills that connect to this one across modules |

**Animation Specification:**

*Opening (Roll Down):*
- CSS class `.rolling-down` added
- Keyframe `panelRollDown`: `scaleY(0) opacity:0` → `scaleY(1) opacity:1`
- Duration: 0.32s, easing: `cubic-bezier(0, 0, 0.2, 1)` (decelerate)
- `transform-origin: top center`
- `max-height` transitions 0 → 600px simultaneously (0.32s same easing)

*Closing via Chevron (Roll Up):*
- CSS class `.rolling-up` added
- Keyframe `panelRollUp`: `scaleY(1) opacity:1` → `scaleY(0) opacity:0`
- Duration: 0.32s, easing: `cubic-bezier(0.8, 0, 1, 1)` (accelerate)
- Inline styles `opacity:0; transform:scaleY(0)` locked before class removal to prevent flash
- Card bottom corner radius restored after 380ms (delayed to match transition)

*Closing via Card Flip (Roll-Up Then Flip):*
1. `rolling-up` animation plays (0.32s)
2. On `animationend`: inline styles locked, `closeExpanded(true)` called (immediate corner restore)
3. `doFlip()` called immediately after

**Card Integration:**
- When panel is open: `expanded-open` class on `#cardStage`
- `expanded-open .card-back`: `border-bottom-left-radius: 0; border-bottom-right-radius: 0`
- Panel: `border-top: none; border-radius: 0 0 var(--card-radius) var(--card-radius)`
- Panel border colour: `var(--border)` — matches card border
- `margin-bottom: 1.4rem` transfers from card-stage to panel when open
- Chevron button rotates 180° (CSS class `.open` on button, `transform: rotate(180deg)` on SVG)
- `aria-expanded="true/false"` on chevron button

**Tap-to-Flip on Expanded Panel:**
- Expanded panel has `onclick="flipCard()"` — tapping panel body flips card
- Roll-up animation plays before flip

**Swipe Down to Open (Touch):**
- `touchstart` / `touchend` on `#cardStage`
- Minimum vertical: 40px, maximum horizontal drift: 50px, maximum time: 450ms
- Only active when flipped (card back showing) and panel not already open

**Acceptance Criteria:**
- Chevron only visible on card back
- Opening plays roll-down animation
- Closing via chevron plays roll-up animation
- Closing via card flip plays roll-up then card flip sequence
- No visual flash between animation states
- Panel bottom corners match card (rounded)
- Panel and card share seamless border
- `aria-expanded` reflects state correctly
- Panel closes on card navigation or deck restart
- Swipe-down gesture opens panel on touch devices

---

## FR-09: Complete State

**Feature Name:** Round Complete
**Priority:** P1 (High)
**Purpose:** Celebrate mastery and provide a clear end-of-round experience.

**Description:** When all cards in the current deck are marked Got It (`known.size === deck.length`), the card stage and result controls are hidden and a "Round Complete" panel is shown. A confetti celebration animation plays.

**Complete State Content:**
- ✦ icon (animated: spin-in then floating loop)
- "Round Complete" heading (h2, --teal colour)
- Summary text: "All X cards mastered! Great work."
- "Start Over" button (calls `resetDeck()`, `aria-label="Restart deck"`)

**Entrance Animations:**
- Panel: `celebrationPop` — `scale(0.82) translateY(16px)` → `scale(1.04)` → `scale(1)` (springy overshoot)
- ✦ icon: `starSpin` (0.65s spin-in with overshoot) + `starFloat` (3s infinite floating, delayed 1s)
- Heading, text, button: `fadeSlideUp` staggered at 0.45s, 0.6s, 0.75s delays

**Confetti Animation:**

*Burst System (55 particles):*
- Explode outward from card centre position (`cx = canvas.width/2`, `cy = canvas.height * 0.38`)
- Angle: evenly distributed 0–360° with random offset
- Speed: 4–13px/frame initial velocity
- Shapes: mix of rectangles and circles

*Physics:*
- Gravity: 0.12px/frame²
- Rotation per frame: random ±0.22rad
- Total duration: 4200ms
- Fade: linear opacity reduction over final 30% of duration

*Colours:* #3dd6c0, #fbbf24, #f87171, #c084fc, #4ade80, #60a5fa, #fff, #fb923c, #e879f9

*Canvas:* Fixed overlay, `pointer-events: none`, `aria-hidden="true"`, resizes on window resize event (once listener).

*Reduced Motion:* Confetti skipped if `prefers-reduced-motion: reduce`.

**Shower System:** Disabled (`SHOWER_COUNT = 0`). Reserved variable retained for future re-enablement.

**Acceptance Criteria:**
- Complete state shown only when all cards are marked Got It
- Confetti plays once per completion
- Start Over button resets deck and returns to card view
- Complete state hidden when filter changes or restart initiated
- Animations respect `prefers-reduced-motion`

---

## FR-10: Dot Row Navigation

**Feature Name:** Dot Row
**Priority:** P1 (High)
**Purpose:** Provide a spatial overview of deck progress and direct-access navigation to any card.

**Description:** A row of 6×6px circular dots below the keyboard hint, one per card. Dot colour indicates card state. Current card shown as a wider pill (16×6px). Supports click-to-navigate and drag/swipe scrubbing.

**Dot States:**

| State | CSS Class | Colour |
|---|---|---|
| Current | `.current` | --text (white), 16px wide, border-radius: 3px |
| Got It | `.known` | --green |
| Still Learning | `.learning` | --amber |
| Unseen | (none) | --faint |

**Drag-to-Scrub:**
- `mousedown` on dot row: enter drag mode, navigate to dot under cursor
- `mousemove` (on document): while dragging, navigate to nearest dot
- `mouseup` (on document): exit drag mode
- `touchstart` / `touchmove` / `touchend`: same on touch devices (passive listeners)
- Position mapping: `closest dot by centre distance` algorithm (not proportional width)
- Cursor: `grab` default, `grabbing` while dragging
- `user-select: none` prevents text selection during drag

**Navigation on Scrub:**
- `currentIndex` updated to target index
- Card reset to front face (unflipped)
- Expanded panel closed (`closeExpanded(true)`)
- `renderCard()` called

**Dot Row Container:**
- `role="group"`, `aria-label="Card progress — drag to navigate"`
- Individual dots: `pointer-events: none` (interaction handled at row level)
- Row: `flex-wrap: wrap`, `gap: 4px`, `justify-content: center`
- Row padding: 6px 4px (increases tap target area)

**Acceptance Criteria:**
- One dot per card in current deck
- Correct colour applied per card state
- Current card dot transitions between cards correctly
- Drag scrubbing navigates cards in real time
- Touch scrubbing works on mobile
- No performance degradation with 50 dots
- Dot row rebuilds correctly after filter change or restart

---

## FR-11: Restart / Shuffle

**Feature Name:** Restart
**Priority:** P1 (High)
**Purpose:** Allow users to reset their session and randomise the deck order.

**Description:** A "Restart" button (circular arrow icon, no text) below the navigation buttons rebuilds the deck from scratch with a new random shuffle.

**`shuffleDeck()` Behaviour:**
- Fisher-Yates shuffle applied to `deck` array in-place
- `currentIndex` reset to 0
- `known` and `learning` Sets cleared
- `flipped` reset to false
- Expanded panel closed
- Complete state hidden
- Card and controls shown
- `renderCard()` and `renderDots()` called

**Initial Page Load Shuffle:**
- `buildDeck()` called first (ordered by source array)
- Fisher-Yates shuffle applied immediately after
- `renderCard()` and `renderDots()` called again

**Acceptance Criteria:**
- Restart shuffles deck and clears all progress
- Card resets to front face
- Filter is retained after restart (deck rebuilt from current filter)
- Restart button has `aria-label="Restart and reshuffle cards"`

---

## FR-12: Keyboard Navigation

**Feature Name:** Keyboard Navigation
**Priority:** P0 (Accessibility)
**Purpose:** Ensure all core interactions are accessible via keyboard without mouse.

**Keyboard Map:**

| Key | Action | Scope |
|---|---|---|
| `←` | Previous card | Global |
| `→` | Next card | Global |
| `Space` / `Enter` | Flip card | Card stage focused |
| `G` | Got It | Global |
| `S` | Still Learning | Global |
| `Escape` | Close modal (if open) or expanded panel (if open) | Global |
| `Tab` | Standard focus traversal | Global |
| `Space` / `Enter` | Activate focused button | All buttons |

**Focus Management:**
- Skip link: first Tab press reveals "Skip to content" link anchored to `#main-content`
- Modal: focus moves to first focusable element on open; returns to trigger on close
- All interactive elements have visible `:focus-visible` outline (2px solid --teal, offset 2px)
- `outline: none` on `:focus` (mouse), `outline: 2px solid var(--teal)` on `:focus-visible` (keyboard)

---

## FR-13: Responsive Pill Collapse

**Feature Name:** Filter Pill Auto-Hide
**Priority:** P2 (Medium)
**Purpose:** Prevent filter pills from overlapping card content on small or zoomed screens.

**Description:** When a card is flipped to its back face, the position of the filter pill container bottom is compared to the card stage top. If they overlap or are within 12px, pills collapse (max-height: 0, opacity: 0).

**Trigger Conditions:**
- Card flip to back
- Window resize event
- Both checks deferred 50ms to allow layout reflow

**CSS:**
- `.filters` default: `max-height: 120px; opacity: 1; transition: max-height 0.3s, opacity 0.3s, margin-bottom 0.3s`
- `.filters.pills-hidden`: `max-height: 0; opacity: 0; pointer-events: none; margin-bottom: 0`

**Acceptance Criteria:**
- Pills collapse when overlapping at small screen sizes
- Pills reappear when card flips back to front
- Check runs on resize for live zoom changes

---

# 6. Non-Functional Requirements

## Performance

| Requirement | Target |
|---|---|
| Lighthouse Performance score | 100 |
| Total file size | ≤ 150KB |
| Time to First Contentful Paint | < 1.5s on 4G |
| No render-blocking resources | Font loaded via print/onload trick + preload |
| GPU compositing for card flip | `will-change: transform` on `.card-inner` |
| Canvas animation | 60fps; automatically pauses when tab backgrounded |
| Drag scrubbing | No perceptible lag with 50 dots |

**Font Loading Strategy:**
1. `<link rel="preconnect">` to fonts.googleapis.com
2. `<link rel="preconnect" crossorigin>` to fonts.gstatic.com
3. `<link rel="preload" as="style">` for the font stylesheet
4. `<link rel="stylesheet" media="print" onload="this.media='all'">` for non-blocking progressive load
5. `<noscript>` fallback stylesheet for JS-disabled environments

## Scalability

The application is static with no server-side components. Scalability concerns are limited to:
- Adding more cards: The data model supports arbitrary card count; UI scales via CSS flex-wrap
- Content updates: All content is inline in the HTML file; no CMS layer exists

## Reliability

- No network dependencies at runtime (all logic is inline)
- Font loading failure: system sans-serif stack provides acceptable fallback
- The application functions without JavaScript enabled for static content display (font loads via noscript fallback); interactive features require JavaScript

## Availability

- Self-contained file: 100% availability when hosted as a static asset
- No single point of failure beyond the hosting platform
- Can be run from local filesystem (file:// protocol)

**Assumption:** Canonical link in SEO metadata references `https://dbt-flashcards.app/` — this domain must be registered and hosting configured if SEO metadata is to function correctly.

## Security

See Section 13.

## Privacy

- No data collection, transmission, or storage of any kind
- `localStorage` was explicitly removed from the implementation
- No cookies, tracking scripts, or analytics
- No user accounts or authentication
- Safe for use in clinical settings; no PHI risk

## Compliance

- WCAG 2.1 Level AA conformance
- GDPR: Not applicable (no personal data processed)
- HIPAA: No PHI processed; clinical suitability is the therapist's responsibility

## Accessibility

See Section 11.

## Internationalisation / Localisation

- Current implementation is English-only
- All DBT skill content is authored in English
- No i18n framework implemented
- CSS uses `lang="en"` on `<html>`
- `text-size-adjust: 100%` applied to prevent mobile browser font scaling

**Open Question:** Is multilingual support a future requirement? (See Section 18)

## Maintainability

- All content (card data, styles, scripts) is contained in a single file
- CARDS array is the canonical data source; new cards are added by appending objects to the array
- CSS uses custom properties (`--variable`) throughout for theming consistency
- JS uses named function declarations for readability and hoisting safety

## Observability

No runtime monitoring exists. The application is a static client-side tool. Observability is limited to:
- Lighthouse CI audits (manual)
- Browser DevTools Console (development only)
- No error tracking, no logging infrastructure

---

# 7. System Architecture

## High-Level Architecture

```
┌─────────────────────────────────────────┐
│           Single HTML File              │
│  ┌─────────────────────────────────┐   │
│  │  <head>                         │   │
│  │  ├─ Meta / SEO tags             │   │
│  │  ├─ Font preload chain          │   │
│  │  └─ Inline <style>              │   │
│  ├─────────────────────────────────┤   │
│  │  <body>                         │   │
│  │  ├─ Skip link                   │   │
│  │  ├─ <main> landmark             │   │
│  │  │   ├─ Header (h1)             │   │
│  │  │   ├─ Stats bar               │   │
│  │  │   ├─ Progress bar            │   │
│  │  │   ├─ Filter nav              │   │
│  │  │   ├─ Card stage              │   │
│  │  │   │   ├─ Card front          │   │
│  │  │   │   └─ Card back           │   │
│  │  │   ├─ Expanded panel          │   │
│  │  │   ├─ Complete state          │   │
│  │  │   ├─ Result controls         │   │
│  │  │   ├─ Navigation controls     │   │
│  │  │   ├─ Dot row                 │   │
│  │  │   └─ Keyboard hint           │   │
│  │  ├─ Modal overlay               │   │
│  │  ├─ Canvas (celebration)        │   │
│  │  └─ Inline <script>             │   │
│  └─────────────────────────────────┘   │
└─────────────────────────────────────────┘
        │
        ▼
┌──────────────────┐    ┌──────────────────┐
│  Google Fonts    │    │  Browser Engine  │
│  (optional,      │    │  (JS, CSS, HTML  │
│  font only)      │    │  rendering)      │
└──────────────────┘    └──────────────────┘
```

## Component Architecture

The application has no formal component system. All UI is constructed from static HTML updated via DOM manipulation. Logical components:

| Component | HTML Element | Primary JS Functions |
|---|---|---|
| Card Stage | `#cardStage` | `flipCard()`, `doFlip()`, `checkPillOverlap()` |
| Card Front | `#cardFront` | `renderCard()` |
| Card Back | `#cardBack` | `renderCard()` |
| Expanded Panel | `#expandedPanel` | `openExpanded()`, `closeExpanded()`, `populateExpanded()`, `toggleExpanded()`, `animatedCloseExpanded()`, `rollUpThenFlip()` |
| Stats Bar | `.stats-bar` | `updateStats()` |
| Progress Bar | `#progress-fill` | `updateStats()` |
| Filter Nav | `.filters` | `buildDeck()`, filter button event listeners |
| Dot Row | `#dotRow` | `renderDots()`, dot-row scrubber IIFE |
| Modal | `#modalOverlay` | `openModal()`, `closeModal()`, `openModalFocus()` |
| Complete State | `#completeState` | `renderCard()` |
| Celebration Canvas | `#celebrationCanvas` | `launchConfetti()` |
| Card Announcer | `#cardAnnouncer` | `renderCard()` (aria-live) |

## Data Flow

```
User Interaction
      │
      ▼
Event Handler (click/keydown/touchend)
      │
      ▼
State Mutation (known/learning Sets, currentIndex, flipped)
      │
      ├──► renderCard()    → Updates card DOM from deck[currentIndex]
      ├──► renderDots()    → Rebuilds dot row from Sets
      └──► updateStats()   → Updates stat pill text and progress bar
```

## State Model

All application state is held in JavaScript module-level variables:

| Variable | Type | Description |
|---|---|---|
| `deck` | Array | Current ordered card array (filtered + shuffled) |
| `currentIndex` | Number | Index of current card in `deck` |
| `known` | Set<Number> | Indices of cards marked Got It |
| `learning` | Set<Number> | Indices of cards marked Still Learning |
| `flipped` | Boolean | Whether current card shows back face |
| `expandedOpen` | Boolean | Whether expanded panel is open |
| `activeCategory` | String | Current filter key |
| `_markBusy` | Boolean | Debounce flag for mark actions |
| `_markTimer` | Number|null | Pending setTimeout ID for mark advance |

**State Lifecycle:** All state is session-only. Refreshing the page resets all state.

---

# 8. Technical Design

## Technologies

| Technology | Version / Spec | Role |
|---|---|---|
| HTML5 | Living Standard | Document structure, semantics |
| CSS3 | Custom Properties, Grid, Flexbox, Animations, 3D Transforms | Layout, theming, animations |
| JavaScript (ES6+) | Vanilla (no framework) | All interactivity and state management |
| Canvas 2D API | Browser native | Confetti celebration |
| Web Fonts | Google Fonts API | Typography |
| CSS Custom Properties | Native | Design token system |

## No Dependencies

The application intentionally uses zero JavaScript libraries or frameworks. All functionality is implemented in vanilla JavaScript.

## Font

**Family:** Plus Jakarta Sans
**Weights loaded:** 400, 500, 600, 700, 800
**Source:** Google Fonts CDN
**Fallback:** System sans-serif stack (implicit browser default)
**Loading:** Progressive non-blocking (print/onload + preload + noscript)

Note: Weight 300 was explicitly excluded from the font request as no elements use it, reducing the font payload.

## CSS Architecture

**Design Token System:** All colours, spacing, radii, and transitions are defined as CSS custom properties on `:root`.

**CSS Custom Properties — Colours (Dark Mode):**

| Variable | Value | Usage |
|---|---|---|
| --bg | #0d1117 | Page background |
| --surface | #161b24 | Card, modal, button surfaces |
| --surface2 | #1e2636 | Card back, expanded panel, modal grid cards |
| --border | rgba(255,255,255,0.09) | Default borders |
| --border-hover | rgba(255,255,255,0.20) | Hovered borders |
| --text | #e8edf8 | Primary text |
| --muted | #8898b8 | Secondary/hint text |
| --faint | #3d4d66 | Dot row unseen state (decorative only, not used for text) |
| --teal | #3dd6c0 | Interpersonal Effectiveness accent |
| --teal-dim | rgba(61,214,192,0.13) | Teal dim background |
| --teal-border | rgba(61,214,192,0.32) | Teal border |
| --amber | #fbbf24 | Emotion Regulation accent; Still Learning |
| --amber-dim | rgba(251,191,36,0.13) | Amber dim background |
| --amber-border | rgba(251,191,36,0.32) | Amber border |
| --coral | #f87171 | Distress Tolerance accent |
| --coral-dim | rgba(248,113,113,0.13) | Coral dim background |
| --coral-border | rgba(248,113,113,0.32) | Coral border |
| --violet | #c084fc | Mindfulness accent |
| --violet-dim | rgba(192,132,252,0.13) | Violet dim background |
| --violet-border | rgba(192,132,252,0.32) | Violet border |
| --green | #4ade80 | Got It; positive confirmation |
| --green-dim | rgba(74,222,128,0.13) | Green dim background |
| --green-border | rgba(74,222,128,0.32) | Green border |

**CSS Custom Properties — Spacing and Radii:**

| Variable | Value |
|---|---|
| --radius | 16px |
| --card-radius | 20px |
| --transition | 0.22s cubic-bezier(0.4,0,0.2,1) |

## JavaScript Architecture

All JavaScript is contained in a single `<script>` tag at the bottom of `<body>`. Code is organised as:

1. CARDS array (data)
2. catColors mapping object (data)
3. State variables
4. Core render functions (`renderCard`, `renderDots`, `updateStats`)
5. Navigation functions (`nextCard`, `prevCard`, `buildDeck`)
6. Action functions (`flipCard`, `doFlip`, `markCard`, `shuffleDeck`, `resetDeck`)
7. Expanded panel functions
8. Modal functions
9. Utility IIFEs (dot scrubber, theme toggle removed)
10. Event listeners
11. Initialisation

---

# 9. Data Model

## CARDS Array

The canonical data source. Each element is a plain JavaScript object.

### Card Object Schema

| Field | Type | Required | Description |
|---|---|---|---|
| `cat` | String | Yes | Category key: `"mindfulness"`, `"distress"`, `"emotion"`, `"interpersonal"` |
| `acronym` | String | Yes | Displayed on card front (large); may be multi-word |
| `title` | String | Yes | Full skill name |
| `subtitle` | String | Yes | Brief descriptor shown beneath title on front |
| `definition` | String | Yes | Paragraph definition shown on card back |
| `breakdown` | Array<{b, t}> | Yes | Breakdown pills: `b` = bold letter(s), `t` = remainder of text |
| `detail` | String | Yes | Extended in-depth explanation for expanded panel |
| `purpose` | String | Yes | Clinical purpose description for expanded panel |
| `related` | Array<String> | Yes | List of related skill names |

### Validation Rules

- `cat` must be one of the four valid category keys
- `acronym` must be non-empty string
- `breakdown` may be empty array `[]` for skills without acronym components
- `related` may be empty array `[]`
- `detail` and `purpose` are required; fallback text: `"No additional detail available."` rendered if empty
- All string fields are rendered as text content (no HTML injection risk)

### catColors Object

Maps category keys to theme objects:

```javascript
{
  label: String,      // Display name (e.g., "Interpersonal Effectiveness")
  color: String,      // CSS var reference (e.g., "var(--teal)")
  dim: String,        // CSS var reference (e.g., "var(--teal-dim)")
  border: String      // CSS var reference (e.g., "var(--teal-border)")
}
```

### Runtime State Objects

| Object | Description |
|---|---|
| `deck` | Mutable copy of filtered CARDS, shuffled; mutated in-place by Fisher-Yates |
| `known` | `Set<Number>` of deck indices |
| `learning` | `Set<Number>` of deck indices |

No persistent storage. No serialisation. All state lives in JavaScript memory for the session duration.

---

# 10. User Experience Specification

## Information Architecture

```
DBT Skills Flashcard Trainer
├── Header
│   └── Title ("DBT Skills Flashcards")
├── Stats Bar
│   ├── Cards (count)
│   ├── Current (position)
│   ├── Got It (count)
│   └── Studying (count)
├── Progress Bar
│   └── Label + percentage
├── Filter Navigation
│   ├── All Skills
│   ├── Mindfulness
│   ├── Distress Tolerance
│   ├── Emotion Regulation
│   └── Interpersonal Effectiveness
├── Card Stage
│   ├── Card Front
│   │   ├── Category Tag
│   │   ├── Acronym
│   │   ├── Title
│   │   ├── Subtitle
│   │   └── "tap to reveal" hint
│   └── Card Back
│       ├── Category Tag
│       ├── More Info Chevron (top-right)
│       ├── Skill Name Label
│       ├── Definition
│       ├── Breakdown Pills
│       └── "tap to flip" hint
├── Expanded Panel (conditional)
│   ├── In Depth section
│   ├── Purpose section
│   └── Related Skills section
├── Complete State (conditional)
│   ├── ✦ icon
│   ├── "Round Complete" heading
│   ├── Summary text
│   └── Start Over button
├── Result Controls
│   ├── Still Learning button
│   └── Got It button
├── Navigation Controls
│   ├── Previous button
│   ├── Restart button
│   └── Next button
├── Dot Row
└── Keyboard Hint
```

## Navigation Structure

The application is a single view with no page routing. Modal overlays provide secondary navigation surfaces.

## Screen States

| State | Condition | Visible Elements |
|---|---|---|
| Default (front) | !flipped | Card front, result controls, nav controls, dot row |
| Revealed (back) | flipped | Card back, More Info chevron, result controls, nav controls, dot row |
| Expanded | flipped + expandedOpen | Card back (flat-bottom) + expanded panel, result controls, nav controls, dot row |
| Complete | known.size === deck.length | Complete state panel, nav controls, dot row |
| Grid Modal | modalOpen | Overlay with grid of thumbnails |

## User Flows

### Primary Study Flow
1. Page loads → deck shuffled → card 1 front shown
2. User reads acronym/title → taps card → definition revealed
3. User reads definition → marks Got It or Still Learning
4. Next non-known card advances automatically
5. Repeat until all cards known → celebration + round complete

### Deep Study Flow
1. Card back shown → user taps ∨ chevron → expanded panel rolls down
2. User reads In Depth, Purpose, Related Skills
3. User taps card or ∨ (now ∧) → panel rolls up (via chevron) or card flips (via tap)

### Module Focus Flow
1. User taps filter pill (e.g., "Mindfulness")
2. Deck rebuilds with 10 Mindfulness cards only
3. Progress/stats reset for filtered deck
4. Study as normal

### Card Browse Flow
1. User taps stat pill (e.g., "Studying")
2. Grid modal opens showing only studying cards
3. User taps any card thumbnail → modal closes → that card shown

## Responsive Behaviour

| Breakpoint | Behaviour |
|---|---|
| ≥ 680px | Card and controls at max-width: 680px, centred |
| < 500px | Reduced padding, smaller font sizes, keyboard hint hidden |
| Zoomed/small | Filter pills collapse when overlapping card back |

## Loading States

No loading states exist (no async operations). Font load may cause brief FOIT/FOUT mitigated by `font-display: swap` (via Google Fonts URL parameter).

## Error States

No error states are defined (no network requests or user input fields). Invalid state is prevented by data validation in the CARDS array (static content).

## Empty States

| Condition | Display |
|---|---|
| Grid modal with no matching cards | "No cards in this group yet." centred message |
| Filtered deck with 0 cards | Theoretically impossible with current data |

---

# 11. Accessibility Specification

## WCAG Conformance Target

WCAG 2.1 Level AA

## Semantic Structure

| Element | Role/Semantic |
|---|---|
| `<html lang="en">` | Language declaration |
| `<main role="main">` | Primary content landmark |
| `<header>` | Page header landmark |
| `<nav aria-label="Filter cards by DBT module">` | Navigation landmark for filters |
| `<h1>` | Page title "DBT Skills Flashcards" |
| `<h2>` | "Round Complete" heading |
| `<button>` | All interactive controls (not `<div onclick>`) |
| `aria-live="polite"` | Card announcer, modal body |
| `role="dialog"` | Modal overlay |
| `aria-modal="true"` | Modal overlay |

## Focus Management

### Skip Link
- `<a class="skip-link" href="#main-content">Skip to content</a>` is the first focusable element
- Visually hidden until focused (`top: -100%` → `top: 1rem` on `:focus`)
- Anchor target: `<a id="main-content">` inside `#cardStage`
- `tabindex="-1"` on anchor; `aria-hidden="true"` to prevent screen reader announcement of empty link

### Focus Ring
```css
:focus { outline: none; }
:focus-visible { outline: 2px solid var(--teal); outline-offset: 3px; border-radius: 4px; }
button:focus-visible, [role="button"]:focus-visible { outline: 2px solid var(--teal); outline-offset: 2px; border-radius: 6px; }
```

### Modal Focus Trap
- On open: `setTimeout(() => first.focus(), 50)` where first is `#modalPanel button, #modalPanel [tabindex="0"]`
- On close: `_modalReturnFocus.focus()` where `_modalReturnFocus` captured at open time
- Escape key: closes modal via global keydown

## Screen Reader Behaviour

### Card Announcements
- `#cardAnnouncer`: `aria-live="polite" aria-atomic="true" class="sr-only"`
- On every `renderCard()`: `"Card X of Y: [title]. [subtitle]. Press Space to reveal definition."`

### Interactive Elements
All buttons have accessible names via either:
1. Visible text content
2. `aria-label` attribute (icon-only buttons)

| Button | Accessible Name |
|---|---|
| Previous | "Previous card" |
| Next | "Next card" |
| Restart | "Restart and reshuffle cards" |
| Still Learning | Text: "Still Learning" + SVG aria-hidden |
| Got It | Text: "Got It" + SVG aria-hidden |
| More Info chevron | "Expand for more detail" |
| Modal close | ✕ character |
| Start Over | "Restart deck" |
| Filter pills | Visible text + `aria-pressed` |

### Decorative SVGs
All SVG icons have `aria-hidden="true" focusable="false"` to prevent screen reader announcement.

### Dot Row
- Container: `role="group" aria-label="Card progress — drag to navigate"`
- Individual dots: `pointer-events: none` (not individually focusable or announceable)

## Colour and Contrast

All text elements meet WCAG 1.4.3 (contrast ratio ≥ 4.5:1 for normal text):

| Element | Foreground | Background | Ratio | Pass |
|---|---|---|---|---|
| Body text | #e8edf8 | #161b24 | 14.72:1 | AA ✓ |
| Muted text | #8898b8 | #161b24 | 5.94:1 | AA ✓ |
| Muted on surface2 | #8898b8 | #1e2636 | 5.22:1 | AA ✓ |
| Teal on surface | #3dd6c0 | #161b24 | 9.52:1 | AA ✓ |
| Amber on surface | #fbbf24 | #161b24 | 10.34:1 | AA ✓ |
| Green on surface | #4ade80 | #161b24 | 9.91:1 | AA ✓ |
| Coral on surface | #f87171 | #161b24 | 6.24:1 | AA ✓ |
| Violet on surface | #c084fc | #161b24 | 6.53:1 | AA ✓ |

**Note:** `--faint` (#3d4d66) is used exclusively as a background colour for the dot row's unseen state. It is not applied to any text element. WCAG 1.4.11 (non-text contrast) is not automatically checked by Lighthouse's axe-core engine.

## Tap Target Sizes

| Element | Min Height | Min Width |
|---|---|---|
| Stat pills | 44px | auto |
| Filter pills | 36px | auto |
| Button (general) | implicit via padding | auto |
| btn-nav (prev/next) | 44px | 44px |
| Modal close | 44px | 44px |

## Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
  .card-inner { transition: none !important; }
}
```

Confetti celebration: `if (window.matchMedia('(prefers-reduced-motion: reduce)').matches) return;`

---

# 12. API Specification

The application makes no API calls. No server-side endpoints exist.

**External Resource:** Google Fonts API
- URL: `https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap`
- Type: CSS stylesheet containing `@font-face` declarations
- Authentication: None required
- Rate limits: Google Fonts standard (not applicable for typical usage)
- Failure mode: System sans-serif fallback renders; no functionality loss

---

# 13. Security Specification

## Threat Model

The application is a static client-side HTML file with no server, no authentication, no user-generated content, and no data transmission. The attack surface is minimal.

## Attack Surfaces

| Surface | Risk | Mitigation |
|---|---|---|
| Static file serving | Directory traversal | Handled by hosting platform configuration (out of scope for this spec) |
| Google Fonts CDN | Supply chain font replacement | Low risk; font is decorative; page functional without it |
| User clipboard (Copy Link) | Not implemented | N/A |
| DOM rendering of card content | XSS via injected content | All card content is authored static data; rendered as `.textContent` not `.innerHTML` (breakdown pills use `.innerHTML` with `<b>` tags but content is static and author-controlled) |

## Security Assumptions

1. The HTML file is served over HTTPS when hosted (canonical URL uses https://)
2. The hosting platform enforces appropriate Content-Security-Policy headers (not configured within the file itself)
3. Card content is authored content and not user-supplied; no sanitisation layer is required beyond what exists
4. No secrets, credentials, or tokens are embedded in the application

## Content Security Policy

**ASSUMPTION:** No CSP header is configured within the file itself. If hosting on a platform that supports CSP headers, the following policy should be applied at the server level:

```
Content-Security-Policy:
  default-src 'self';
  style-src 'self' 'unsafe-inline' https://fonts.googleapis.com;
  font-src https://fonts.gstatic.com;
  script-src 'self' 'unsafe-inline';
  img-src 'self' data:;
  connect-src 'none';
```

Note: `'unsafe-inline'` is required because styles and scripts are inline. An alternative approach would be to extract styles and scripts to separate files and use nonces.

## Data Protection

- No personal data is processed
- No cookies are set
- No `localStorage` or `sessionStorage` is used
- No network requests are made during normal operation (only Google Fonts on initial load)

## Abuse Prevention

No abuse vectors exist for a static client-side application with no form inputs, no server, and no data transmission.

---

# 14. Infrastructure and Operations

## Hosting Model

The application is a single HTML file suitable for hosting on any static file server including:
- GitHub Pages
- Netlify
- Vercel
- Cloudflare Pages
- Any web server (nginx, Apache, etc.)
- Local filesystem (file:// protocol)

**Assumption:** The canonical URL referenced in SEO metadata (`https://dbt-flashcards.app/`) must be configured and pointed to the hosted file.

## Deployment Process

Deployment is file replacement. There is no build process, no compilation, no transpilation, and no package management.

**Recommended Deployment Process:**
1. Make changes to `dbt-flashcards.html`
2. Run local validation (JS syntax, Lighthouse audit)
3. Replace the hosted file
4. Verify via Lighthouse CI or manual audit

## CI/CD

No CI/CD pipeline is currently implemented. Recommended pipeline:

```yaml
on: push to main
steps:
  - Validate HTML (W3C validator)
  - Check JS syntax (node --check)
  - Run Lighthouse CI audit
  - Deploy to static host
```

## Environment Management

Single environment (production). No staging, development, or preview environments are defined.

**Recommendation:** Maintain a local development copy; test changes before replacing the production file.

## Backup Strategy

The HTML file should be version-controlled in a Git repository. The full build history represents a de facto changelog.

## Rollback Strategy

Replace the current file with a previous version from Git history.

## Monitoring

No runtime monitoring exists. Recommended:
- Uptime monitoring on the hosting URL
- Periodic Lighthouse CI audit runs

---

# 15. Testing Strategy

## Unit Testing

No automated unit testing framework is implemented. Recommended tests:

| Test | Method |
|---|---|
| Card data completeness | Validate all 50 CARDS entries have required fields |
| Category assignment | Assert each card has valid `cat` value |
| Acronym uniqueness | Assert no duplicate acronym values |
| Breakdown format | Assert breakdown items have `{b, t}` shape |

## Integration Testing

Manual testing matrix:

| Scenario | Steps | Expected |
|---|---|---|
| Filter → study → complete | Filter to Mindfulness, mark all 10 as Got It | Complete state shows, confetti plays |
| Mark → navigate skip | Mark card 1 as Got It, press next | Card 2 shown (card 1 skipped) |
| Restart | Click Restart | Deck shuffled, all marks cleared |
| Modal navigation | Click Got It pill, tap a card | Modal closes, that card shown |
| Expanded panel open/close | Flip card, tap chevron, tap chevron | Panel opens then closes |
| Roll-up-then-flip | Open expanded, tap card | Panel rolls up, card flips |

## End-to-End Testing

Recommended: Playwright or Cypress test suite covering primary user flows.

```
test('complete primary study flow')
  navigate to app
  expect 50 cards in dot row
  flip card
  expect card back visible
  click Got It
  expect dot becomes green
  expect progress increases
```

## Accessibility Testing

| Tool | Scope |
|---|---|
| axe DevTools | Automated WCAG 2.1 AA check |
| Lighthouse Accessibility | Score ≥ 100 |
| NVDA + Chrome | Screen reader functional test |
| VoiceOver + Safari | Screen reader functional test (iOS) |
| Keyboard-only navigation | Complete all flows without mouse |
| Zoom to 200% | Layout integrity check |
| `prefers-reduced-motion` | Verify animations suppressed |

## Performance Testing

- Google Lighthouse (local and CI): Performance score ≥ 100
- WebPageTest: LCP, FCP, TBT measurements
- DevTools Performance tab: Card flip animation frame rate (target 60fps)
- Canvas animation: Measure frame rate during confetti on low-end mobile

## Security Testing

- Check for inline script injection points: None (all content is `.textContent`)
- Verify no external requests during normal use (DevTools Network tab)
- Verify no data in localStorage/sessionStorage (Application tab)

## Regression Testing

All changes should be validated against the full Lighthouse audit before deployment. Key regression checks:
- All 50 cards present and accessible
- Keyboard navigation functional
- Screen reader announcements firing
- Animations working
- Complete state triggering correctly

## Acceptance Testing

| Criterion | Method |
|---|---|
| Lighthouse 100 all categories | Automated Lighthouse audit |
| All 50 cards present | Card count assertion |
| All four modules covered | Category filter test |
| Screen reader usable | Manual VoiceOver/NVDA walkthrough |
| Mobile usable | Physical device test on iOS/Android |

---

# 16. Analytics and Metrics

## Current State

No analytics are implemented. This is intentional given the privacy-first design.

## Recommended Metrics (if analytics are added in future)

| Metric | Measurement |
|---|---|
| Session starts | Page load events |
| Cards reviewed per session | Mark event count |
| Completion rate | Complete state reach rate |
| Most studied skills | Aggregate learning marks per card |
| Filter usage | Category selection events |
| Expanded panel usage | Chevron click rate |
| Session duration | Time from load to last interaction |

**Privacy Recommendation:** If analytics are added, use a privacy-preserving, cookieless analytics tool (e.g., Plausible, Fathom) with no PII collection.

## Success Metrics

| Metric | Target |
|---|---|
| Lighthouse scores | 100 across all categories |
| File size | ≤ 150KB |
| Zero accessibility violations | 0 axe-core errors |
| Card content coverage | 50 / 50 skills documented |

---

# 17. Risks and Constraints

## Technical Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Google Fonts unavailable | Low | Low | System font fallback; functional without fonts |
| Browser 3D transform support gap | Very Low | Medium | All modern browsers support CSS 3D; no polyfill needed |
| Canvas API unavailable | Very Low | Low | Confetti simply doesn't play; non-critical feature |
| File size growth with content additions | Medium | Low | Monitor file size; consider content splitting if > 200KB |
| CSS :has() unsupported (used for dot brightness on flash) | Low | Very Low | Feature enhancement only; degraded gracefully |
| Lighthouse scoring changes | Medium | Medium | Pin to specific Lighthouse version for CI |

## Product Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Clinical inaccuracy of skill content | High | Content review by qualified DBT practitioner |
| Missing skills from Linehan curriculum | Medium | Full curriculum audit against source material |
| Skills described insufficiently for clinical use | Medium | Mark as study aid; not a replacement for formal training |

## Business Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Google Fonts deprecates endpoint | Medium | Self-host font files as fallback |
| Canonical domain not registered | Low | Update canonical URL or remove if not hosting |

## Legal Risks

| Risk | Likelihood | Mitigation |
|---|---|---|
| Clinical misuse without therapist oversight | Low | Add disclaimer text; not a medical device |
| Copyright of DBT curriculum | Low | Skill names are descriptive; content is explanatory (not copied from copyrighted source) |

## Known Limitations

1. **No cross-session persistence:** Progress resets on page refresh. Users must complete a session in one sitting to retain progress.
2. **No spaced repetition:** The app provides random-order recall without a scientifically optimised repetition schedule.
3. **English only:** No multilingual support.
4. **Dark mode only:** Light mode was removed; users in bright environments may find readability reduced.
5. **No audio:** No text-to-speech or audio support for definitions.
6. **No offline font loading:** Font requires network on first load; cached by browser thereafter.

---

# 18. Open Questions and Unknowns

## Content Questions

| # | Question | Why It Matters | Decision Depends On |
|---|---|---|---|
| OQ-01 | Has the card content been reviewed by a qualified DBT practitioner for clinical accuracy? | Inaccurate content could harm users relying on it for therapeutic practice | Clinical review process |
| OQ-02 | Are all 50 skills the complete canonical set per Linehan's 2015 manual? | Missing skills reduce completeness; extra skills may introduce inaccuracies | Content audit against source |
| OQ-03 | Should a clinical disclaimer be added to the application? | Manages liability and user expectations | Legal/clinical stakeholder decision |

## Product Questions

| # | Question | Why It Matters | Decision Depends On |
|---|---|---|---|
| OQ-04 | Should cross-session progress persistence be added? | Would significantly improve long-term learning value | Privacy vs. functionality trade-off |
| OQ-05 | Is spaced repetition (e.g., SM-2 algorithm) a future requirement? | Transforms the tool from simple flashcards to an evidence-based learning system | Product roadmap decision |
| OQ-06 | Is multilingual support required? | Affects architecture (i18n framework, content management) | Audience definition |
| OQ-07 | Should a therapist/educator mode be added? | Enable card projection, group session features | Stakeholder requirements |

## Technical Questions

| # | Question | Why It Matters | Decision Depends On |
|---|---|---|---|
| OQ-08 | What is the canonical hosting URL? | The canonical meta tag currently references `https://dbt-flashcards.app/` | Domain registration |
| OQ-09 | Should the application be distributed as a GitHub repository rather than a single file? | Enables version control, issues, contributions, CI/CD | Maintenance model decision |
| OQ-10 | Should fonts be self-hosted to remove the Google Fonts dependency? | Removes only external dependency; enables true offline use | Hosting strategy decision |
| OQ-11 | Is a Progressive Web App (PWA) implementation desired? | Enables installation and offline use without internet | Product requirements |

## Design Questions

| # | Question | Why It Matters | Decision Depends On |
|---|---|---|---|
| OQ-12 | Should "tap to reveal" / "tap to flip" hints remain visible or only show on first use? | Reducing noise for experienced users | UX preference |
| OQ-13 | Should the confetti shower (currently disabled) be re-enabled? | Aesthetic and celebration intensity | User preference testing |

---

# 19. Future Roadmap

## Near-term Enhancements (v1.x)

| Feature | Value |
|---|---|
| Cross-session persistence via localStorage | Retain progress between sessions |
| Clinical disclaimer / about modal | Manage user expectations |
| Self-hosted font (woff2) | Remove Google Fonts dependency; true offline |
| PWA manifest + service worker | Installable; fully offline |
| GitHub repository publication | Open-source distribution |

## Medium-term Enhancements (v2.x)

| Feature | Value |
|---|---|
| Spaced repetition algorithm (SM-2 or FSRS) | Evidence-based recall scheduling |
| Session statistics / review history | Learning analytics without PII |
| Custom card creation | User extensibility |
| Multiple deck profiles | Study different DBT workbook editions |
| Export/import progress | Backup and device transfer |

## Long-term Vision

| Feature | Value |
|---|---|
| Multilingual card content (Spanish, French, Mandarin, Arabic) | Global accessibility |
| Therapist portal | Share decks with clients; assign homework |
| Audio narration | Screen reader users and audio learners |
| Adaptive difficulty | Personalised card weighting based on performance |
| Integration with electronic health record (EHR) systems | Clinical workflow integration |

---

# 20. Assumptions Register

| ID | Assumption | Section | Impact if Wrong |
|---|---|---|---|
| A-01 | A single individual holds product/technical ownership | Section 3 | Multi-contributor workflow and governance needed |
| A-02 | Dark mode is the permanent design direction | Section 2 | Re-implementing light mode requires full contrast audit |
| A-03 | No cross-session persistence is acceptable | Section 6 | Architecture change needed if localStorage added |
| A-04 | 50 cards represents complete DBT skills coverage | Section 9 | Missing skills require content addition |
| A-05 | `https://dbt-flashcards.app/` is the intended canonical URL | Section 14 | SEO metadata needs updating |
| A-06 | Google Fonts will remain available and unchanged | Section 8 | Font self-hosting required as contingency |
| A-07 | Users access the app on modern browsers (Chrome 90+, Safari 14+, Firefox 88+) | Section 8 | Polyfills needed for older browsers |
| A-08 | `prefers-reduced-motion` implementation sufficiently covers vestibular disorder needs | Section 11 | Additional animation controls may be needed |
| A-09 | The confetti shower being disabled is a deliberate product decision | Section 5/FR-09 | Variable retained; re-enablement is one line change |
| A-10 | No server-side rendering, SSR, or pre-rendering is required | Section 7 | Architecture change for SEO beyond static file hosting |
| A-11 | The application will not be embedded in an iframe | Section 13 | X-Frame-Options header would need configuration |
| A-12 | Card content is authored in English and not translated | Section 6 | i18n architecture required for multilingual support |
| A-13 | Clinical accuracy of expanded panel content was not verified by a practitioner during development | Section 17 | Content review recommended before clinical deployment |

---

# 21. Glossary

| Term | Definition |
|---|---|
| **DBT** | Dialectical Behavior Therapy. A cognitive-behavioural treatment developed by Marsha Linehan, validated for borderline personality disorder and other conditions. |
| **Flashcard** | A learning device presenting a question or prompt on one side and the answer on the other, used for recall practice. |
| **Module** | One of the four major DBT skill groups: Mindfulness, Distress Tolerance, Emotion Regulation, Interpersonal Effectiveness. |
| **Got It** | User-assigned state indicating a card is mastered; stored in the `known` Set. |
| **Still Learning** | User-assigned state indicating a card requires more study; stored in the `learning` Set. |
| **Deck** | The ordered array of card objects currently being studied, filtered and shuffled from the master CARDS array. |
| **Expanded Panel** | The "More Info" section that slides open below the card back to show detailed clinical information. |
| **Roll-Up / Roll-Down** | The `scaleY` CSS animation used to open (roll down) or close (roll up) the expanded panel. |
| **Dot Row** | The row of coloured circles below the controls indicating card status and enabling drag-to-scrub navigation. |
| **Scrubbing** | The interaction of clicking and dragging (or touch and swiping) across the dot row to rapidly navigate between cards. |
| **catColors** | The JavaScript object mapping category keys to theme colour objects. |
| **CARDS** | The master JavaScript array of all 50 DBT skill objects — the canonical data source. |
| **Fisher-Yates** | The shuffle algorithm used to randomise the deck: iterates from the last element to the first, swapping each with a randomly chosen element at or before its position. |
| **backface-visibility** | CSS property that hides the reverse side of a 3D-transformed element, used to show only the correct face during card flip. |
| **aria-live** | ARIA attribute that marks a region for automatic screen reader announcement when its content changes. |
| **WCAG** | Web Content Accessibility Guidelines. The internationally recognised standard for web accessibility, published by the W3C. |
| **Lighthouse** | Google's automated tool for auditing web page quality across Performance, Accessibility, Best Practices, and SEO. |
| **axe-core** | The JavaScript accessibility testing engine used by Lighthouse's Accessibility audit. |
| **SM-2** | A spaced repetition algorithm developed by SuperMemo; schedules reviews based on recall performance. |
| **PWA** | Progressive Web App. A web application that can be installed on a device and function offline using service workers. |
| **LCP** | Largest Contentful Paint. A Core Web Vital measuring perceived loading performance. |
| **FCP** | First Contentful Paint. Measures when the first content element is rendered to screen. |
| **TBT** | Total Blocking Time. Measures how long the main thread is blocked during page load. |
| **FOIT/FOUT** | Flash of Invisible Text / Flash of Unstyled Text. Loading artefacts caused by web font loading delays. |
| **CSP** | Content Security Policy. An HTTP header that restricts what resources a page can load. |
| **PHI** | Protected Health Information. Patient data protected under HIPAA and similar regulations. |

---

# 22. Appendices

## Appendix A: Complete Card Inventory

All 50 cards currently in the CARDS array:

### Mindfulness Module (10 cards)

| Acronym | Title |
|---|---|
| WISE MIND | Wise Mind |
| WHAT | WHAT Skills of Mindfulness |
| HOW | HOW Skills of Mindfulness |
| OBSERVE | Observe |
| DESCRIBE | Describe |
| PARTICIPATE | Participate |
| NON-JUDGE | Non-judgmentally |
| ONE-MINDFUL | One-mindfully |
| EFFECTIVELY | Effectively |
| MINDFUL THOUGHTS | Mindfulness of Current Thoughts |

### Distress Tolerance Module (13 cards)

| Acronym | Title |
|---|---|
| CRISIS | Crisis Survival Overview |
| TIPP | TIPP — Change Body Chemistry |
| TEMP | Temperature |
| INTENSE EX | Intense Exercise |
| PACED BR | Paced Breathing |
| PMR | Paired Muscle Relaxation |
| ACCEPTS | Distract with ACCEPTS |
| SELF-SOOTHE | Self-Soothe with Five Senses |
| IMPROVE | IMPROVE the Moment |
| PROS & CONS | Pros and Cons |
| RADICAL ACC | Radical Acceptance |
| TURNING | Turning the Mind |
| WILLING | Willingness vs. Willfulness |
| HALF-SMILE | Half-Smiling and Willing Hands |

### Emotion Regulation Module (14 cards)

| Acronym | Title |
|---|---|
| EMOTION MODEL | Model of Emotions |
| FUNCTIONS | Function of Emotions |
| REDUCE VULN | Reduce Vulnerability |
| PLEASE | PLEASE Skills |
| ACCUMULATE + | Accumulate Positive Emotions |
| LIFE WORTH | Build a Life Worth Living |
| MASTERY | Build Mastery |
| COPE AHEAD | Cope Ahead |
| CHECK FACTS | Check the Facts |
| OPP ACTION | Opposite Action |
| PROBLEM SOLVE | Problem Solving |
| RIDE WAVE | Ride the Wave |
| MINDFUL EMOTION | Mindfulness of Current Emotion |
| LOVING KIND | Loving Kindness |

### Interpersonal Effectiveness Module (13 cards)

| Acronym | Title |
|---|---|
| GOALS | Goals in Interpersonal Situations |
| DEAR MAN | DEAR MAN |
| GIVE | GIVE |
| FAST | FAST |
| INTENSITY | Intensity of Asking |
| FIND PEOPLE | Finding and Getting Relationships |
| END RELATION | Ending Destructive Relationships |
| RELATION MINDFUL | Mindfulness in Relationships |
| VALIDATION | Validation |
| DIALECTICS | Dialectical Thinking |
| MIDDLE PATH | Walking the Middle Path |
| SELF-RESPECT | Self-Respect Effectiveness |

**Note:** Card count totals 50 (10 + 14 + 14 + 13 = 51). Discrepancy from stated "50 cards" should be audited — this may be an off-by-one in the narrative vs. actual data. **Confirmed requirement: the CARDS array is the source of truth.**

## Appendix B: CSS Animation Keyframes

| Name | Usage | Duration | Easing |
|---|---|---|---|
| `slideIn` | Card stage on navigation | 0.3s | ease |
| `modalIn` | Modal panel open | 0.25s | cubic-bezier(0.4,0,0.2,1) |
| `panelRollDown` | Expanded panel open | 0.32s | cubic-bezier(0,0,0.2,1) |
| `panelRollUp` | Expanded panel close | 0.32s | cubic-bezier(0.8,0,1,1) |
| `celebrationPop` | Complete state entrance | 0.55s | cubic-bezier(0.34,1.4,0.64,1) |
| `starSpin` | ✦ icon entrance | 0.65s | cubic-bezier(0.34,1.56,0.64,1) |
| `starFloat` | ✦ icon idle | 3s infinite | ease-in-out |
| `fadeSlideUp` | Complete state text stagger | 0.45s | ease |
| `swipeHintPulse` | (removed) | — | — |

## Appendix C: SEO Metadata

```html
<title>DBT Skills Flashcard Trainer — Dialectical Behavior Therapy</title>
<meta name="description" content="Practice all four DBT skill modules...">
<meta name="robots" content="index, follow">
<meta name="author" content="DBT Skills Flashcard Trainer">
<meta name="theme-color" content="#0d1117">
<meta name="color-scheme" content="dark">
<meta property="og:title" content="DBT Skills Flashcard Trainer">
<meta property="og:description" content="...">
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="DBT Skills Flashcard Trainer">
<meta name="twitter:description" content="...">
<link rel="canonical" href="https://dbt-flashcards.app/">
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "DBT Skills Flashcard Trainer",
  "applicationCategory": "EducationalApplication",
  "operatingSystem": "Any",
  "offers": { "@type": "Offer", "price": "0", "priceCurrency": "USD" }
}
</script>
```

## Appendix D: Favicon

Inline SVG data URI favicon: 32×32px dark background (#0d1117) with rounded corners (rx=8), teal card outline with two text line indicators. Embedded as `<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,...">`.

---

# 23. Clarification Questions

## Category A: Clinical Content

**CQ-A1:** Has the skill content (definitions, expanded detail, purpose descriptions) been reviewed and validated by a qualified DBT practitioner or certified DBT trainer?
- *Why it matters:* Clinical inaccuracy in a therapeutic learning tool could harm users. The content should be verified against Linehan's Skills Training Manual (2015).
- *Decision depends on:* Whether a clinical review process exists or needs to be established.

**CQ-A2:** Is the current 50-card set intended to represent complete coverage, or are additional skills expected to be added?
- *Why it matters:* The spec describes "50 cards" but the card inventory appears to total 51. The discrepancy must be resolved.
- *Decision depends on:* A definitive curriculum reference.

**CQ-A3:** Should a disclaimer be displayed stating that this is a study aid and not a replacement for formal DBT training or clinical care?
- *Why it matters:* Legal protection and user expectation management.
- *Decision depends on:* Legal and clinical stakeholder input.

## Category B: Persistence and Data

**CQ-B1:** Should session progress (Got It / Still Learning states) persist across page refreshes and return visits?
- *Why it matters:* Currently all progress is lost on page refresh. Adding localStorage would significantly improve the tool's value for ongoing learners.
- *Decision depends on:* Privacy policy and product requirements.

**CQ-B2:** If persistence is added, should it be per-browser/device (localStorage) or cross-device (account-based backend)?
- *Why it matters:* Determines whether a backend and authentication system need to be built.
- *Decision depends on:* Scope and complexity appetite.

## Category C: Hosting and Distribution

**CQ-C1:** Is `https://dbt-flashcards.app/` the confirmed canonical URL?
- *Why it matters:* SEO canonical tag currently references this domain. If the domain is not registered or used, the canonical tag should be updated or removed.
- *Decision depends on:* Domain registration status.

**CQ-C2:** Should the project be published as an open-source repository?
- *Why it matters:* Determines whether a public GitHub repository should be set up, which enables contributions, issue tracking, and versioned releases.
- *Decision depends on:* Licensing and open-source policy decision.

## Category D: Design and Features

**CQ-D1:** Should the application support light mode in the future, or is dark-only a permanent decision?
- *Why it matters:* Light mode was implemented and removed. If it's to return, the contrast palette work already done for light mode should be preserved or the decision to remove should be documented as permanent.
- *Decision depends on:* Accessibility requirements and user feedback.

**CQ-D2:** Is the confetti shower (`SHOWER_COUNT = 0`) disabled temporarily pending a design decision, or permanently removed?
- *Why it matters:* The code path remains in the source. If permanently removed, the code should be deleted for cleanliness.
- *Decision depends on:* UX preference.

**CQ-D3:** Should the keyboard shortcut hints (`←→ navigate Space flip G got it S still learning`) be shown to all users or only on first visit?
- *Why it matters:* Experienced users see hints they no longer need; new users benefit from them.
- *Decision depends on:* UX preference; would require localStorage if shown only once.

## Category E: Accessibility

**CQ-E1:** Has the application been tested with real assistive technology users beyond automated tooling?
- *Why it matters:* Automated tools catch ~30–40% of accessibility issues. Manual testing with screen readers is required for full AA conformance.
- *Decision depends on:* Accessibility testing resource availability.

---

*End of Project Specification Document*

*Document version: 1.0 | Built from iterative development history | June 2026*