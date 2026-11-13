# Overdracht Bison

Dashboard voor de wekelijkse rapportage overdracht van de havendienst Bison (ketenverbetering VH6).

## Gebruiken

1. Open het dashboard via de GitHub Pages-link van deze repo.
2. Klik op **Excel kiezen** (of sleep het bestand op de pagina) en kies de nieuwste `Rapportage overdracht Bison.xlsx`.
3. Het dashboard vult zich met alle weekbladen. Met de filters bovenaan kies je een periode of alleen dag- of nachtdienst.
4. Met **Indeling aanpassen** zet je onderdelen hoger of lager of verberg je ze. Die keuze wordt per browser onthouden.
5. Bij **Meetpunten vergelijken** maak je zoveel vergelijkingen als je wilt (tabbladen), elk met een eigen naam en tot 8 meetpunten: elke kolom uit het Excel, de beleving, het aantal meldingen of een thema uit de meldingen. Kies per vergelijking de grafiek: lijn, staaf, gestapeld, onder elkaar, per dienst (spreiding) of samenhang. Klik op een meetpunt in de legenda om het uit te lichten. Vergelijkingen worden in de browser bewaard; met **Link delen** krijgt een collega dezelfde vergelijking. Met **CSV** download je de cijfers voor Excel, met **PDF** druk je de vergelijking af of sla je hem op als PDF.
6. Bij **Samenhang** vergelijk je alles met één meetpunt naar keuze. Klik op een vak in de matrix of op **Bekijk** voor de details van dat paar; daar kun je het ook als vergelijking bewaren.
7. Bijna alles is klikbaar voor meer details: de kerncijfers, een week in de grafieken, een kleur bij dag/nacht, een partij, een vak in de themakaart, een melding, een stip per dienst. In het detailvenster klik je door naar een dienst of week, en ga je met **Terug** weer terug.
8. Bij elke grafiek onder **Registraties per week** kies je zelf lijn of staaf.

Het Excel wordt alleen in je eigen browser gelezen. Er wordt niets geüpload of opgeslagen, ook niet op GitHub.

## Wat het Excel moet bevatten

- Eén blad per week met in de naam `Week NN JJJJ`, bijvoorbeeld `Week 44 2026`. Het jaartal zorgt ervoor dat week 1 van het nieuwe jaar na week 52 komt. Staat een week twee keer in het bestand (bijv. een gekopieerd blad `Week 44 2026 (2)`), dan telt alleen het eerste blad en meldt het dashboard dat.
- Bovenaan de tabel met kopregel `Datum | Dienst | Beleving | ...` en daaronder dag- en nachtdiensten tot de regel `Totaal`.
- De beleving als celkleur in kolom C: groen, oranje, rood, of roze voor "geen overdracht ontvangen".
- Alle kolommen vanaf D met een kopnaam worden ingelezen, ook kolommen die je later toevoegt. Het voorvoegsel zoals `S:` of `P:` telt niet mee, en de volgorde maakt niet uit. Een nieuwe kolom krijgt vanzelf een grafiek bij "Registraties per week" en komt in "Samenhang" (verband met de beleving en met de andere kolommen). Het dashboard hoeft daarvoor niet te worden aangepast. Houd de kopnaam wel elke week precies hetzelfde, anders telt hij als een andere kolom.
- Het dashboard bepaalt zelf of een kolom een **telling** is (per week opgeteld, lege cel = 0, tekst = 1) of een **meting** (gemiddelde per dienst, zoals vaartijd of sterkte). Woorden als sterkte, tijd, uur, gemiddeld, bezetting of personen in de kopnaam maken er een meting van; anders kijkt het naar de cijfers. Wil je het zeker weten, zet dan `(gem)` of `(som)` achter de kopnaam. Bij een meting telt een 0 als niet ingevuld, behalve bij tijden en uren.
- `In de sterkte aan dek` (kolom H, vanaf het blanco blad van november 2026) is het aantal mensen aan dek dat meetelt voor de wettelijke bemanningseis. Mensen boven de sterkte (bijvoorbeeld herintreders) tellen hier niet mee, dus 4 in de sterkte kan betekenen dat er 5 aan dek staan. Oudere weken met de kop `Personeelsbijzonderheden` blijven een aparte kolom.
- Daaronder het kopje `Oorzaken oranje/rode diensten` met per regel datum, dienst en reden.
- Regels die beginnen met `Extra opmerking` worden ook als melding meegenomen. Staat er geen dag- of nachtdienst in, dan telt de opmerking als algemeen en blijft hij bij beide dienstfilters zichtbaar.
- Een tekst met `Conclusie` komt in het overzicht "Conclusies per week".
- Staat er `Laagwaterperiode` boven de tabel, dan telt die week als laagwaterperiode.

De tabellen met verbeteracties staan in het Excel als plaatjes. Het dashboard leest die plaatjes in de browser met tekstherkenning en toont ze bij **Verbeteracties uit de weekbladen**. Dat werkt alleen via de website (GitHub Pages), niet als je `index.html` als los bestand opent. De eerste keer duurt het ongeveer een halve minuut; daarna onthoudt de browser het. Een enkel woord kan verkeerd gelezen zijn. De samengevoegde lijst "Beste oplossingen" staat apart in `index.html` (zoek op `OPLOSSINGEN`). Ook de thema's en trefwoorden (`THEMAS`) en de partijen (`PARTIJEN`) zijn daar aan te passen.

## Let op

Deze repo is openbaar. Zet het Excel er niet in, want dan kan iedereen de meldingen lezen. Het dashboard kan een bestand `data/rapportage.xlsx` automatisch laden, maar gebruik dat alleen in een privé-omgeving.

## Techniek

Eén HTML-pagina zonder server. `lib/` bevat [d3](https://d3js.org) en [JSZip](https://stuk.github.io/jszip/) met hun licenties, en in `lib/tesseract/` [Tesseract.js](https://github.com/naptha/tesseract.js) 5.1.1 (tekstherkenning, Apache 2.0) met de Nederlandse taaldata uit `@tesseract.js-data/nld` (tessdata `best_int`, Apache 2.0). Alles draait in de browser; er wordt niets naar een server gestuurd.
