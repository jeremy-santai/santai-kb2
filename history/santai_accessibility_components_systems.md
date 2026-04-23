# Santai Context: Accessibility + Component Systems for Web UI

## Metadata
- title: Accessibility + Component Systems for Web UI
- format: santai_context
- type: design_principles
- domain: ui-ux
- sources:
  - https://danielbeadle.medium.com/7-qualities-of-a-great-website-ab43520544a1
  - https://www.w3.org/WAI/fundamentals/accessibility-intro/
  - https://www.ada.gov/resources/web-guidance/
  - https://askearn.org/page/10-tips-for-an-accessible-website
  - https://m3.material.io/components
  - https://www.figma.com/best-practices/components-styles-and-shared-libraries/
- attempted_but_not_fully_readable:
  - https://www.ecomback.com/blogs/accessibility-standards-for-websites
- created_at: 2026-04-15
- intended_use:
  - agent_reference
  - UI generation defaults
  - accessibility review
  - design-system planning
  - component-library governance
- confidence: high
- synthesis_method: combine accessibility requirements + practical website quality + component-library best practices into agent-actionable rules

---

## Purpose

This file translates accessibility guidance, website quality criteria, and design-system/component-library best practices into a format agents can use while generating or reviewing UI.

Use it when:
- designing websites or product surfaces
- reviewing screens for accessibility issues
- building reusable component systems
- deciding when to abstract patterns into components
- making interfaces clearer, safer, and more maintainable

Core idea:
> A strong interface is understandable, accessible, reusable, and trustworthy.

---

## Section A — Accessibility Principles

### 1) Accessibility is not optional
**Meaning**
Web accessibility is a baseline quality requirement, not an optional enhancement.

**Why it matters**
People with disabilities must be able to perceive, understand, navigate, interact with, and contribute to the web. Accessibility also helps older users, people with temporary impairments, people in bright sunlight, people with limited bandwidth, and users on different devices.

**Example**
- Bad: designing only for mouse users with perfect vision on desktop
- Good: designing for keyboard use, readable contrast, captions, and responsive layouts

**Agent rule**
Default to inclusive interaction patterns unless the user explicitly requests a narrow prototype.

**Implementation heuristics**
- Assume diverse users and contexts
- Treat inaccessible patterns as defects, not edge cases
- Do not gate core flows behind one sensory mode or one input mode

---

### 2) Keyboard access is a first-class requirement
**Meaning**
Users must be able to navigate and operate the interface without a mouse.

**Example**
- Bad: custom dropdown only opens on hover and cannot be reached with Tab
- Good: all interactive controls are reachable by keyboard with visible focus states

**Agent rule**
If a user can click it, a keyboard user should also be able to reach and use it.

**Implementation heuristics**
- Ensure logical tab order
- Avoid keyboard traps
- Make focus indicators visible
- Do not rely on hover as the only mechanism

---

### 3) Structure the page for screen readers
**Meaning**
Page structure should communicate meaning to assistive technology.

**Example**
- Bad: a page visually looks organized but is built from unlabeled generic containers
- Good: headings, lists, labels, and navigation regions reflect the actual information hierarchy

**Agent rule**
Semantic structure should match visual structure.

**Implementation heuristics**
- Use clear headings in order
- Label navigation and forms clearly
- Use lists for list-like content
- Ensure controls have meaningful accessible names

---

### 4) Always include text alternatives for non-text content
**Meaning**
Images, icons, charts, and media need text equivalents when they convey information.

**Example**
- Bad: a product image with no alt text
- Good: alt text that describes the image’s relevant purpose, plus captions/transcripts for media

**Agent rule**
If a visual element communicates something necessary, provide a text path to that meaning.

**Implementation heuristics**
- Add alt text for informative images
- Mark decorative visuals as decorative when appropriate
- Add captions and transcripts for media
- Do not encode essential meaning only in imagery

---

### 5) Forms must be explicitly labeled and forgiving
**Meaning**
Forms need clear labels, instructions, and recoverable errors.

**Example**
- Bad: placeholder-only inputs with generic “invalid” messages
- Good: explicit labels, plain instructions, and field-specific validation feedback

**Agent rule**
Never make users guess what a field means or why submission failed.

**Implementation heuristics**
- Pair each field with a clear label
- Provide instructions where format is not obvious
- Surface error states clearly
- Keep form flows understandable with screen readers and keyboards

---

### 6) Contrast and readability are foundational
**Meaning**
Text and controls must be easy to read and distinguish.

**Example**
- Bad: light gray text on white, tiny labels, weak state differences
- Good: readable text sizes, clear contrast, visible interaction states

**Agent rule**
If content is hard to perceive, the design is not done.

**Implementation heuristics**
- Favor readable font sizes
- Ensure text-background contrast is strong
- Do not rely on color alone to communicate status
- Break up dense text with headings and chunks

---

### 7) Avoid inaccessible motion and time pressure
**Meaning**
Moving content and time limits can create barriers.

**Example**
- Bad: auto-rotating carousel with no pause, short expiration timer with no extension
- Good: pause/stop controls and flexible time limits for tasks

**Agent rule**
Do not force users to race the interface.

**Implementation heuristics**
- Provide pause/stop for moving content
- Avoid excessive flashing
- Let users extend or disable time limits where feasible

---

### 8) Use plain language
**Meaning**
Simple, concise language improves comprehension for everyone, including users with cognitive and learning disabilities.

**Example**
- Bad: jargon-heavy error text like “authentication token invalidated”
- Good: “Your sign-in link expired. Request a new one.”

**Agent rule**
Choose wording users can understand on the first pass.

**Implementation heuristics**
- Prefer direct verbs
- Reduce jargon
- Explain technical states in user terms
- Keep microcopy short and actionable

---

### 9) Downloads and attachments must also be accessible
**Meaning**
Accessibility does not stop at the webpage. Files linked from it need the same care.

**Example**
- Bad: important instructions only in an inaccessible PDF
- Good: HTML-first content when possible, or accessible downloadable files when necessary

**Agent rule**
Do not move essential content into inaccessible attachments.

**Implementation heuristics**
- Prefer native HTML for critical content
- Audit downloadable docs before publishing
- Preserve headings, reading order, and alt text in attached documents

---

### 10) Accessibility supports legal compliance and trust
**Meaning**
For many organizations, especially public entities and businesses open to the public, inaccessible web content creates compliance risk in addition to usability harm.

**Example**
- Bad: online registration flow that only works with a mouse and unlabeled fields
- Good: accessible services, forms, and communications across web experiences

**Agent rule**
Treat accessibility as both user care and risk reduction.

**Implementation heuristics**
- Build accessibility into default patterns
- Audit critical public-facing flows first
- Use WCAG-based review as a practical benchmark

---

## Section B — Website Quality Principles

### 11) Purpose should be obvious immediately
**Meaning**
A site should quickly explain what it is, who it serves, and why it matters.

**Example**
- Bad: a homepage opens with stylish visuals but unclear value
- Good: clear headline, supporting statement, and next step

**Agent rule**
The user should know what this interface is for within seconds.

**Implementation heuristics**
- Clarify value early
- Avoid abstract hero sections with no message
- Align opening copy with the target audience’s need

---

### 12) Branding and visual tone should be coherent
**Meaning**
Color, hierarchy, imagery, and layout should reinforce a consistent identity.

**Example**
- Bad: random visual styles across pages
- Good: a stable, recognizable tone that matches audience expectations

**Agent rule**
Use brand expression to support comprehension, not overpower it.

**Implementation heuristics**
- Keep typography, color, and imagery aligned
- Match visual tone to product and audience
- Avoid style shifts that reduce trust

---

### 13) Information architecture should feel intuitive
**Meaning**
Users should be able to find what they need without guessing.

**Example**
- Bad: dead ends, confusing categories, scattered related content
- Good: predictable organization and connected flows

**Agent rule**
Navigation should feel discoverable and unsurprising.

**Implementation heuristics**
- Group related pages logically
- Keep navigation labels concrete
- Reduce dead ends and orphaned pages
- Connect flows to likely next steps

---

### 14) Typography should support consumption, not decoration
**Meaning**
Type size, line length, line height, and emphasis patterns should help users read comfortably.

**Example**
- Bad: long dense paragraphs with weak contrast and no structure
- Good: readable text blocks with subheads, bullets, and emphasis where useful

**Agent rule**
Make content easy to consume at a glance and readable in depth.

**Implementation heuristics**
- Limit line length
- Use enough line height
- Break text into chunks
- Use consistent type ramps across breakpoints

---

### 15) Imagery should reinforce meaning
**Meaning**
Images, icons, and graphics should support the story of the page.

**Example**
- Bad: generic stock photos that add noise
- Good: visuals that clarify the product, audience, or message

**Agent rule**
Do not add images that only decorate but do not help.

**Implementation heuristics**
- Choose imagery with communicative purpose
- Keep icon style consistent
- Ensure graphics match brand and content tone

---

### 16) Responsive behavior should preserve usability
**Meaning**
Content and actions must still work well across devices and screen sizes.

**Example**
- Bad: a mobile layout that hides key content or requires zooming
- Good: reflowed layouts, preserved hierarchy, and touch-friendly actions

**Agent rule**
Do not solve responsive design by removing important meaning.

**Implementation heuristics**
- Reflow content thoughtfully
- Preserve key actions at all sizes
- Make targets comfortable for touch
- Test whether tables, nav, and cards degrade gracefully

---

### 17) Every important page needs a clear next step
**Meaning**
Interfaces should guide users toward the intended action.

**Example**
- Bad: attractive page with no obvious action
- Good: one visible CTA with clear benefit

**Agent rule**
A page without direction leaves users stranded.

**Implementation heuristics**
- Give each page a primary action
- Use specific CTA text
- Reduce competing actions
- Place CTA where user intent peaks

---

## Section C — Component Systems and Shared Libraries

### 18) Repetition is a signal to abstract
**Meaning**
Once an element appears across multiple screens, it should likely become a reusable component.

**Example**
- Bad: hand-building every button, input, and card separately
- Good: turning repeated UI into shared components early enough to save time

**Agent rule**
If a pattern appears more than once, consider componentizing it.

**Implementation heuristics**
- Promote repeated UI to components
- Do not over-engineer one-off exploration too early
- Abstract when consistency and speed benefits become clear

---

### 19) Components should be easy to update globally
**Meaning**
Reusable components are valuable because a single change can propagate across many screens.

**Example**
- Bad: changing a button color in 27 places manually
- Good: updating the main button component once and pushing the change system-wide

**Agent rule**
Prefer structures that centralize future edits.

**Implementation heuristics**
- Use instances of shared components
- Keep the source of truth clear
- Publish updates intentionally

---

### 20) Shared libraries should optimize for the people using them
**Meaning**
A library is successful when designers and developers can find the right thing quickly and understand how to use it.

**Example**
- Bad: one giant undifferentiated library with noisy internals exposed
- Good: the right library enabled for the right team, with discoverable structure and clear usage guidance

**Agent rule**
Treat consumers of the design system as end users.

**Implementation heuristics**
- Publish only what downstream users need
- Hide low-level implementation-only pieces when appropriate
- Organize libraries by platform, product, or team when scale demands it

---

### 21) Name components and styles so humans can scan them
**Meaning**
Naming is part of usability for design systems.

**Example**
- Bad: vague names like “blue 2” or “thing-final-final”
- Good: names that reflect purpose, hierarchy, or code alignment

**Agent rule**
A good naming scheme reduces search time and misuse.

**Implementation heuristics**
- Use predictable naming patterns
- Group related styles/components consistently
- Align names with code concepts where helpful
- Prefer scan-friendly names over clever ones

---

### 22) Add descriptions to teach correct usage
**Meaning**
Metadata around components and styles reduces misuse.

**Example**
- Bad: designers guess which button variant to use
- Good: hover descriptions explain intended usage and constraints

**Agent rule**
Document the intended use where the choice is made.

**Implementation heuristics**
- Add descriptions for main components
- Add descriptions for styles when usage is ambiguous
- Clarify when something is primary, secondary, destructive, mobile-only, etc.

---

### 23) Constraints and layout behavior should be predictable
**Meaning**
Reusable UI should resize and adapt in deliberate ways.

**Example**
- Bad: a card breaks when stretched or shrunk
- Good: constraints and grids preserve margins, padding, and internal alignment

**Agent rule**
A reusable component should behave well under common resize scenarios.

**Implementation heuristics**
- Set constraints intentionally
- Use grids to visualize spacing
- Test components in multiple sizes and content states

---

### 24) Separate styles from one-off visual values
**Meaning**
Colors, type styles, effects, and grids should be reusable system assets rather than repeatedly hardcoded values.

**Example**
- Bad: manually entering font sizes and hex values screen by screen
- Good: shared text styles, color styles, effect styles, and layout grids

**Agent rule**
Abstract reusable design decisions into reusable style primitives.

**Implementation heuristics**
- Maintain shared color styles
- Maintain shared type ramps
- Reuse effect and elevation styles
- Standardize layout grids across viewports

---

### 25) Organize libraries to scale
**Meaning**
Library structure that works for a small team may become noisy at larger scale.

**Example**
- Bad: every team consumes the same giant asset library regardless of need
- Good: separate libraries by platform or audience when it improves focus

**Agent rule**
Optimize the library topology for scale, not just for simplicity.

**Implementation heuristics**
- Use one library when scope is small and shared
- Split libraries when size creates search overhead
- Keep library access scoped to what teams actually need

---

### 26) Match design-system structure to implementation reality
**Meaning**
The organization of styles and components should help handoff to code, not fight it.

**Example**
- Bad: design names that have no correspondence to product implementation
- Good: style names and component groups that map cleanly to design and code usage

**Agent rule**
Prefer system structures that improve design-dev alignment.

**Implementation heuristics**
- Use naming that can map to code comments/tokens
- Keep organization consistent across design and implementation
- Avoid semantic drift between the Figma system and the product system

---

### 27) Use components as interactive building blocks, not decoration
**Meaning**
A component system is meant to support real tasks, actions, and flows.

**Example**
- Bad: collecting component variants without a clear product use case
- Good: using components to solve repeated interface needs like buttons, search, cards, menus, app bars, and lists

**Agent rule**
Start from user tasks, then choose or build the right component.

**Implementation heuristics**
- Prefer purpose-based components
- Avoid unnecessary variants
- Keep component APIs understandable
- Reuse standard interaction patterns for common actions

---

## Agent Decision Framework

When generating or reviewing accessible UI, check in this order:

### Pass 1 — Core access
- Can the interface be used with keyboard only?
- Are headings, labels, and semantics clear?
- Are media and images represented accessibly?

### Pass 2 — Readability
- Is text readable in size, contrast, and structure?
- Is language plain enough for first-pass understanding?
- Are error states and instructions understandable?

### Pass 3 — Flow
- Is the site’s purpose obvious?
- Can users find information predictably?
- Is the next action clear?

### Pass 4 — Reuse
- Are repeated patterns abstracted into components?
- Are shared styles defined instead of repeated manually?
- Is the component/library structure understandable?

### Pass 5 — Trust and risk
- Would this experience exclude or surprise users?
- Does it create avoidable legal/compliance exposure?
- Are design choices respectful of user control and capability?

---

## Default Agent Behaviors

When the prompt is vague, default to:
1. semantic structure
2. keyboard-friendly interactions
3. labeled forms
4. readable contrast and typography
5. captions/transcripts for media
6. clear CTAs
7. intuitive IA and navigation
8. reusable components for repeated patterns
9. shared styles for color/type/elevation/grid
10. system naming that humans can scan

---

## Anti-Patterns

Avoid by default:
- click targets reachable only by mouse
- placeholder-only forms
- inaccessible carousels and autoplay motion
- weak contrast and tiny body text
- decorative images with no purpose
- content buried in inaccessible downloads
- giant undifferentiated libraries
- unclear component names
- repeated hardcoded visual values
- multiple competing CTAs with no primary action

---

## Compact Review Checklist

- keyboard usable?
- focus visible?
- headings structured?
- images described?
- forms labeled?
- errors clear?
- captions/transcripts present?
- contrast strong?
- copy plain?
- purpose obvious?
- navigation intuitive?
- CTA obvious?
- responsive behavior preserved?
- repeated patterns componentized?
- styles reusable?
- library easy to use?

---

## Source Mapping

- W3C WAI contributed: definition of accessibility, broad inclusion framing, and the idea that accessibility supports many users beyond permanent disability
- ADA.gov contributed: U.S. legal applicability for state/local governments and public accommodations, plus practical examples like forms, labels, keyboard navigation, and use of WCAG as guidance
- AskEARN contributed: practical accessibility checklist items like screen reader structure, alt text, keyboard access, moving/timed content controls, labeled forms, contrast, accessible downloads, plain language, and captions
- Daniel Beadle contributed: website purpose, branding coherence, architecture, typography, imagery, responsiveness, and call-to-action clarity
- Figma contributed: when to create components, shared libraries, descriptions, constraints, shared styles, naming, organization, and scaling library structure
- Material Design contributed: the framing of components as reusable interactive building blocks for common UI tasks

---

## Notes / Limitations

- One provided source (ecomback.com) was not fully readable during capture, so it was not treated as a primary basis for synthesis.
- This file is a practical design-and-review guide, not legal advice.
- For implementation-specific audits, pair these principles with WCAG success criteria and real testing.

---

## Mental Model

Accessible design and system design are connected.

Accessibility ensures:
- people can use the interface

Design systems ensure:
- teams can build the interface consistently

For agents:
> Build UI that more people can use, and that your team can maintain without chaos.
