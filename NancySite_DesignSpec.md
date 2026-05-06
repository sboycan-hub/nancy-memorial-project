# nancy.boycan.com — Site Design Specification
## Version 3.0 — May 2026

Reference document for Claude chat and Chrome extension sessions. Contains full project context.

---

## 1. Project Overview

| Field | Detail |
|-------|--------|
| Site URL | nancy.boycan.com |
| Parent domain | boycan.com (Boycan family hub) |
| Purpose | Memorial website for Nancy Eileen Boycan |
| Subject | Nancy Eileen Boycan, October 26, 1942 – May 2, 2025 |
| Audience | Family and friends of all ages — keep UX simple and accessible |
| Hosting | InMotion Hosting, cPanel |
| Platform | WordPress |
| Theme | Crio by BoldGrid |
| Page Builder | Post and Page Builder by BoldGrid |
| Admin | Steve Boycan (sole administrator) |
| Admin URL | nancy.boycan.com/wp-admin |
| Future use | Template for other Boycan family memorials |

---

## 2. Plugins

| Plugin | Purpose | Status |
|--------|---------|--------|
| Post and Page Builder by BoldGrid | Drag-and-drop page layout | Installed |
| Crio theme | Base theme | Installed |
| MetaSlider | Rotating photo slideshow | Installed |
| MailPoet | Email subscriptions and notifications | Installed |
| Total Upkeep | Automatic backups | Installed |
| WPForms Lite | Submission forms for Tributes, Memories, Gallery | To install |

---

## 3. Site Structure

### 3.1 Home Page (static front page)

Layout top to bottom:

**A. Site Header**
- Name: Nancy Eileen Boycan
- Dates: October 26, 1942 – May 2, 2025
- Subtitle: A Memorial

**B. Rotating Photo Slideshow (MetaSlider)**
- Full-width banner slideshow
- Photos from WordPress Media Library
- Transition: fade
- Interval: 5–7 seconds (adjustable)
- Steve manages photos via Media Library — no coding needed
- Framework built now, photos added over time

**C. Intro Paragraph (non-collapsible)**
> Nancy Eileen Boycan, 82, of Reston, Virginia, passed away on May 2, 2025. She was a woman who moved through life on her own terms — a pioneer in her profession, a devoted mother, a friend to every creature she encountered, and a person of great heart.

**D. Accordion Obituary (11 sections)**

All sections collapsed by default. User clicks to expand.

1. Early Life
2. Family
3. A Career That Broke Ground
4. The Good Times
5. The Animals
6. Her Generosity
7. Faith
8. Her Final Fight
9. Her Wishes
10. Survivors
11. A Note to Those Who Knew Her

Full text in Nancy_Obituary.md

**E. MailPoet Subscribe Box**
> Stay informed — enter your email to receive updates when new tributes, memories, or events are posted.

---

### 3.2 Tributes Page

Longer written pieces from people who knew Nancy.

**Display:** Contributor name, relationship to Nancy, full tribute text. Most recent first. First entry: Gary Boycan's tribute (text in Gary_Boycan_Tribute.md).

**Submission form (WPForms Lite):**
- Your name (required)
- Your relationship to Nancy (required)
- Your tribute (large text area, required)

**Moderation:** Hold for approval → Steve approves in dashboard → admin notification email on each submission.

---

### 3.3 Memories Page

Shorter recollections — guest book style. Lower barrier than a full tribute.

**Display:** Contributor name, optional date/place context, memory text.

**Submission form (WPForms Lite):**
- Your name (required)
- Your relationship to Nancy (optional)
- Date or place (optional — e.g. "Summer at Reston lakes, 1985")
- Your memory (text area, required)

**Moderation:** Hold for approval → admin notification email on each submission.

---

### 3.4 Gallery Page

Photos contributed by family and friends, attributed to submitter.

**Display:** Grid or masonry layout, lightbox on click, contributor name + optional caption per photo.

**Submission form (WPForms Lite):**
- Your name (required)
- Your relationship to Nancy (optional)
- Photo upload (required — one photo per submission)
- Caption (optional)

**Moderation:** Hold for Steve approval → admin notification email on each submission.

**NOTE:** Gallery page is separate from the Home page MetaSlider slideshow. Steve manually selects slideshow photos via MetaSlider.

---

### 3.5 Events Page

Currently a placeholder. Update when memorial arrangements are confirmed.

**Placeholder text:**
> Nancy asked to be celebrated, not mourned. A memorial gathering is being planned. Details will be posted here when arrangements are confirmed — check back or subscribe below to be notified.

**Planned event:** Memorial celebration/party (not a somber service). Nancy's ashes to be placed in a trout stream. Date, time, location TBD.

---

### 3.6 Links Page

Curated links — Steve controls entirely, no submissions.

**GoFundMe**
Help cover Nancy's final expenses. Any excess donated to causes she loved.
*(URL to be added when GoFundMe is created)*

**Charities — In Her Memory**
- Neuroendocrine Tumor Research Foundation (NETRF) — netrf.org — her cancer diagnosis
- Sepsis Alliance — sepsis.org — MRSA and sepsis awareness
- Trout Unlimited — tu.org — wild trout conservation (Nancy requested ashes in a trout stream)
- National Wildlife Federation — nwf.org — wildlife conservation

---

## 4. Design & Visual Style

| Element | Decision |
|---------|----------|
| Tone | Warm, dignified, personal |
| Heading font | Playfair Display (Google Fonts) |
| Body font | Lora or Merriweather (Google Fonts) — final choice TBD |
| Text alignment | Left-aligned — not justified |
| Color palette | Soft creams, warm grays, gentle blues/greens — exact hex values TBD in Step 1 |
| Mobile | Essential — many visitors older, on phones |
| Navigation | Simple top menu — 6 items |
| Sidebar | Minimal or none |
| Footer | Privacy Policy, subscribe reminder, site credit |

**Typography rationale:** Georgia and formal serif fonts were considered and rejected as too stiff. Playfair Display + Lora/Merriweather reads more like a personal book than a corporate document.

**Decisions pending:**
- Final choice between Lora and Merriweather for body text
- Exact color hex values (set during Step 1)
- Whether first accordion section opens by default or all start collapsed

### Design Change Log

| Date | Element | Change | Session |
|------|---------|--------|--------|
| May 2026 | Typography | Playfair Display headings + Lora/Merriweather body selected | Claude chat |
| May 2026 | Text alignment | Changed from justified to left-aligned | Chrome extension |

---

## 5. Email & Notifications (MailPoet)

**Subscriber list:**
- Maintained inside WordPress — MailPoet → Subscribers
- Visitor enters email → double opt-in confirmation → added to list
- Steve manages list in dashboard — can view, export, remove subscribers
- Free tier supports up to 1,000 subscribers

**Subscriber notifications:**
- New tribute approved → notify list
- New event posted → notify list
- General site updates as needed

**Admin notifications (Steve):**
- New tribute submitted → email to Steve
- New memory submitted → email to Steve
- New gallery photo submitted → email to Steve
- Configured via WPForms Lite notification settings per form

---

## 6. Content Status

### Ready
- Full obituary — Nancy_Obituary.md (Draft 8, two placeholders remain)
- Gary Boycan tribute — Gary_Boycan_Tribute.md
- GoFundMe appeal text — written, ready to post once GoFundMe URL created
- Charity list — finalized

### Placeholders in obituary
- Grove City College major (Steve to verify)
- Virginia Tech field of study (Steve to verify)
- Sibling details: Barbara's last name, Sharon Eisnor — confirm spelling

### Still to gather
- Photos for slideshow and gallery — being collected over time
- Memorial event details — date, time, location TBD
- GoFundMe URL — once created

---

## 7. GitHub Repository Files

All project documents stored in the nancy-memorial-project repository (account: sboycan-hub). Design decisions are logged in Section 4 of this file — no separate design decisions document.

| File | Purpose |
|------|---------|
| Nancy_Obituary.md | Full obituary text, current draft |
| Gary_Boycan_Tribute.md | Gary's written tribute — first Tributes entry |
| NancySite_BuildPlan.md | Step-by-step build checklist with completion status |
| NancySite_DesignSpec.md | This file — full project reference and design decisions |

---

*nancy.boycan.com • Design Spec v3.0 • May 2026*
