# Erstcheck dem-gruppe.de — 09.11.2026

Firma: DEM GROUP Management GmbH, Immobilienmakler Düsseldorf (Kauf/Verkauf, auch deutschlandweit). Sprachen: DE + EN (WPML, hreflang de/en).

## Technik
- WordPress 6.9.4, Theme Houzez, Elementor 4.0.7, Slider Revolution 6.7.34, Redux, WPML 4.9.2.1, Site Kit 1.178.0
- nginx/1.24.0 (Ubuntu) — Version im Header sichtbar
- Tracking: GTM-5VMCM5P8 + gtag; Consent: Complianz
- Startseite: ~420 KB HTML, 45 <script>, 1 H1

## Erste Auffälligkeiten
1. robots.txt → 404 (nginx-Fehlerseite); Sitemap wird damit nirgends angekündigt
2. http://dem-gruppe.de → 3 Weiterleitungen (https ohne www → http www → https www) statt 1
3. Kein HSTS-Header
4. Sitemaps (Yoast/RankMath-Index): page 45, post 18, property 121 URLs; zusätzlich Taxonomie-Sitemaps (property_feature/label/state/city, houzez_agent/agency, fts_builder) → Thin-Content-Kandidaten
5. Blog: viele fachfremde News (Weihnachtsmarkt Herne, Charité-Ranking, Visapolitik, Grenzkontrollen Polen) → Relevanz/E-E-A-T prüfen
6. Startseiten-HTML schwer (420 KB) → PageSpeed prüfen

## Nächste Schritte
- Statuscodes von Unterseiten nachprüfen (curl -w lieferte lokal 000, Tool-Problem)
- Screaming-Frog-Vollcrawl → raw/
- PSI mobil/desktop, SE Ranking (Sichtbarkeit, Keywords, Wettbewerber Düsseldorf), KI-Sichtbarkeit
- Rechtliches: Impressum, Datenschutz, Consent vor GTM

---

# Screaming-Frog-Vollcrawl 10.11.2026 (Export `2026.11.10.08.29.17/`, lokal, gitignored)

Zahlen: 1.280 HTML-URLs (717 DE / 563 EN), davon nur **285 indexierbar**, 995 nicht indexierbar (971 per Canonical auf andere URL). Zählungen je Export-Datei: `data/screamingfrog-2026-11-10-counts.txt`.

## Hauptbefunde
1. **Endlose Paginierung auf Makler-/Agentur-Seiten (Crawler-Falle).** `/agent/evgeny-katsman/page/N/`, `/agent/severyna-moroz/…`, `/agentur/dem-group-management-gmbh/…` + EN-Pendants: ~970 URLs bis page/179. Live geprüft: page/2, /10, /100, /178, **/500** → alle 200, identischer Inhalt (3 Objekte), Canonical auf Seite 1. Crawl-Budget-Verschwendung + Serverlast → am Ende des Crawls **11× 502** (u. a. agent/…/page/169, /177, /179; /ausstattung/balkon/page/2–3, /en/ausstattung/garden|kitchen|balcony) + 3 Timeouts.
2. **robots.txt 404** (s. o.) — bestätigt.
3. **Redirect-Kette** https://dem-gruppe.de → http://www → https://www (Crawl bestätigt).
4. **404:** `/?p=21092` und `/en/?p=21092` intern verlinkt.
5. **H1:** 6 ohne H1 (u. a. `/en/`, `/blog/`, `/anfrageformular/`), 116 mit mehreren H1, 145 doppelte H1.
6. **Titles/Descriptions:** 30 doppelte Titles, 172 Titles > 60 Zeichen, 253 ohne Meta-Description.
7. **Bilder:** 2.393 ohne Alt-Text, 1.143 > 100 KB, 2.413 ohne width/height (CLS).
8. **PageSpeed (SF-PSI):** Performance-Median **44** (n=1.170); render-blocking, unused CSS/JS, Bild-Auslieferung auf fast allen Seiten.
9. **Security-Header:** HSTS, CSP, X-Frame-Options, X-Content-Type-Options, Referrer-Policy fehlen auf allen URLs.
10. **EN-Exposés ohne viewport-Meta** (5 URLs, u. a. /en/property/berlin-exclusive-…, /en/property/attractive-hotel-…).
11. **Autoren-Archive** mit E-Mail im Slug: `/author/roman-kitikgmail-com/` (noindex, aber öffentlich) → Datenschutz/Spam.
12. EN-Exposé `/en/property/restaurant-in-47137-duisburg/` leitet auf DE-Version um.
