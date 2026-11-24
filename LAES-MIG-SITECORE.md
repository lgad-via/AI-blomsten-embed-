# AI-Blomsten – tre selvstændige funktioner til Sitecore

Denne pakke er lavet ud fra AI-blomsten 3.0.

## Funktioner
1. `plakat.html` – vælg, download og udskriv plakat.
2. `plakat-editor.html` – den eksisterende editor til at lave din egen plakat.
3. `ai-blomst.html` – den **rigtige interaktive AI-blomst** fra `#lav-din-egen-blomst`, med seks blade, forklaringer og download/kopi.

## Upload til GitHub Pages
1. Opret/brug et offentligt repository, eksempelvis `AI-blomst-embed`.
2. Upload **indholdet** af `site`-mappen direkte til repositoryets rod (ikke selve mappen).
3. Slå GitHub Pages til under Settings > Pages: Deploy from branch, main, /(root).
4. Kontrollér adresserne:
   - https://lgad-via.github.io/AI-blomst-embed/plakat.html
   - https://lgad-via.github.io/AI-blomst-embed/plakat-editor.html
   - https://lgad-via.github.io/AI-blomst-embed/ai-blomst.html
   Alle tre adresser er allerede tilpasset dit repository.

## Sitecore
Giv Sitecore-udvikleren `SITECORE-INTEGRATION-3-FUNKTIONER.html`.
- Der er **tre separate iframes**. Brug kun den relevante iframe på den relevante Sitecore-side.
- Kopiér det fælles script til de sider, der indeholder en iframe. Scriptet lytter på sikre beskeder fra GitHub Pages og tilpasser højden.
- Sitecores origin er allerede sat til `https://ai-blomsten.via.dk` i alle tre iframe-adresser.
- Sitecore skal tillade iframes og JavaScript. CSP `frame-src` skal tillade `https://lgad-via.github.io`.
- `lang=da|en` og `theme=light|dark` er URL-parametre. Plakatsidens kontroller oversættes; AI-blomst og plakat-editor har fortsat dele af deres oprindelige danske grænseflade.
- Ved flere iframes på samme side skelner scriptet mellem dem ved `event.source`.

## Vigtigt om AI-blomst
`ai-blomst.html` genbruger den originale interaktive blomsts HTML og JavaScript for at bevare funktionerne. Den øvrige hjemmesides header, navigation, sidefod og andre sektioner er skjult, men original kode er stadig inkluderet. Det er ikke en fuldstændig adskilt, optimeret komponent. Test den i Sitecore inden offentlig lancering.

## Opdater en eksisterende AI-blomst
Overskriv `ai-blomst.html` og `embed-bridge.js` i GitHub-repositoryets rod, og upload også `via-theme.css` og mappen `fonts`. Den eksisterende iframe-adresse kan genbruges. Med integrationsscriptet i Sitecore følger iframens højde indholdet.

## Test
Åbn alle tre adresser direkte efter upload. Test bladvalg, forklaringer, download/kopi, plakat-download/print, mobilvisning og iframe-højde. Browserens sikkerhedsregler kan påvirke udklipsholder og print.

Der er ikke foretaget ændringer direkte i GitHub eller Sitecore.

## Konfiguration klar
Sitecore: `https://ai-blomsten.via.dk`
GitHub Pages: `https://lgad-via.github.io/AI-blomst-embed/`
Alle tre iframe-adresser og `parentOrigin` er indsat i integrationsfilen. Ingen manuel ændring af domæner er nødvendig. Sitecore-udvikleren skal stadig placere iframes og integrationsscript i Sitecore og sikre tilladelser i CSP.
