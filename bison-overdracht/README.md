# Overdracht Bison

Dashboard voor de wekelijkse rapportage overdracht van de havendienst Bison (ketenverbetering VH6).

## Gebruiken

1. Open het dashboard via de GitHub Pages-link van deze repo.
2. Klik op **Excel kiezen** (of sleep het bestand op de pagina) en kies de nieuwste `Rapportage overdracht Bison.xlsx`.
3. Het dashboard vult zich met alle weekbladen. Met de filters bovenaan kies je een periode of alleen dag- of nachtdienst.

Het Excel wordt alleen in je eigen browser gelezen. Er wordt niets geüpload of opgeslagen, ook niet op GitHub.

## Wat het Excel moet bevatten

- Eén blad per week met in de naam `Week NN JJJJ`, bijvoorbeeld `Week 44 2026`. Het jaartal zorgt ervoor dat week 1 van het nieuwe jaar na week 52 komt. Staat een week twee keer in het bestand (bijv. een gekopieerd blad `Week 44 2026 (2)`), dan telt alleen het eerste blad en meldt het dashboard dat.
- Bovenaan de tabel met kopregel `Datum | Dienst | Beleving | ...` en daaronder dag- en nachtdiensten tot de regel `Totaal`.
- De beleving als celkleur in kolom C: groen, oranje, rood, of roze voor "geen overdracht ontvangen".
- Daaronder het kopje `Oorzaken oranje/rode diensten` met per regel datum, dienst en reden.
- Regels die beginnen met `Extra opmerking` worden ook als melding meegenomen. Staat er geen dag- of nachtdienst in, dan telt de opmerking als algemeen en blijft hij bij beide dienstfilters zichtbaar.
- Een tekst met `Conclusie` komt in het overzicht "Conclusies per week".
- Staat er `Laagwaterperiode` boven de tabel, dan telt die week als laagwaterperiode.

De verbetervoorstellen staan in het Excel als plaatjes en kunnen niet automatisch worden gelezen. De samengevoegde lijst met oplossingen staat daarom in `index.html` (zoek op `OPLOSSINGEN`). Ook de thema's en trefwoorden (`THEMAS`) en de partijen (`PARTIJEN`) zijn daar aan te passen.

## Let op

Deze repo is openbaar. Zet het Excel er niet in, want dan kan iedereen de meldingen lezen. Het dashboard kan een bestand `data/rapportage.xlsx` automatisch laden, maar gebruik dat alleen in een privé-omgeving.

## Techniek

Eén HTML-pagina zonder server. `lib/` bevat [d3](https://d3js.org) en [JSZip](https://stuk.github.io/jszip/) met hun licenties.
