## What research says

- Award-level portfolios (Awwwards/Muzli 2026) win on **one strong idea + motion storytelling**, not generic card grids: [Awwwards portfolio winners](https://www.awwwards.com/websites/winner_category_portfolio/), [Muzli top 100](https://muz.li/blog/top-100-most-creative-and-unique-portfolio-websites-of-2025/)
- 2026 trends: storytelling case studies, texture/tactility, retro-futurism, gamified touches, AI chat moments: [Envato portfolio trends](https://elements.envato.com/learn/portfolio-trends)
- Minimal editorial with generous whitespace + strong typography = timeless, recruiter-friendly: [minimalist examples](https://reallygooddesigns.com/minimalist-portfolio-website/)
- Brutalist/terminal = high personality, dev-native, but trend-brutalism dating fast; functional brutalism evergreen: [Superdesign brutalism data](https://superdesign.dev/styles/brutalism), [terminal-portfolio](https://github.com/satnaing/terminal-portfolio)
- Hero with one living moment (canvas/3D/GSAP scroll scene) beats static hero: [GSAP hero tutorial](https://dev.to/fahadalikhanca/building-an-animated-portfolio-hero-with-gsap-splittext-and-a-canvas-particle-background-3d4e), [GSAP vs Framer Motion](https://codolve.com/blog/gsap-vs-framer-motion)

## Content architecture (same for any direction — built from your real data)

1. **Hero** — name + positioning line: "I build products and break them before users do." Builder + QA duality = your unique hook. GitHub/LinkedIn/email.
2. **Proof strip** — 89 repos · 3 orgs · 6 shipping products · 5 yrs cross-discipline.
3. **Featured case studies (5, deep not shallow)** — each gets problem → what I built → stack → status:
   - StormCom (multi-tenant SaaS, 42-model schema)
   - PetFolio (Flutter social-commerce, 260+ commits)
   - GadgetChai (bKash billing + AI e-KYC — most technically distinctive, lead with it)
   - Awaken (ML Kit pose-detection alarm — most memorable demo story)
   - FreeLLMAPI (16-provider LLM proxy — devtools credibility)
4. **CodeStorm-Hub founder story** — org, team, open source, community.
5. **Dual-track experience timeline** — engineering track (A1QA, Hilinkz) parallel to leadership track (SalesMaestro PM). Two rails, one timeline. Rare combo, show it as strength.
6. **Skills** — grouped: Mobile / Web / QA / Backend / AI-Ops.
7. **Contact** — single strong CTA.

## Three design directions

**A — Engineering Editorial (recommended)**
Light, magazine-like. Swiss typography: big serif display (e.g. Instrument Serif / Fraunces) + grotesk body (Inter/General Sans). Numbered sections (01–06), thin rules, huge whitespace, one accent color (deep green or international orange). Case studies read like articles with side-notes and stack margins. Subtle motion only: text mask reveals, underline draws. Ages best, recruiter-friendly, stands out precisely because most dev portfolios are dark.

**B — Terminal / IDE native**
Monospace (JetBrains Mono), dark editor palette, hero = interactive prompt (`> anam --projects`), sections as "files" in a tree, test-pass badges (`✓ 42 checks passed`) as QA identity motif. Gamified, dev-audience catnip. Risk: themed hard; hiring managers outside engineering get less.

**C — Cinematic Interactive**
Dark, GSAP scroll-driven storytelling: pinned hero with canvas particle/3D moment, horizontal-scroll project reel, big kinetic type. Awwwards energy. Highest wow, highest effort, needs restraint to not feel template-y.

All three: mobile-first, WCAG AA, `prefers-reduced-motion`, no emoji icons, <100KB critical path.

Direction locked: **Cinematic Interactive, dual theme**. Full design plan:

## Design Plan — "Storm" (working title)

### Concept
One narrative spine: **"I build the storm, then test it."** Scroll = journey through your products. Every section is a scene, not a card grid. Signature visual: a living particle field (canvas) that reacts to scroll and cursor — calm in light mode, electric in dark mode. Ties to CodeStorm-Hub identity.

### Themes
| Token | Dark (default at night) | Light |
|---|---|---|
| Background | `#0A0E1A` near-black navy | `#FAFAF7` warm paper |
| Text | `#F4F6FB` | `#101418` |
| Accent | electric green `#22C55E` | deep green `#15803D` (AA on paper) |
| Secondary accent | storm blue `#38BDF8` | `#0369A1` |
| Surface | `rgba(255,255,255,.04)` | `#FFFFFF` + soft shadow |

Toggle: sun/moon button, persists in `localStorage`, respects `prefers-color-scheme` first visit. Particle canvas re-colors per theme.

### Typography
- Display: **Clash Display** or **Archivo Expanded** — 800 weight, clamp(3rem → 8rem), kinetic
- Body: **Space Grotesk**
- Code/labels: **JetBrains Mono** (stack tags, section numbers, stats)

### Scene-by-scene choreography (GSAP + ScrollTrigger)

1. **Hero (pinned, 100vh)** — particle storm canvas behind. Name assembles letter-by-letter (SplitText-style mask reveal). Sub-line types in mono: `builder × breaker × founder`. Cursor repels particles. Scroll hint pulses.
2. **Proof strip** — numbers count up as line draws across screen: 89 repos / 6 products / 3 orgs / 5 yrs.
3. **Project reel (pinned, horizontal scroll)** — 5 full-viewport panels slide horizontally while vertical scroll drives them. Each panel: giant index number (01–05), project name in display type, one-line hook, 3 mono stack tags, live GitHub link. Order: GadgetChai → Awaken → StormCom → PetFolio → FreeLLMAPI. Background hue shifts subtly per panel.
4. **Case study deep-dives** — after reel, each project gets a vertical block that parallax-reveals: problem → built → stack → status. Text slides in from alternating sides.
5. **CodeStorm-Hub scene** — particles converge into a storm vortex forming the org mark; founder story text pinned beside it.
6. **Dual-track timeline** — two vertical rails (Engineering | Leadership) draw as SVG lines on scroll; nodes pop as they enter.
7. **Contact finale** — particles calm to slow drift. Big type: "Let's build something that survives testing." Magnetic email button (cursor-attracted). Social icons.

### Micro-interactions
- Custom cursor dot + trailing ring, scales on hoverables
- Magnetic buttons (translate toward cursor within radius)
- Link underlines draw left→right
- Theme toggle morphs sun↔moon with rotation

### Performance & accessibility budget
- Canvas: capped particle count (~120 desktop, ~50 mobile), `requestAnimationFrame` paused off-screen
- `prefers-reduced-motion`: kill pin/horizontal scroll, particles static, everything readable top-to-bottom
- Mobile: horizontal reel degrades to vertical stacked panels
- Focus states, semantic landmarks, AA contrast both themes, keyboard nav
- Zero framework: vanilla JS + GSAP (CDN or vendored ~60KB), single HTML — deployable to GitHub Pages/Vercel as-is

### Build order (once you approve)
1. Theme system + typography + custom cursor
2. Particle engine + hero
3. Horizontal reel + scenes
4. Timeline + contact + polish
5. Cross-viewport verify (375/768/1024/1440), reduced-motion pass

Plan good? Say go — I build it. Want changes (different accent, section order, more/fewer projects) — say what.