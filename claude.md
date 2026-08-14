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

## Website variants

- `planet-website.html` — aktuelle Live-/Hauptversion.
- `planet-website-v2.html` — experimentelle Kopie für unsichere Änderungen; Assets (`planet.css`, `assets/…`) werden geteilt.

## Arbeitsweise

- **Keine Screenshots und keine Browser-Durchläufe zur Routine-Kontrolle.** Änderungen, die am Code eindeutig ablesbar sind, direkt umsetzen und in Worten beschreiben.
- Nur wenn eine Ursache am Code wirklich nicht erkennbar ist (z. B. Umbruch-/Layout-Verhalten, das erst beim Rendern entsteht), im Browser nachmessen — **vorher kurz fragen**.

## Open todos (`planet-website.html`)

1. **Telefonnummer** unten ergänzen (Footer / Kontakt) — inkl. echte `tel:`- und WhatsApp-Links bei „Und wie geht's weiter?“ (Anruf / WhatsApp).
2. **E-Mail freigeben** für den Fragebogen-Versand — FormSubmit-Aktivierung für `hello@plnt.group` (Aktivierungslink in der ersten Mail bestätigen). Ohne das kommt keine Antwort an.
3. **Zahlen** für die einzelnen Unternehmen recherchieren und bestätigen lassen (Marken-Metriken / Stats-Strip).
4. **Domain** `planet.group` verbinden (öffentliche Site statt GitHub-Pages-Vorschau).
5. **Nachfolge-Variante** der Webseite bauen — eigene Version, die gezielt nur die Zielgruppe Unternehmensnachfolge anspricht (statt beider Wege „Wachstum" und „Nachfolge").
6. **Umsatzbänder im Fragebogen bestätigen** — aktuell Philips Schätzung (unter 1 / 1–5 / 5–15 / über 15 Mio. €). Das ist der eigentliche Filter, die Bänder müssen von der Geschäftsführung kommen.
7. **Interne Triage festlegen** — wer liest die Fragebögen, nach welchen Kriterien wird bewertet, wer lädt persönlich ein (Mail oder WhatsApp). Die Seite verspricht Antwort innerhalb von 2 Werktagen.
8. **Warm-up prüfen** (Philips Punkt 5) — kurze Checkliste oder 1-Pager als Gegenleistung fürs Ausfüllen, z. B. „Bist du reif für einen Partner?“. Inhalt existiert noch nicht.

## Fragebogen-Funnel (`planet-website-v2.html`)

- Haupt-CTA ist der Fragebogen, nicht mehr die Terminbuchung — es gibt bewusst **keinen** Self-Service-Kalender.
- Vollbild-Overlay `#fragebogen`, gelb, auf Basis von `.principles-overlay`; öffnet über jeden Link mit `href="#fragebogen"`.
- Sechs Schritte, eine Frage pro Screen: Umsatz, Profitabilität, Wachstum/Nachfolge, Zeithorizont, Beweggrund (Freitext), Kontaktdaten.
- Kontaktdaten stehen absichtlich am Ende — das hebt die Abschlussquote.
- Versand gesammelt über FormSubmit an `hello@plnt.group`, danach der Wellenbrecher-Screen: Antwort in 2 Werktagen.
