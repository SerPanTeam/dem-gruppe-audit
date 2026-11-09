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
