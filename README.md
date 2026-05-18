# Andreas Lindeman portefølje

Statisk portefølje. Ingen byggesteg, ingen rammeverk. Slipp den rett inn på en hvilken som helst statisk host.

## Struktur

```
norwegian/
├── index.html              # landingssiden (hero, om, tidslinje, verktøy, kontakt)
├── style.css               # alle stiler, inkludert prosjektsider
├── script.js               # tidslinjerendering, filtre, tooltip
├── projects_data/
│   ├── manifest.json       # lister hver oppføringsfil under
│   └── *.json              # én fil per tidslinjeoppføring
└── projects/
    ├── _template.html      # kopier denne når du legger til et nytt dypdykk
    └── *.html              # én fil per dypdykk
```

## Publiser på GitHub Pages

1. Skyv denne mappa til et repo (f.eks. `andreas-lindeman/andreas-lindeman.github.io`,
   eller et hvilket som helst repo med Pages slått på).
2. Under **Settings → Pages**, sett kilde til `main`-branchen / rot.
3. Ferdig. Siden er på lufta på Pages-URL-en innen et minutt.

For et eget domene, legg en `CNAME`-fil i rota med domenet og pek DNS-en mot GitHub.

## Legge til en ny tidslinjeoppføring

1. Lag en ny JSON-fil i `projects_data/`, med navnet
   `YYYY-kort-slug.json`. Bruk en eksisterende fil som mal. Skjemaet er:

   ```json
   {
     "id": "unik-id",
     "title": "Visningstittel",
     "category": "work | school | hobby",
     "isProject": true,
     "start": "YYYY",            // eller "YYYY-MM"
     "end": "YYYY",              // valgfri, kan også være "YYYY-MM" eller "present"
     "shortDescription": "Vises i tooltipen og mobillista.",
     "tags": ["python", "ml"],
     "projectPage": "projects/<slug>",             // valgfri, ren URL uten .html
     "externalLinks": [                            // valgfri
       { "label": "GitHub", "url": "https://...", "type": "github" }
     ],
     "status": "nda | lost | ongoing",            // valgfri
     "statusNote": "Fritekst som vises ved siden av statustaggen." // valgfri
   }
   ```

2. Legg filnavnet inn i `projects_data/manifest.json` så lasteren plukker det opp.
3. (Valgfritt) Hvis `projectPage` er satt, kopier `projects/_template.html` til den
   stien og fyll inn.

Det er alt. Ingen JS å pirke i, tidslinjen bygges på nytt fra JSON-ene.

## Verktøy

De delte SEO- og PDF-verktøyene ligger i `../tools/` (utenfor språkmappene) og
deles mellom alle språkversjoner. Kjør dem med `--site`-flagget for å peke på
denne mappa:

```
python ../tools/build_seo.py --site norwegian
python ../tools/extract_pdfs.py --site norwegian
```

## En kommentar om innramming

Et par av oppføringene på tidslinjen kommer fra en periode i livet mitt der jeg
var tenåring og gjorde ting jeg ville håndtert helt annerledes i dag.
Hovedsiden bruker nøytrale formuleringer for de oppføringene: «første frittstående
Python-program», «selvlært cybersikkerhetsforskning», «utforskning av
nettverkssystemer». Dypdykkene bak dem er ærlige om hva som faktisk skjedde,
hva jeg lærte, og hva jeg ville endret. Poenget med å ta dem med er ikke å
skryte. Det er å vise stien ærlig, og de tekniske lærdommene er ekte.
