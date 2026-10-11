# Sector Three: Design Language

**Brand:** Sector Three, a performance sim racing lab in Mooresville, NC (fictional)
**Concept:** *The live timing monitor.* The whole site looks like the timing screen on a race engineer's pit wall: dark, dense, and exact. Colour is never decoration. It always reports lap status.
**Audience:** Serious amateur and club racers who already know the basics and want measurable improvement.
**Mood:** Clinical, technical, quietly confident. It feels like a data tool, not a lifestyle brand.

---

## 1. Core principles

1. **Colour means status.** Purple = fastest overall, green = personal best, yellow = slower than PB, red = flag or time lost. These are real motorsport timing conventions. Never use them for decoration, and never use a fourth accent.
2. **Data is the hero.** Show real lap times, sector splits, Nm, kg, Hz and mm wherever you can. Numbers are always monospaced with tabular figures.
3. **Panels, not cards.** Content sits in flat rectangular panels split by 1px hairlines. Panels are often butted together with a 1px gap that lets the line colour show through, like a grid of monitors. No rounded corners and no drop shadows anywhere.
4. **Condensed, uppercase headlines.** Big, tight and squared off, like signage on a pit wall.
5. **Dark only.** This is a single-theme design. Don't make a light variant.

## 2. Colour tokens

| Token | Hex | Use |
|---|---|---|
| `--bg` | `#0A0E13` | Page background (blue-biased near-black, never pure black) |
| `--status-bar` | `#070A0E` | Sticky top bar, ticker strip |
| `--panel` | `#10161E` | Panels, tables, booking grid |
| `--line` | `#1E2731` | All hairlines and panel gaps |
| `--fg` | `#D9E0E8` | Primary text |
| `--fg-2` | `#B4BECA` | Body copy and paragraphs |
| `--mute` | `#7C8897` | Labels, axis text, secondary data |
| `--purple` | `#B266FF` | Fastest overall. Also the single brand accent (primary CTA, logo tick, highlighted row) |
| `--green` | `#2FD06C` | Personal best, "track green" status |
| `--yellow` | `#F0C232` | Slower than PB |
| `--flag` | `#FF4A3D` | Time lost, red flag. Use sparingly, often at 15–35% opacity as a fill |

Highlighted table row: `rgba(178,102,255,.07)` background with the position number in purple.

## 3. Typography

All three faces are on Google Fonts.

| Role | Family | Weights | Treatment |
|---|---|---|---|
| Display | **Saira Condensed** | 600, 800 | UPPERCASE, line-height 0.86–0.95, letter-spacing −0.01em. Hero 56–148px fluid, H2 36–64px, H3 22–30px |
| Body | **Saira** | 400, 500, 600 | 16px base, 1.55 line-height. Lead paragraph 18px |
| Data / labels | **JetBrains Mono** | 400, 600 | Tabular numbers. Labels are 11px UPPERCASE with 0.12em tracking in `--mute`. Tables 13px |

- Put one word of the hero headline in `--purple` (for example, "Find the last **tenth.**").
- Section labels follow the pattern `01 · Coaching` in mono. They're numbered because the page is a real sequence: coaching → hardware → programs → booking.
- Buttons use Saira Condensed 600, UPPERCASE, 0.06em tracking.

## 4. Layout

- Max width 1360px. Side gutter `clamp(16px, 3.2vw, 44px)`.
- **Status bar:** sticky, 52px, `--status-bar` background. Logo on the left, nav, then a live status readout on the right ("■ TRACK GREEN · 6/6 RIGS ONLINE"), then a light inverse "Book a rig" button.
- **Hero:** two columns. Left: a huge condensed headline, lead text and two CTAs. Right: a **timing tower** table aligned to the bottom of the headline.
- **Ticker:** a full-width mono strip between hairlines, scrolling lap records and next events. It pauses under reduced-motion.
- **Section header:** a 220px left column for the mono label, then the H2 and description on the right.
- Section padding `clamp(56px, 8vw, 112px)`.
- Mobile: everything stacks to one column, the nav hides, and wide tables scroll inside their own container.

## 5. Signature components

- **Timing tower:** a table with columns Pos, Driver (bold name + muted car number), S1, S2, S3, Last and Gap, all in mono. Each sector cell is coloured purple, green or yellow. A legend row underneath explains the colours.
- **Telemetry trace:** an SVG speed-vs-distance chart. The reference lap is a purple line, the user's lap is a yellow line, and the gap between them is filled with `--flag` at 16% opacity. It has faint horizontal grid lines and dashed vertical corner markers (T10a, T10b, T12) with mono labels. Next to it sits a "Coach's notes" list: a mono corner code in purple, then a bold instruction and an explanation.
- **Spec sheet:** a three-column grid separated by vertical hairlines. Each column has an H3 class name, a mono count ("Rigs 04–05") and a `<dl>` of mono-uppercase keys with plain values, ending in a rate line ("$62 / hour").
- **Program grid:** four panels in a 1px-gap grid. Each has a purple mono eyebrow, condensed H3 and copy, with the price at the bottom above a dashed top border.
- **Slot booking grid:** rows are rigs and columns are hours. Free slots are outlined boxes, taken slots use a diagonal hatch (`repeating-linear-gradient(135deg, …)`), and picked slots fill solid purple. A side panel lists the picks with a running total.

## 6. Motion

- Restrained. The only ambient motion is the scrolling ticker (48s linear loop).
- Hover changes border or text colour only. No lift or scale.
- No page-load choreography. Data should already be there, like a live screen.

## 7. Voice

- Short, coach-like and specific: "Brake 12 m later." "Throttle earlier, not harder."
- Use real terms: sector, delta, PB, stint, stewarded, HPDE, direct drive, load cell.
- Never hype ("ultimate", "insane", "next-level").

## 8. Don'ts

- No rounded corners, glows, gradients on surfaces, or glassmorphism.
- No neon green as a brand accent. Green only means personal best.
- No stock photos of people in VR headsets. Data visuals carry the page.
- No centred hero layouts.
