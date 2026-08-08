# Tiefstart Landingpage

Quellcode von [projekt-tiefstart.de](https://projekt-tiefstart.de) — der Landingpage für
Tiefstart, eine Gemeinschaft für Menschen in einer Krise.

Einziges Ziel der Seite ist die Buchung eines kostenlosen Erstgesprächs über TidyCal.

## Technik

Statisches HTML und CSS. Bewusst ohne Framework, ohne Build-Schritt und **ohne JavaScript** —
was im Repository liegt, ist genau das, was der Browser bekommt.

- **Kein Tracking.** Keine Analytics, keine Cookies, kein Consent-Banner. Vercel Analytics
  und Speed Insights sind absichtlich deaktiviert.
- **Schriften self-hosted.** Keine Requests an Google-Server (DSGVO).
- **Barrierefreiheit:** WCAG 2.1 AA als Anspruch — semantische Struktur, durchgehende
  Überschriften-Hierarchie, sichtbare Fokus-Indikatoren, Sprungmarke, `prefers-reduced-motion`.
- **Mobile-first** über `clamp()` und `auto-fit`-Raster, ohne eine einzige Media Query.

## Lokal starten

Es gibt nichts zu installieren. Ein beliebiger statischer Server genügt:

```bash
python3 -m http.server 4173
```

Dann `http://localhost:4173` öffnen.

## Aufbau

```
index.html            Die Landingpage
assets/tiefstart.css  Sämtliche Styles, Tokens als CSS-Custom-Properties
assets/fonts/         woff2 + Lizenztexte
assets/*.svg          Wortzeichen und Favicon
vercel.json           Security-Header, Caching, cleanUrls
```

Die Farb-, Abstands- und Schriftgrößen-Tokens stehen gesammelt im `:root`-Block von
`assets/tiefstart.css`.

## Deployment

Vercel, statisch, ohne Build-Schritt. `vercel.json` setzt Security-Header und Caching-Regeln.
Die Content-Security-Policy erlaubt `script-src 'none'` — die Seite kommt ohne JavaScript aus,
und diese Einstellung stellt sicher, dass das so bleibt.

## Schriften

| Schrift | Lizenz | Verwendung |
|---|---|---|
| [Newsreader](https://github.com/productiontype/Newsreader) | SIL OFL 1.1 | Überschriften, Zitate, Ziffern |
| [Source Sans 3](https://github.com/adobe-fonts/source-sans) | SIL OFL 1.1 | Fließtext, Bedienelemente |

Die vollständigen Lizenztexte liegen als `OFL-Newsreader.txt` und `OFL-SourceSans3.md` in
`assets/fonts/`. Ausgeliefert wird jeweils nur das Latin-Subset.

## Herkunft

Design und Texte stammen aus einem Prototyp in Claude Design und sind final. Diese
Produktionsfassung übernimmt sie unverändert; Änderungen am Wortlaut gehören in den Prototyp,
nicht hierher.
