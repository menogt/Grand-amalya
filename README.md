# The Grand Amalya — Landing Page

A premium, single-page marketing site for **The Grand Amalya**, a tropical
hotel in Homagama, Sri Lanka, known for poolside dining, garden spaces, and a
150-guest Grand Ballroom.

Built with **Astro 5**, scoped **vanilla CSS with custom properties**, and
**TypeScript** for all interactivity. No CSS framework, no build-time UI deps.

## Design direction — "Tropical Modern Luxe"

A deliberate move away from the common cream / high-contrast-serif / terracotta
look. The identity is drawn from the subject itself:

| Token   | Value                                  | Why |
| ------- | -------------------------------------- | --- |
| Canvas  | `--ivory #f3efe6`                      | warm, never pure white |
| Base    | `--jade-900 #0c211c` → `--jade-500`    | Sri Lankan foliage & pool water |
| Accent  | `--brass #c08b3e` / `--brass-soft`     | ballroom / wedding luxury |
| Display | Fraunces (used with restraint)         | editorial elegance |
| Body    | Inter                                  | clean, legible utility |

**Signature element:** a morphing "water-ripple" gradient shape in the hero with
parallax, paired with a floating glassmorphic guest-review card that overlaps
the dark ballroom section.

## Structure

1. **Hero** — massive Fraunces headline, sub-headline, dual CTAs, ambient
   parallax shapes, real guest stats (4.0 / 1,494 reviews).
2. **Features grid** — offset 4-column glassmorphism cards (card 02 lifted for
   asymmetry), inline SVG icons.
3. **Interactive showcase** — tab toggle that cross-fades between three real
   photographed spaces (Pool Deck / Grand Ballroom / From the Kitchen).
4. **Gallery** — asymmetric photo mosaic ("Around the grounds") with a tall
   center feature.
5. **Ballroom / CTA** — dark botanical section over a real ballroom photo, with
   an overlapping glass review card.
6. **Visit + newsletter** — accessible signup with client-side validation.
7. **Footer** — address, phone, nav, social, Google Maps directions.

## Photography

Six real property photos live in `src/assets/photos/` and are served through
Astro's `<Image>` component, which emits responsive `srcset` `.webp` variants
and width/height to prevent layout shift:

| File | Used in |
| --- | --- |
| `pool-day.webp`     | Hero (eager, high priority) |
| `pool-night.webp`   | Showcase — The Pool Deck |
| `ballroom-blue.webp`| Showcase — Grand Ballroom |
| `dining-buffet.webp`| Showcase — From the Kitchen |
| `pool-morning.webp` | Gallery |
| `ballroom-red.webp` | Gallery (tall) + Ballroom section background |

## Run

    npm install
    npm run dev      # http://localhost:4321
    npm run build    # static output -> dist/
    npm run preview

Requires Node >=22.12.

## Accessibility checklist

- Semantic landmarks (header, main, nav, footer) + skip link.
- All interactive controls keyboard-operable with visible :focus-visible rings.
- Showcase tabs use role="tablist" / aria-selected.
- prefers-reduced-motion disables animation, parallax, and the custom cursor.
- Custom cursor is decorative (aria-hidden) and pointer-fine-only; native cursor
  is never removed on touch/coarse pointers.
- Newsletter status messages announced via aria-live="polite".
- Color pairings meet WCAG AA contrast (jade/brass on ivory, ivory on jade-900).
- Responsive from 320px up; layout reflows to single column on mobile.

> Placeholder imagery is rendered as CSS gradient "art" panels. Swap the
> .stage__art blocks for real <img>/<picture> elements when photography is
> available — labels and captions already describe each space.
