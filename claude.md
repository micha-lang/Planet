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

## Website

- `planet-website.html` — aktuelle Live-/Hauptversion (Wachstum und Nachfolge). Assets: `planet.css`, `assets/…`.
- `planet-website-nachfolge.html` — spezialisierte Nachfolge-Variante. Dieselbe Technik und dieselben Assets, Copy nur für Unternehmer, die ihr Unternehmen in gute Hände geben wollen.

## Arbeitsweise

- **Keine Screenshots und keine Browser-Durchläufe zur Routine-Kontrolle.** Änderungen, die am Code eindeutig ablesbar sind, direkt umsetzen und in Worten beschreiben.
- Nur wenn eine Ursache am Code wirklich nicht erkennbar ist (z. B. Umbruch-/Layout-Verhalten, das erst beim Rendern entsteht), im Browser nachmessen — **vorher kurz fragen**.
- **Nach dem Push immer nach `main` mergen.** GitHub Pages baut aus `main`; ohne Merge landet nichts in der Vorschau. Nicht jedes Mal nachfragen.
- Vorschau-URLs: [Live-Fassung](https://planet-group.github.io/Planet/planet-website.html) · [Nachfolge](https://planet-group.github.io/Planet/planet-website-nachfolge.html). Es gibt **keine** Seite unter `/Planet/` (404) — `/Planet/Pages/` ist der Signatur-Generator, nicht die Website.

## Open todos (`planet-website.html`)

1. **E-Mail freigeben** für den Fragebogen-Versand — FormSubmit-Aktivierung für `torsten@plnt.group`. Torsten muss den Link in der ersten Mail bestätigen, sonst kommt kein Fragebogen an.
   - Danach die Adresse durch den **FormSubmit-Token** ersetzen (`formsubmit.co/ajax/<token>`), damit sie nicht im Quelltext steht.
2. **Zahlen** für die einzelnen Unternehmen recherchieren und bestätigen lassen (Marken-Metriken / Stats-Strip).
3. **Domain** `planet.group` verbinden (öffentliche Site statt GitHub-Pages-Vorschau).
4. **Umsatzbänder im Fragebogen bestätigen** — aktuell Philips Schätzung (unter 1 / 1–5 / 5–15 / über 15 Mio. €). Das ist der eigentliche Filter, die Bänder müssen von der Geschäftsführung kommen.
5. **Bewertungskriterien für die Triage** — Torsten sichtet die Fragebögen und lädt persönlich ein; die Fragebögen gehen an `torsten@plnt.group`. Offen ist nur noch, nach welchen Kriterien bewertet wird. Die Seite verspricht Antwort innerhalb von 2 Werktagen.
6. **Warm-up prüfen** (Philips Punkt 5) — kurze Checkliste oder 1-Pager als Gegenleistung fürs Ausfüllen, z. B. „Bist du reif für einen Partner?“. Inhalt existiert noch nicht.

## Fragebogen-Funnel (`planet-website.html`)

- Haupt-CTA ist der Fragebogen, nicht mehr die Terminbuchung — es gibt bewusst **keinen** Self-Service-Kalender.
- Vollbild-Overlay `#fragebogen`, gelb, auf Basis von `.principles-overlay`; öffnet über jeden Link mit `href="#fragebogen"`.
- Sechs Schritte, eine Frage pro Screen: Umsatz, Profitabilität, Wachstum/Nachfolge, Zeithorizont, Beweggrund (Freitext), Kontaktdaten.
- Kontaktdaten stehen absichtlich am Ende — das hebt die Abschlussquote.
- Versand gesammelt über FormSubmit an `torsten@plnt.group`, danach der Wellenbrecher-Screen: Antwort in 2 Werktagen.
- Mail, Telefon und WhatsApp stehen bewusst **nicht** neben dem Einstieg — sie würden den Filter aushebeln. `hello@plnt.group` bleibt nur im Impressum und in der Fehlermeldung des Formulars.

## Nachfolge-Variante (`planet-website-nachfolge.html`)

- Eigene URL, nicht ein Modus der Hauptseite. Zielgruppe: Unternehmer, die ihr Unternehmen übergeben wollen — nicht um jeden Preis.
- Kein Wachstumspfad: Sektion `#wege` ist „Du bestimmst das Tempo“ (gehen / bleiben / erst reden). Der Fragebogen fragt Rolle statt Wachstum/Nachfolge und sendet immer `Weg: Nachfolge` plus `Quelle: Nachfolge-Seite`.
- Mail-Betreff: `Planet Fragebogen Nachfolge — {Unternehmen}`.
