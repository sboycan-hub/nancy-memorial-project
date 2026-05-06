# nancy.boycan.com — Build Execution Plan
## Version 1.1 — May 2026

This is the active build checklist. The Chrome extension updates checkboxes as steps are completed. This session and the main Claude chat session both reference this file.

**Status legend:** `[ ]` = not started | `[x]` = complete | `[~]` = in progress

---

## Step 0 — Install Remaining Plugins

Install before beginning any page work. Forms on Tributes, Memories, and Gallery depend on this.

- [ ] WPForms Lite — install and activate
- [ ] Confirm active: Crio theme
- [ ] Confirm active: Post and Page Builder by BoldGrid
- [ ] Confirm active: MetaSlider
- [ ] Confirm active: MailPoet
- [ ] Confirm active: Total Upkeep

---

## Step 1 — Theme & Visual Style

Configure Crio theme settings. Everything built after this inherits these styles.

- [ ] Color palette: soft creams, warm grays, gentle blues/greens
- [ ] Typography — Headings: Playfair Display | Body: Lora or Merriweather (Google Fonts via Appearance → Customize → Typography)
- [ ] Text alignment: left-aligned body text (not justified)
- [ ] Header layout: Nancy's name prominent, dates as subtitle
- [ ] Footer layout: placeholder for Privacy Policy, subscribe reminder, site credit
- [ ] Mobile responsiveness: verify layout on phone view

---

## Step 2 — Home Page Layout

Build full Home page structure using BoldGrid Page Builder. Top to bottom:

- [ ] Site header block: Nancy Eileen Boycan / October 26, 1942 – May 2, 2025 / "A Memorial"
- [ ] MetaSlider placeholder block (slideshow embedded in Step 3)
- [ ] Intro paragraph block (non-collapsible): opening two sentences from obituary
- [ ] Accordion block — 11 sections in order:
  - [ ] Early Life
  - [ ] Family
  - [ ] A Career That Broke Ground
  - [ ] The Good Times
  - [ ] The Animals
  - [ ] Her Generosity
  - [ ] Faith
  - [ ] Her Final Fight
  - [ ] Her Wishes
  - [ ] Survivors
  - [ ] A Note to Those Who Knew Her
- [ ] Paste full obituary text into each accordion section (from Nancy_Obituary.md)
- [ ] MailPoet subscribe box at bottom of page

---

## Step 3 — MetaSlider Setup

- [ ] Create new slider in MetaSlider
- [ ] Set transition: fade
- [ ] Set interval: 5–7 seconds
- [ ] Add 1–2 placeholder/test photos from Media Library
- [ ] Embed slider into Home page designated block
- [ ] Verify display on desktop and mobile

---

## Step 4 — Tributes Page

Longer written pieces. Display + submission form + moderation.

- [ ] Page layout: title, brief description
- [ ] Display area: contributor name, relationship, tribute text — most recent first
- [ ] Pre-load Gary Boycan's tribute as first entry (text in Gary_Boycan_Tribute.md)
- [ ] WPForms Lite form — fields: Name (required), Relationship (required), Tribute text (required)
- [ ] Form moderation: hold for approval before publishing
- [ ] Configure form: admin notification email to Steve on each submission

---

## Step 5 — Memories Page

Shorter recollections — guest book style.

- [ ] Page layout: title, brief description
- [ ] Display area: contributor name, optional date/place, memory text
- [ ] WPForms Lite form — fields: Name (required), Relationship (optional), Date or Place (optional), Memory (required)
- [ ] Form moderation: hold for approval
- [ ] Configure form: admin notification email to Steve on each submission

---

## Step 6 — Gallery Page

Photos with attribution, moderated.

- [ ] Page layout: title, description, gallery grid above form
- [ ] Gallery display: grid/masonry, lightbox on click, contributor name + caption per photo
- [ ] WPForms Lite form — fields: Name (required), Relationship to Nancy (optional), Photo upload (required), Caption (optional)
- [ ] Form moderation: hold for Steve approval
- [ ] Configure form: admin notification email to Steve on each submission
- [ ] NOTE: Gallery is separate from Home page MetaSlider slideshow

---

## Step 7 — Events Page

Placeholder now. Update when memorial arrangements confirmed.

- [ ] Add placeholder text: "Nancy asked to be celebrated, not mourned. A memorial gathering is being planned. Details will be posted here when arrangements are confirmed — check back or subscribe below to be notified."
- [ ] Add subscribe link below placeholder text

---

## Step 8 — Links Page

Curated links — Steve controls entirely.

- [ ] GoFundMe section: placeholder URL, brief description
- [ ] NETRF — Neuroendocrine Tumor Research Foundation — netrf.org
- [ ] Sepsis Alliance — sepsis.org
- [ ] Trout Unlimited — tu.org
- [ ] National Wildlife Federation — nwf.org
- [ ] Brief description under each charity explaining connection to Nancy

---

## Step 9 — Footer

Appears sitewide on all pages.

- [ ] Privacy Policy link
- [ ] Subscribe reminder
- [ ] Site credit line
- [ ] Verify footer on all six pages

---

## Step 10 — MailPoet Configuration

Subscriber list management and automated notifications.

- [ ] Configure sender name and email (Steve's)
- [ ] Understand: MailPoet maintains full subscriber list in WordPress dashboard (MailPoet → Subscribers)
- [ ] Visitor flow: enter email → double opt-in confirmation email → added to list
- [ ] Set up subscription form on Home page
- [ ] Set up subscription form in footer — sitewide
- [ ] Configure subscriber notifications: alert list when new tribute approved, new event posted
- [ ] Coordinate admin notifications with WPForms Lite (Steps 4–6) to avoid duplicates
- [ ] Test full flow: submit → Steve notified → approve → appears on site → subscribers notified

---

*Last updated: May 2026*
