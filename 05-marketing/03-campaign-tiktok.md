# Flavio Fusuma -- TikTok Content Strategy

---

## Overview

**Brand:** Flavio Fusuma
**Website:** flaviofusuma.com
**Platform goal:** Build awareness among product-minded tech leaders and creative agency professionals through short-form video content that showcases the intersection of code and design.
**Tone on TikTok:** Confident, educational, slightly informal. Show the craft, don't just talk about it.

---

## Content Pillars for TikTok

### Pillar 1: Code-to-UI Transformations
Show the journey from raw code to polished interface. These are the "before and after" of engineering.

**Format:** Screen recordings with text overlay and music.
**Frequency:** 2x per week.

### Pillar 2: Design Engineering Hot Takes
Short, opinionated statements about the intersection of code and design. Spark conversation.

**Format:** Direct to camera or bold text on screen with voiceover.
**Frequency:** 1x per week.

### Pillar 3: Behind the Build
Show real work in progress -- architecture decisions, debugging sessions, design reviews.

**Format:** Screen recordings, desk shots, sketch-to-code walkthroughs.
**Frequency:** 1x per week.

### Pillar 4: Quick Wins and Tips
Bite-sized technical or design tips that viewers can apply immediately.

**Format:** Tutorial-style screen recording with voiceover.
**Frequency:** 1x per week.

---

## 5 Video Concept Hooks (First 3 Seconds)

### Hook 1: "The Reveal"
**Visual:** Black screen. A cursor types one line of CSS. Hit enter. A stunning UI transition plays.
**Why it works:** Instant visual payoff. Creates curiosity about how one line changed everything.

### Hook 2: "The Callout"
**Visual:** Bold white text slams onto a deep blue screen: "Your engineer doesn't understand design."
**Why it works:** Provocation stops the scroll. Viewers want to see if they agree or disagree.

### Hook 3: "The Side-by-Side"
**Visual:** Split screen. Left: a janky, poorly built version of a UI. Right: the same UI built with craft. Both animate at once.
**Why it works:** The contrast is immediately visible and satisfying.

### Hook 4: "The Process Timelapse"
**Visual:** Sped-up screen recording of an entire component being built from scratch -- 2 hours compressed to 3 seconds.
**Why it works:** Timelapse content signals "this is going to be satisfying to watch."

### Hook 5: "The Question"
**Visual:** Flavio on camera, looking directly at the lens: "Why do most web apps feel like they were built by people who've never used a web app?"
**Why it works:** Relatable frustration hooks the audience into wanting the answer.

---

## Full Video Scripts

### Video 1: "One Line of CSS Changed Everything"

**Duration:** 45 seconds
**Pillar:** Code-to-UI Transformations
**Hook type:** The Reveal

---

**[0-3 sec] HOOK**
Screen: Black background. A cursor types `will-change: transform;` in a code editor.
Text overlay: "One line of CSS."
[Cut to: a laggy scroll animation suddenly becoming silky smooth]

**[3-10 sec] SETUP**
Voiceover: "A client came to me and said their app felt sluggish. Users were complaining. The team had spent two weeks trying to optimize JavaScript."
Screen: Shows the original janky animation playing.

**[10-25 sec] THE BUILD**
Voiceover: "I opened DevTools, checked the compositing layers, and found the problem in about four minutes. The browser was recalculating layout on every frame."
Screen: DevTools performance panel. Highlight the layout thrashing. Then show adding the CSS property.

**[25-35 sec] THE RESULT**
Voiceover: "One CSS property told the browser to promote the element to its own layer. Sixty frames per second. Instantly."
Screen: Side-by-side before and after. The smooth version is visibly satisfying.

**[35-45 sec] THE TAKEAWAY**
Voiceover: "Performance isn't always about rewriting your code. Sometimes it's about understanding how the browser thinks. That's what design-informed engineering looks like."
Screen: End card -- "Flavio Fusuma | flaviofusuma.com" on deep blue with amber accent.
Text overlay: "Follow for more code + design content."

---

### Video 2: "What Your Designer Wishes You Knew"

**Duration:** 55 seconds
**Pillar:** Design Engineering Hot Takes
**Hook type:** The Callout

---

**[0-3 sec] HOOK**
Screen: Bold text on deep blue: "What your designer wishes you knew."
Sound: A sharp, satisfying click.

**[3-8 sec] POINT 1**
Text on screen: "1. Spacing is not optional."
Voiceover: "When your designer specifies 24 pixels of padding, they mean 24. Not 'roughly a thumb-width.' Not whatever the default is. Twenty-four."
Visual: Side-by-side: one component with correct spacing, one with sloppy spacing.

**[8-18 sec] POINT 2**
Text on screen: "2. Transitions matter more than you think."
Voiceover: "An instant state change feels broken. A 200-millisecond ease-out feels intentional. The difference is one line of code and a lot of user trust."
Visual: Button click with no transition vs. button click with a smooth transition.

**[18-28 sec] POINT 3**
Text on screen: "3. Color is not decoration."
Voiceover: "That amber accent your designer picked? It's not random. It's guiding the user's eye to the primary action. If you use it everywhere, it guides nowhere."
Visual: A UI with amber used correctly on one CTA vs. amber scattered on every element.

**[28-40 sec] POINT 4**
Text on screen: "4. Responsive doesn't mean 'it doesn't break.'"
Voiceover: "Responsive means it feels considered at every viewport. If your mobile layout is just the desktop layout squeezed into a smaller box, you've failed the user."
Visual: A thoughtfully adapted mobile layout vs. a squished desktop layout.

**[40-50 sec] CLOSE**
Voiceover: "These aren't nice-to-haves. They're the difference between software people tolerate and software people love."
Visual: Quick montage of polished UI interactions.

**[50-55 sec] END CARD**
Screen: "Flavio Fusuma | Code meets design." on deep blue.
Text overlay: "Save this for your next code review."

---

### Video 3: "Building a Component From Scratch -- 2 Minutes"

**Duration:** 60 seconds (compressed from ~30 min real time)
**Pillar:** Behind the Build
**Hook type:** The Process Timelapse

---

**[0-3 sec] HOOK**
Screen: Empty code editor. Text overlay: "Let's build a button. But like... a good one."
Sound: Keyboard clacking begins.

**[3-12 sec] PHASE 1 -- STRUCTURE**
Voiceover: "Start with semantic HTML. A button is a button, not a div with an onclick handler."
Screen (sped up): Writing a clean React component. `<button>` tag, props interface, basic structure.
Text overlay: "Step 1: Structure"

**[12-22 sec] PHASE 2 -- STYLING**
Voiceover: "Design tokens for color, spacing, and type. No magic numbers. Every value comes from the system."
Screen (sped up): Adding CSS with design token variables. Showing the button taking shape visually.
Text overlay: "Step 2: Style with tokens"

**[22-32 sec] PHASE 3 -- STATES**
Voiceover: "Hover, focus, active, disabled, loading. Each state needs to feel intentional, not like an afterthought."
Screen (sped up): Adding hover transitions, focus rings, disabled opacity, a loading spinner.
Text overlay: "Step 3: Every state matters"

**[32-42 sec] PHASE 4 -- ACCESSIBILITY**
Voiceover: "Keyboard navigation. Screen reader labels. Reduced motion support. This isn't extra credit -- it's the baseline."
Screen (sped up): Adding aria labels, keyboard event handlers, prefers-reduced-motion media query.
Text overlay: "Step 4: Accessibility"

**[42-52 sec] PHASE 5 -- POLISH**
Voiceover: "Final pass. The animation easing. The shadow depth. The way it feels when you click it."
Screen: Real-time demo of the finished button. Click it. See the subtle press animation, the focus ring, the loading state.
Text overlay: "Step 5: The details"

**[52-60 sec] CLOSE**
Voiceover: "That's a button built with craft. Every component in your app deserves this level of care."
Screen: End card on deep blue. "Flavio Fusuma | flaviofusuma.com"
Text overlay: "Drop a component in the comments and I'll build it next."

---

## Hashtag Strategy

### Primary Hashtags (use on every post)
- #CodeAndDesign
- #DesignEngineering
- #FrontendDev
- #WebDevelopment
- #SoftwareEngineer

### Secondary Hashtags (rotate based on content)
- #ReactJS
- #TypeScript
- #UIUX
- #CSSAnimation
- #DesignSystems
- #WebPerformance
- #CleanCode
- #TechTok
- #DevTok
- #CodeTok

### Trending / Discovery Hashtags (use 1-2 per post)
- #LearnOnTikTok
- #TechTips
- #CodingTips
- #DeveloperLife
- #BuildInPublic

### Hashtag Rules
- Use 5-8 hashtags per post (not more -- TikTok's algorithm penalizes hashtag stuffing)
- Always include 2-3 primary, 2-3 secondary, and 1-2 trending
- Create a branded hashtag for ongoing series: #CraftWithFlavio

---

## Posting Cadence

| Day | Content Type | Pillar |
|-----|-------------|--------|
| Monday | Code-to-UI transformation | Pillar 1 |
| Wednesday | Hot take or opinion | Pillar 2 |
| Friday | Behind the build or tutorial | Pillar 3 or 4 |
| Saturday (optional) | Quick tip or community response | Pillar 4 |

**Optimal posting times (US audience):**
- Weekdays: 11:00 AM - 1:00 PM EST or 7:00 - 9:00 PM EST
- Weekends: 10:00 AM - 12:00 PM EST

**Minimum frequency:** 3 posts per week
**Target frequency:** 4-5 posts per week (including 1-2 lighter/reactive posts)

---

## Content Production Notes

### Equipment
- Screen recording: OBS or built-in screen capture
- Camera (for direct-to-camera): Smartphone or mirrorless in vertical orientation
- Audio: Lapel mic for voiceover; record in a quiet room
- Editing: CapCut (for TikTok-native feel) or DaVinci Resolve

### Visual Consistency
- Code editor theme: Dark theme with syntax highlighting that includes #F59E0B amber for key tokens
- Text overlays: Clean sans-serif font, white on deep blue or amber on dark backgrounds
- End card: Always the same -- "Flavio Fusuma | flaviofusuma.com" on #1E3A5F deep blue
- No face filters or heavy effects -- keep it clean and professional

### Engagement Strategy
- Reply to every comment in the first hour after posting
- Pin a comment with a question to drive discussion (e.g., "What component should I build next?")
- Stitch or duet other dev/design creators to participate in the community
- Respond to trending sounds or formats only if they authentically fit the brand

### Growth Tactics
- Cross-post to Instagram Reels and YouTube Shorts (adjust captions per platform)
- Collaborate with design-focused TikTok creators for duets
- Post "Part 1 / Part 2" series to drive follow-for-more behavior
- Use the pinned comment to link to flaviofusuma.com (since TikTok bio link is limited)

---

## Metrics and Goals

| Metric | Month 1 Target | Month 3 Target | Month 6 Target |
|--------|----------------|----------------|----------------|
| Followers | 500 | 2,500 | 10,000 |
| Avg. views per video | 1,000 | 5,000 | 15,000 |
| Engagement rate | 5%+ | 6%+ | 7%+ |
| Website clicks (bio link) | 50 | 250 | 1,000 |
| Saves per video | 20 | 100 | 300 |

**Key insight:** On TikTok, saves and shares matter more than likes for algorithmic reach. Optimize content to be reference-worthy ("save this for later").

---

*Last updated: April 2026*
