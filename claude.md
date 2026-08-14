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
- **Nach dem Push immer nach `main` mergen.** GitHub Pages baut aus `main`; ohne Merge landet nichts in der Vorschau. Nicht jedes Mal nachfragen.
- Vorschau-URLs: [v2](https://planet-group.github.io/Planet/planet-website-v2.html) · [Live-Fassung](https://planet-group.github.io/Planet/planet-website.html). Es gibt **keine** Seite unter `/Planet/` (404) — `/Planet/Pages/` ist der Signatur-Generator, nicht die Website.

## Open todos (`planet-website.html`)

1. **Telefonnummer** unten ergänzen (Footer / Kontakt) — inkl. echte `tel:`- und WhatsApp-Links bei „Und wie geht's weiter?“ (Anruf / WhatsApp). Betrifft nur noch `planet-website.html`; in v2 sind Mail, Telefon und WhatsApp aus der Kontaktsektion entfernt, dort führt allein der Fragebogen zum Kontakt.
2. **E-Mail freigeben** für den Fragebogen-Versand — FormSubmit-Aktivierung für `torsten@plnt.group`. Torsten muss den Link in der ersten Mail bestätigen, sonst kommt kein Fragebogen an.
   - Danach die Adresse durch den **FormSubmit-Token** ersetzen (`formsubmit.co/ajax/<token>`), damit sie nicht im Quelltext steht.
3. **Zahlen** für die einzelnen Unternehmen recherchieren und bestätigen lassen (Marken-Metriken / Stats-Strip).
4. **Domain** `planet.group` verbinden (öffentliche Site statt GitHub-Pages-Vorschau).
5. **Nachfolge-Variante** der Webseite bauen — eigene Version, die gezielt nur die Zielgruppe Unternehmensnachfolge anspricht (statt beider Wege „Wachstum" und „Nachfolge").
6. **Umsatzbänder im Fragebogen bestätigen** — aktuell Philips Schätzung (unter 1 / 1–5 / 5–15 / über 15 Mio. €). Das ist der eigentliche Filter, die Bänder müssen von der Geschäftsführung kommen.
7. **Bewertungskriterien für die Triage** — Torsten sichtet die Fragebögen und lädt persönlich ein; die Fragebögen gehen an `torsten@plnt.group`. Offen ist nur noch, nach welchen Kriterien bewertet wird. Die Seite verspricht Antwort innerhalb von 2 Werktagen.
8. **Warm-up prüfen** (Philips Punkt 5) — kurze Checkliste oder 1-Pager als Gegenleistung fürs Ausfüllen, z. B. „Bist du reif für einen Partner?“. Inhalt existiert noch nicht.

## Fragebogen-Funnel (`planet-website-v2.html`)

- Haupt-CTA ist der Fragebogen, nicht mehr die Terminbuchung — es gibt bewusst **keinen** Self-Service-Kalender.
- Vollbild-Overlay `#fragebogen`, gelb, auf Basis von `.principles-overlay`; öffnet über jeden Link mit `href="#fragebogen"`.
- Sechs Schritte, eine Frage pro Screen: Umsatz, Profitabilität, Wachstum/Nachfolge, Zeithorizont, Beweggrund (Freitext), Kontaktdaten.
- Kontaktdaten stehen absichtlich am Ende — das hebt die Abschlussquote.
- Versand gesammelt über FormSubmit an `torsten@plnt.group`, danach der Wellenbrecher-Screen: Antwort in 2 Werktagen.
- Mail, Telefon und WhatsApp stehen bewusst **nicht** neben dem Einstieg — sie würden den Filter aushebeln. `hello@plnt.group` bleibt nur im Impressum und in der Fehlermeldung des Formulars.
