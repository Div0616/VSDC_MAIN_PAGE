# Prompt: Build the "VighnoLearn" Landing Page

Build a complete, pixel-accurate, responsive landing page for an ed-tech platform called **VighnoLearn**. Use React + Tailwind CSS (or plain HTML/CSS/JS if no framework is specified). Follow every spec below exactly — colors, gradients, typography, spacing, and structure — rather than using generic defaults.

---

## 1. Global Design System

### Color Palette (exact hex values, extracted from source design)

**Backgrounds**
- `--bg-nav`: `#0f131c` — flat near-black navy, used only behind the top navigation bar
- `--bg-hero-base`: `#0e0701` — near-black warm brown, hero section base
- `--bg-hero-glow`: `#201003` to `#2a1505` — lighter warm brown, radial glow origin
- `--bg-page`: `#120701` to `#1b0d02` — the warm black-brown used across "Who Should Join," "Popular Courses," and CTA sections
- `--bg-pure-black`: `#000000` — behind course thumbnail images and CTA/footer base
- `--bg-course-card`: `#000000` with a very faint cool-toned border `#0b1a1f`

**Background gradient logic:** The entire page (nav excluded) sits on a **radial gradient**, warm amber-brown glow fading to near-black:
```css
background: radial-gradient(ellipse at 75% 20%, #2a1505 0%, #1b0d02 40%, #0e0701 100%);
```

**Brand Orange (primary accent)**
- `--orange-primary`: `#f97216` (core brand orange — buttons, logo accent, prices, star ratings, headline emphasis words)
- `--orange-muted`: `#d67c3e` / `#da7b37` (secondary/shading tone within gradients and badges)
- `--orange-light`: `#fff1c6` / `#ffeabc` (highlight edge on gradient buttons)

**Feature Card Maroon (radial gradient, NOT flat)**
- Card center: `#561416`
- Card edge/corner: `#2f0b0b` → `#180c0e`
```css
background: radial-gradient(circle at center, #5c1518 0%, #2a0d0c 100%);
```
- Icon chip inside cards: dark plum `#241419` to `#2a1b20`, rounded-square, white line icon centered

**CTA Button gradient** ("Get Free Membership" — this one IS a left-to-right gradient, unlike other flat orange buttons):
```css
background: linear-gradient(90deg, #f97216 0%, #d57c40 60%, #c2703a 100%);
```

**Text Colors**
- Headline white: `#ffffff`
- Body copy (warm off-white): `#e5e0da` to `#c9c4bd`
- Footer headings: `#ffffff`
- Footer body/links (muted warm grey): `#9d9592`
- Social icon circle background: dark slate `#1e293b` / `#20283b`, white icon glyph

---

## 2. Typography

- **Headings** (hero H1, section titles "Who Should Join VighnoLearn?", "Popular Courses", "Ready to Start Building?"): bold, geometric/rounded sans-serif, heavy weight (700–800), tight letter-spacing. Use **Poppins** (Bold/ExtraBold) or **Sora** (Bold) from Google Fonts.
- **Italic accent word** ("*Start Building*" in the closing CTA): same heading font, italic, orange color.
- **Body/paragraph text**: regular weight (400), humanist sans-serif with high x-height. Use **Inter** or **Roboto**.
- **Logo "VighnoLearn"**: rounded semi-bold sans (Poppins SemiBold), two-tone — "Vighno" in white, "Learn" in orange `#f97216`.
- **Buttons & labels**: medium-bold (600), heading font family.
- **Footer column headers** ("PLATFORM", "COMMUNITY", "ORGANIZATION", "RESOURCES"): uppercase, small size, letter-spacing ~0.05em, white, semi-bold.
- **Price text** (₹89.00): bold, orange, heading font.

Suggested font imports:
```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&family=Inter:wght@400;500;600&display=swap');
```

---

## 3. Structural Layout (top to bottom)

### 3.1 Navigation Bar
- Full-width, flat background `#0f131c`, no gradient
- Left: logo icon (small orange arrow/checkmark glyph) + "VighnoLearn" wordmark (white + orange split)
- Center: nav links — About, Courses, Events, Contact Us, Join (light grey/white, regular weight)
- Right: "Log In" as plain text link in orange, "Sign Up" as solid orange pill button with white text
- Sticky/fixed on scroll (assume yes for a modern landing page)

### 3.2 Hero Section
- Background: radial gradient warm-brown-to-black (see §1)
- Small pill badge top-left: "The Future of Learning" — solid orange `#f97216` background, white bold uppercase-style text, fully rounded (pill radius)
- H1 headline, large (~48–56px desktop), bold, white, with **inline orange emphasis** on the words "Industry" and "Real World":
  > Become **Industry** Ready with Skills, Mentorship, and **Real World** Experience.
- Supporting paragraph below, 2–3 lines, warm off-white `#e5e0da`, regular weight, max-width ~500px:
  > "VighnoLearn is a student focused skill development and career platform that helps students become industry ready through workshops, job oriented courses, mentorship, hackathons, and real world projects."
- Two CTA buttons side by side:
  - Primary: solid orange `#f97216` pill, white bold text, "Get Started"
  - Secondary: outlined pill (white/light border, transparent/dark fill), orange text, "Explore Programs"
- Right side: illustration of a person at a laptop wearing headphones, surrounded by floating icons (course/laptop screen, certificate, lightbulb, stacked books, target with arrow, gear, clipboard with checklist and award ribbon, trophy, coffee mug, sparkle/star accents). Illustration style: flat vector, orange/white/dark accent palette matching brand.

### 3.3 "Who Should Join VighnoLearn?" Section
- Background continues the same warm dark gradient
- Centered section heading in orange `#f97216`, bold
- Centered subheading in white/light grey, 2 lines:
  > "Whether you're a beginner or an aspiring professional, VighnoLearn helps you develop the skills employers value most."
- **6-card grid** (3 columns × 2 rows on desktop, stacks to 1 column on mobile), each card:
  - Radial maroon gradient background (see §1 gradient spec)
  - Rounded corners (~16px radius)
  - Padding ~24–32px
  - Small icon chip top-left (dark plum rounded-square, white line icon, ~40×40px)
  - Bold white card title
  - 2–3 line description in muted warm-white body text
  - Cards: **Interactive Content**, **Expert Instructors**, **Certificates**, **Learn at Your Pace**, **Career Support**, **Cutting-Edge Skills** (use icon glyphs: layers/copy, person-badge, certificate/shield-check, clock, briefcase, trending-up chart respectively)

### 3.4 Popular Courses Section
- Thin near-invisible horizontal divider line above this section (`#190b00`)
- Left: "Popular Courses" heading (orange, bold) + subtext "Join thousands of students in our most highly-rated professional paths." (white)
- Right (same row, desktop): "View All Courses" — solid orange pill button
- **6-card grid** (3 columns × 2 rows desktop → 1 column mobile), each course card:
  - Pure black `#000000` background, faint cool-dark border `#0b1a1f`, rounded corners (~12px), overflow-hidden
  - Top: full-width thumbnail image (16:9ish), rounded top corners only
  - Below image: bold white course title + right-aligned star rating (`★ 4.9`, star icon in orange/gold `#f49e0b`)
  - 2-line grey description text
  - Thin horizontal divider line
  - Bottom row: price in bold orange (`₹89.00`) left-aligned, "Enroll Now →" in orange, right-aligned
  - Courses: AI in Data Analytics, AI in App Development, AI in Data Science, AI Based Cybersecurity, AI Powered Web Development, AI in Cloud Computing — use relevant stock-style illustration/photo thumbnails for each (data dashboards, mobile app UI, robotic hand + human hand, hacker/cybersecurity dark scene, code/laptop dev scene, cloud network diagram)

### 3.5 Closing CTA Section
- Centered, background same warm dark base (near `#0f0802`)
- Large heading: "Ready to " + italic orange "Start Building" + "?" — white bold text with the italic orange accent word
- Subtext below: "Join thousands of students building their future with VighnoLearn." (muted light grey)
- Centered button: "Get Free Membership >" — gradient orange pill (see CTA gradient spec in §1), white bold text

### 3.6 Footer
- Background: flat near-black `#120701`
- Thin top divider line before footer content
- 5-column layout (desktop):
  1. Logo (white+orange wordmark) + short description paragraph (muted grey) + 3 circular social icons (Twitter, LinkedIn, Instagram — dark slate circle `#1e293b`, white glyph)
  2. **PLATFORM**: Courses, Mentorship, Chapters, Skill Labs
  3. **COMMUNITY**: Global Hub, Ambassadors, Partners, Events
  4. **ORGANIZATION**: About Us, Mission, Teams, Impact
  5. **RESOURCES**: Documentation, Brand Assets, Research, Legal
- Column headers: uppercase, white, small, semi-bold, letter-spaced
- Links: muted grey `#9d9592`, regular weight, hover → orange
- Bottom bar: thin divider, then "© 2026 VighnoLearn. All rights reserved." (left, muted grey) + "Privacy" / "Terms" links (right, muted grey)

---

## 4. Component & Style Details

- **Border radius**: generous throughout — fully rounded (pill) buttons; ~12–16px on cards; ~8px on smaller chips/icon boxes
- **Buttons**:
  - Primary (Get Started, Sign Up, Enroll link, View All Courses): flat solid orange `#f97216`, white text, pill-shaped, medium padding
  - Secondary (Explore Programs): outlined/light border, transparent or dark fill, orange text
  - CTA (Get Free Membership): gradient orange pill (see §1)
- **Dividers**: thin (1px), very low-contrast lines (`#190b00`-ish), used sparingly between major sections and inside course cards above price row
- **Icons**: minimal single-color (white) line-style icons, ~20–24px, centered inside small rounded-square chips with dark plum backgrounds (feature cards) — sourced from an icon set like Lucide or Phosphor
- **Shadows**: minimal to none — this design relies on color/gradient contrast rather than drop shadows
- **Spacing rhythm**: generous vertical section padding (~80–120px desktop between major sections), consistent 24–32px gutter in grids

---

## 5. Responsive Behavior

- Desktop: multi-column grids (3-col for feature cards and course cards), nav links inline
- Tablet (~768px): grids collapse to 2 columns, hero illustration may shrink or stack below text
- Mobile (~480px): all grids single-column; hero text and CTA buttons stack vertically and become full-width; nav collapses to hamburger menu; footer columns stack vertically

---

## 6. Tech Notes for Antigravity

- Use semantic HTML5 sectioning (`<nav>`, `<section>`, `<footer>`)
- Implement colors as CSS custom properties / Tailwind theme extension so they're reusable
- Implement the radial page-background gradient once at the top-level wrapper, not repeated per-section, so it reads as one continuous glow
- Feature cards and course cards should be built as reusable components taking title/description/icon (or image/price/rating) as props
- Ensure WCAG-reasonable contrast is checked where text sits directly on the darkest background areas (some muted greys are close to background — bump lightness slightly if contrast fails accessibility checks, while keeping the visual mood)
