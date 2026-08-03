# Planet Styleguide — Agent Notes

Patterns that live in the product (and as live examples in `UX-Styleguide.html`) but are not spelled out as separate guide chapters.

## Cockpit (internal dashboard)

- File: `Pages/cockpit.html` — employee dashboard on Planet tokens (`../planet.css`).
- Modular widgets (Kalender, Personio, Asana, Mail, Chat, WhatsApp, Canva, Apps hub, News, Events, Birthdays).
- Customizable: edit mode (drag reorder, remove), catalog panel (add/remove), layout in `localStorage` (`planet-cockpit-layout-v1`).
- Integrations are mocked surfaces for now — ready to swap for real APIs later.

## Brand & Naming

- In UI, wordmark and voice the brand is **Planet**.
- Legal entity and domain: **PLNT Group** / `plnt.group`.
- **Planet** → logo, headlines, body, nav, soft-outro wordmark.
- **PLNT Group** → copyright, imprint, email `hello@plnt.group`.

## Hero Full-Bleed

- Standard entry for image-led landing pages (also the guide’s opening hero).
- Edge-to-edge photo, dark overlay, display headline, short sub, scroll cue.
- Nav on hero: transparent with light chrome.
- No cards or badges in the first viewport.
- Type: headline = `--text-display`; on mobile often step down to `--text-h2`.
- Text-hero (no image) is a secondary variant — not shown as a guide chapter; use the `.hero` pattern from `planet.css` when needed.

## Open todos (`planet-website.html`)

- Telefonnummer unten ergänzen (Footer / Kontakt).
- E-Mail für Kontaktformular freigeben (FormSubmit-Aktivierung für `hello@plnt.group`).
- Zahlen für die einzelnen Unternehmen recherchieren und bestätigen lassen (Marken-Metriken / Stats).
