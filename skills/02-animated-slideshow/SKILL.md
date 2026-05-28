---
name: animated-slideshow
description: |
  Battle-tested patterns for building polished single-file HTML presentations with bidirectional navigation, timeline TOC sidebar, the five acceptable animation patterns, and six real-world report patterns (comparison bar pairs, italic accent words, serif numbered findings, gradient bar fills, scroll-triggered counters, filter tabs). Triggers on: keynote, slideshow, slide deck, presentation, HTML deck, animated slides, interactive report.
metadata:
  version: "1.1.0"
  license: "Use freely"
---

# Animated HTML Slideshow · Patterns

This is a distilled, sanitized version of the slide engine I use. Drop into your skills directory or use as a reference when building HTML decks.

## The Slide Engine

```css
.slide {
  position: absolute; inset: 0;
  display: flex; flex-direction: column; justify-content: center;
  padding: 56px 80px;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity .55s ease, transform .55s ease;
  pointer-events: none;
}
.slide.active { opacity: 1; transform: translateY(0); pointer-events: auto; }
.slide.prev   { opacity: 0; transform: translateY(-20px); }
```

## The Bidirectional Fix (most important pattern)

Without this, backward navigation looks identical to forward. The fix locks the incoming slide at its current position before the class shuffle:

```javascript
function goTo(n) {
  if (n < 0 || n >= total || n === current) return;
  const goingBack = n < current;
  const incoming = slides[n];

  if (goingBack) {
    incoming.style.transition = "none";
    incoming.style.transform = "translateY(-20px)";
    incoming.style.opacity = "0";
    void incoming.offsetHeight;
  }

  slides.forEach((s, i) => {
    s.classList.remove("active", "prev");
    if (i < n) s.classList.add("prev");
  });

  if (goingBack) {
    incoming.style.transition = "";
    incoming.style.transform = "";
    incoming.style.opacity = "";
  }

  current = n;
  incoming.classList.add("active");
}
```

## The Five Acceptable Animations

1. **Opacity cascade** · children stagger in with translateY(14px) to 0 over 80ms delays
2. **Curtain reveal** · clip-path wipe inset(0 100% 0 0) to inset(0 0 0 0)
3. **Counting counter** · requestAnimationFrame easing a number from 0 to target
4. **Breathing pulse** · scale 1.0 to 1.02 over 3.2s on KPI values only
5. **SVG draw-in** · stroke-dashoffset animated from length to 0

## Banned Animations (see nuanced bans further down)

- popIn, glowPulse, slide-wow, bounceIn, flipCard · these mark the deck as amateur or AI-slop
- Generic barGrow across every chart and KPI tile (see nuanced bar pattern below for the one acceptable use)
- Continuous animations on static content beyond the breathing pulse on 1 to 3 KPIs
- Dark hero backgrounds. Always light-first

## Timeline TOC Sidebar

Fixed left rail, 168 to 188 pixels wide, dots grouped under section headers with a gradient progress line. Critical for any deck of 10+ slides.

## Slide Anatomy

Every slide should have:
- Small uppercase brand label at the top
- Bold heading
- Subtitle if needed
- Content block
- Optional source line at the bottom

## Real-World Patterns from Top-Tier Reports

These six patterns were extracted from professional interactive reports (Deloitte State of AI, McKinsey insights, BCG features) and validated for slideshow use. Each makes a deck feel like institutional-grade work without crossing into slop.

### 1. Comparison bar pair with floating delta

The single highest-signal data viz for change: two bars, end-state labels, a "+X pts" or "+X%" annotation floating between them. Use when a slide is comparing a before/after, a peer benchmark, or a now/projection.

```html
<div class="bar-pair">
  <div class="bp-title">Accelerating into production</div>
  <div class="bp-chart">
    <div class="bp-bar" style="--h: 28%"><span class="bp-val">25%</span></div>
    <div class="bp-delta">+29 pts</div>
    <div class="bp-bar" style="--h: 62%"><span class="bp-val">54%</span></div>
  </div>
  <div class="bp-labels"><span>Today</span><span>Within six months</span></div>
  <div class="bp-legend">Companies expecting at least 40% of experiments in production</div>
</div>
```

```css
.bp-chart {
  display: grid; grid-template-columns: 1fr auto 1fr;
  align-items: end; gap: 18px; height: 220px;
}
.bp-bar {
  background: linear-gradient(180deg, #00F09B 0%, #059669 100%);
  border-radius: 6px 6px 0 0;
  position: relative;
  height: 0;
  animation: barRise 1.1s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}
@keyframes barRise { to { height: var(--h); } }
.bp-val {
  position: absolute; top: -28px; left: 0; right: 0;
  text-align: center; font-weight: 800;
}
.bp-delta {
  padding: 6px 12px; border-radius: 100px;
  background: rgba(0,240,155,0.12); color: #059669;
  font-size: .82rem; font-weight: 700; align-self: center;
  opacity: 0;
  animation: fadeIn .4s ease forwards;
  animation-delay: 1.2s;
}
@keyframes fadeIn { to { opacity: 1; } }
```

**Rules of use:**
- 2 to 3 bars maximum. More than three needs a real chart.
- Both bars rise together, ascending values arranged left to right
- Delta appears AFTER bars finish rising (1.2s delay)
- End-state values labeled at the top of each bar, not midway
- Trigger once on slide entry, never re-fire

### 2. Italic accent word inside a sans heading

The Deloitte move: "Moving from pilot to scale as *access* expands" where one word, the concept word, is italic serif accent green, while the rest stays sans bold black. Draws the eye to the conceptual hinge of the sentence.

```html
<h2 class="finding-title">Moving from pilot to scale as <span class="accent-em">access</span> expands</h2>
```

```css
.finding-title {
  font-size: 2.4rem; font-weight: 800; letter-spacing: -1.2px; color: #18181b;
}
.accent-em {
  font-family: "Lora", "Georgia", serif;
  font-style: italic;
  font-weight: 500;
  color: #059669;
  letter-spacing: 0;
}
```

**Rules of use:**
- One accent word per heading. Two ruins the trick.
- The accented word must be the conceptual pivot, never an article or verb
- Serif italic only on the accent, not the surrounding text
- Brand primary color (or its dark variant for contrast on light)

### 3. Numbered key finding with serif italic marker

For "Five findings", "Six principles" or any sequence of big ideas, the serif italic large number marker gives editorial weight without bullets.

```html
<section class="finding">
  <span class="finding-num">1.</span>
  <h2 class="finding-title">Headline of the finding</h2>
  <h3 class="finding-sub">Sub-headline that explains it</h3>
  <p class="finding-body">Body paragraph with stats and explanation.</p>
</section>
```

```css
.finding-num {
  font-family: "Lora", "Georgia", serif;
  font-style: italic;
  font-weight: 600;
  font-size: 3.4rem;
  color: #059669;
  display: block;
  margin-bottom: 8px;
  line-height: 1;
}
```

**Rules of use:**
- Sequences of 3 to 7 max. Beyond that the eye loses count.
- Serif italic only on the number marker, not the headings
- Same accent color as the body primary accent
- Period after the number, not a colon or parenthesis

### 4. Subtle vertical gradient on bar fills

Bars filled with a top-to-bottom gradient from solid brand color to a slightly darker variant feel more refined than flat fills, without becoming decorative. The gradient must be SUBTLE (10 to 15 percent luminance difference at most). Anything stronger reads as decoration.

```css
.bar-gradient {
  background: linear-gradient(180deg, #00F09B 0%, #059669 100%);
  /* OR for purple: linear-gradient(180deg, #AA32FF 0%, #7c3aed 100%); */
}
```

**Banned variants:**
- Rainbow gradients (red to yellow to green)
- Gradients across two different brand colors (green to blue) on the same bar
- Reflective or glossy gradients (top highlight strip)
- Animated gradients (color cycling)

### 5. Scroll-triggered counter via IntersectionObserver

For long-form HTML pages (handouts, reports) rather than slide decks, fire counters when their container enters the viewport.

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting && !entry.target.dataset.counted) {
      entry.target.dataset.counted = "1";
      animateCounter(entry.target);
    }
  });
}, { threshold: 0.4 });

document.querySelectorAll(".wow-counter").forEach(el => observer.observe(el));

function animateCounter(el) {
  const target = parseFloat(el.dataset.target);
  const suffix = el.dataset.suffix || "";
  const prefix = el.dataset.prefix || "";
  const duration = 1100;
  const isInt = Number.isInteger(target);
  const start = performance.now();
  function tick(now) {
    const t = Math.min((now - start) / duration, 1);
    const eased = 1 - Math.pow(1 - t, 3);
    el.textContent = prefix + (isInt ? Math.round(target * eased) : (target * eased).toFixed(1)) + suffix;
    if (t < 1) requestAnimationFrame(tick);
    else el.textContent = prefix + (isInt ? Math.round(target) : target.toFixed(1)) + suffix;
  }
  requestAnimationFrame(tick);
}
```

**When to use which:**
- Slide deck: fire on slide entry (existing pattern). Replays each time the slide is shown.
- Long page: fire on viewport entry with IntersectionObserver. Fires once per page load.

### 6. Filter tab strip (segmented control)

For sections where the user can switch between cohorts, industries, time windows, or any category. A simple text-only tab strip with an active green underline.

```html
<div class="tab-bar" role="tablist">
  <button role="tab" class="active" data-target="all">All industries</button>
  <button role="tab" data-target="financial">Financial services</button>
  <button role="tab" data-target="health">Health</button>
  <button role="tab" data-target="industrial">Industrial</button>
</div>
<div class="tab-panels">
  <div data-panel="all" class="active">All content</div>
  <div data-panel="financial">Financial content</div>
</div>
```

```css
.tab-bar { display: flex; gap: 22px; border-bottom: 1px solid #e4e4e7; }
.tab-bar button {
  background: none; border: none; padding: 12px 2px;
  color: #a1a1aa; font-weight: 400; font-size: .92rem;
  border-bottom: 2px solid transparent;
  cursor: pointer; transition: color .2s, border-color .2s;
}
.tab-bar button:hover { color: #18181b; }
.tab-bar button.active {
  color: #18181b; font-weight: 600;
  border-bottom-color: #00F09B;
}
.tab-panels > [data-panel] { display: none; }
.tab-panels > [data-panel].active { display: block; }
```

```javascript
document.querySelectorAll(".tab-bar button").forEach(btn => {
  btn.addEventListener("click", () => {
    const target = btn.dataset.target;
    document.querySelectorAll(".tab-bar button").forEach(b =>
      b.classList.toggle("active", b === btn));
    document.querySelectorAll(".tab-panels > [data-panel]").forEach(p =>
      p.classList.toggle("active", p.dataset.panel === target));
  });
});
```

**Rules of use:**
- 3 to 6 tabs maximum. Beyond that, use a dropdown.
- One tab is active by default, never zero.
- Active state is text-weight plus green underline only. No filled backgrounds, no badges.
- Sticky position at the top of long sections is fine. Sticky in slide decks is not.

## Updated Bans (nuanced)

The blanket ban on barGrow from earlier guidance was over-broad. Tightened:

- BANNED: generic everywhere-pops-up-from-zero animations on every chart, KPI, and metric tile (the "teenager first PowerPoint" effect)
- BANNED: bars that overshoot and bounce back (use linear or ease-out, never ease-in-out with overshoot)
- BANNED: bars whose final height does not faithfully represent the data
- ALLOWED: a controlled 2-to-3-bar comparison with end-state labels and a delta annotation, bottom-up height transition, runs once on slide entry, finishes inside 1.2 seconds

## Pre-Flight Checklist

1. Navigate forward and backward through every slide
2. Click random timeline dots
3. Resize to mobile (test responsive)
4. Verify all numbers have sources
5. Check prefers-reduced-motion (* { animation-duration: .01ms !important })
6. Grep for banned animation classes
7. If you used a comparison bar pair, confirm the delta annotation matches the actual difference
8. If you used the italic accent word pattern, confirm it appears at most once per heading
9. If you used a filter tab strip, confirm one tab is active by default and the panel content matches
