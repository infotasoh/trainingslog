---
name: voetbalbets
description: Dagelijkse sportbets kiezen voor de app "Bets van de dag" (voetbal, NBA, NHL, tennis en meer). Gebruik dit wanneer je de tips voor een dag samenstelt, de app vult of de uitslagen en het puntensysteem bijwerkt. Richtlijn - odd rond de 2.00, niet te riskant, met ruimte voor uitschieters als het vertrouwen daarom vraagt.
---

# Bets van de dag

Doel: elke dag een fijn overzicht met inspiratie voor leuke bets, verdeeld over sporten.
Geen garanties, wel goed onderbouwde ideeën die passen bij hoe ik graag wed.

## Mijn voorkeuren

- **Richt-odd: ongeveer 2.00.** Normaal zoeken we tussen **1.80 en 2.20**.
- **Niet te riskant.** Liever een markt met duidelijke onderbouwing (vorm, blessures,
  thuis/uit, onderlinge duels, modelkansen) dan een gok op een gelijkopgaande wedstrijd.
- **Uitschieters mogen, maar benoem ze.**
  - **Hoger (2.20 - 2.80):** alleen als je er echt veel vertrouwen in hebt en de prijs
    beter is dan de kans doet vermoeden (value). Label: `hoger`.
  - **Lager (1.50 - 1.80):** als het extra veilig is en een lagere odd daarom te
    verantwoorden valt. Label: `lager`.
  - Binnen 1.80 - 2.20 is het label `kern`.
- Als een favoriet te laag staat (bijv. 1.35), zoek een markt die richting 2.00 brengt
  zonder veel extra risico: winst + over 1.5, handicap, winst + BTTS nee, enz.
- **Combi-bets zijn welkom.** Meerdere lage, zeer waarschijnlijke uitkomsten samen naar
  een totaal rond de 2.00, bijvoorbeeld drie keer ongeveer 1.25 (1.25 × 1.25 × 1.25 = 1.95).
  Regels voor een combi:
  - **2 tot 4 wedstrijden**, elk tussen ongeveer **1.15 en 1.50**.
  - Elke leg moet een **modelkans van minstens 75-80%** hebben. Eén twijfelgeval maakt
    de hele combi fout, dus liever een leg weglaten dan een gok erbij.
  - Totale odd = het product van de legs, afgerond op 2 decimalen; label zoals bij losse
    tips (`kern` 1.80-2.20, `lager`, `hoger`).
  - Geen twee legs uit dezelfde wedstrijd, en reken eerlijk: drie keer 80% is samen
    ongeveer 51%. Zet die gecombineerde kans in de analyse.
  - Een combi telt op het scorebord als **één** voorspelling: goed alleen als alle legs
    goed zijn (void-legs vallen weg).
  - Mik op 1 à 2 combi's per dag naast de losse tips.
- **4 tot 8 tips per dag**, verdeeld over zoveel mogelijk sporten waar het aanbod goed is
  (streef naar minstens 3 sporten). Kwaliteit gaat
  voor aantal: is er weinig te halen, geef dan minder tips en zeg dat eerlijk.
- Elke tip krijgt een **vertrouwen van 1 tot 5**. Een `hoger`-tip heeft minimaal 4.

## Sporten

Een combi krijgt `"type": "combi"` en verschijnt in de app onder "Combi's" (zie het
voorbeeld onderaan). Waarde voor `sport` bij losse tips en per combi-leg (de app groepeert hierop): `voetbal`, `basketbal` (NBA, EuroLeague),
`ijshockey` (NHL), `tennis`, `american-football` (NFL), `honkbal` (MLB), `darts`,
`handbal`, `volleybal`, `f1`, `mma`, `boksen`, `rugby`, `wielrennen`.
Voetbal blijft de basis. Kijk daarnaast elke dag actief naar wat er speelt: NBA en NHL
(oktober - juni), NFL (september - februari, vooral zondag/maandag), tennis (ATP/WTA),
darts (PDC), MLB (april - oktober). NBA/NHL/NFL spelen 's nachts in Nederlandse tijd;
geef die tijd dan aan als bijvoorbeeld `02:00 (nacht)`.

## Kijk naar alles: opstellingen, formaties en context

Een bet is pas goed onderbouwd als je weet wie er speelt. Check per wedstrijd:

- **Blessures en schorsingen**, vooral van sleutelspelers: topscorer, spelmaker, eerste
  keeper, aanvoerder, centrale verdediger. Hoeveel procent van de goals/assists valt weg?
- **Verwachte of officiële opstelling en formatie** (bijv. 4-3-3 tegen 3-5-2). Welke
  formaties passen slecht bij elkaar? Speelt een ploeg met een nood-verdediging?
- **Rotatie**: Europese wedstrijd midweek, bekerduel, belangrijke wedstrijd in het verschiet.
- **Trainerswissel** (nieuwe trainer-effect), interne onrust, motivatie (degradatie,
  titelstrijd, niets meer te spelen).
- **Speelschema**: back-to-backs en reizen (NBA/NHL), korte rust, jetlag.
- **Sportspecifiek**: NHL de startende keeper, MLB de startende werper, NFL de status van
  de quarterback, tennis fitheid en ondergrond, darts recente gemiddelden.
- **Thuis/uit**: controleer waar de wedstrijd echt gespeeld wordt (niet aannemen op basis
  van de volgorde van de namen; Amerikaanse sites zetten de uitploeg vaak eerst).
- **Weer en veld** bij buitensporten (wind en regen drukken het aantal goals/punten).
- Scheidsrechter bij kaarten-markten, onderlinge duels, vorm thuis/uit apart.

Leg dit vast in het veld `lineups` van elke losse tip (zie schema) en verwerk het in de
analyse: wat betekent de afwezigheid of formatie concreet voor deze bet?

### Check vlak voor de wedstrijd

Om 13:10 en 19:10 draait een extra check. Die kijkt voor alle tips van vandaag die nog
niet begonnen zijn of de officiële opstellingen, laatste blessurenieuws en keepers/werpers
nog kloppen met de analyse, en zet `lineupCheck`:

- `bevestigd`: niets veranderd, de tip blijft staan.
- `aangepast`: de markt is vóór de aftrap aangepast (bijv. een lagere handicap) omdat de
  opstelling daar aanleiding toe gaf. Leg in `note` uit wat er veranderde.
- `ingetrokken`: een concrete opstellingsreden maakt de tip te riskant (topspeler valt
  last-minute weg, keeper geschorst, B-elftal). De tip krijgt `result: "void"` en telt dus
  niet mee op het scorebord. Alleen bij harde nieuwsfeiten, nooit op gevoel, en altijd vóór
  de aftrap. Benoem het in de `review` van de volgende dag.

## Puntensysteem (Claude's scorebord)

- Elke tip die **goed** is: **+3 punten**. Elke tip die **fout** is: **−5 punten**.
  Geannuleerd (`void`) telt niet mee. Of de gebruiker de bet gezet heeft maakt niet uit.
- De app rekent de punten zelf uit op basis van `result`; jij vult alleen `result` in.
- Break-even ligt op **63% goed**. Bij odds rond 2.00 is dat een hoge lat, dus kies alleen
  tips waarvan je echt denkt dat de kans duidelijk groter is dan de odd aangeeft.
- **Zelfcorrectie, elke dag vóór je nieuwe tips kiest:**
  1. Zet de uitslagen van de vorige dag(en) (`won`, `lost`, `void`).
  2. Bekijk de laatste 7 dagen: welke sporten, markten en labels gingen fout?
  3. Schrijf in het veld `review` van vandaag een eerlijke evaluatie (3-6 zinnen):
     wat ging goed, wat ging fout en waarom, en wat je vandaag anders doet.
  4. Staat het saldo van de laatste 7 dagen **onder nul**, dan word je strenger:
     maximaal 4 tips, alleen vertrouwen 4 of 5, geen `hoger`-tips, en mijd de
     sporten/markten die fout gingen. Staat het saldo van de laatste 7 dagen op
     −15 of lager, dan maximaal 3 tips en alleen markten met modelkans boven 60%.

## Werkwijze

1. Werk uitslagen, punten-evaluatie en `review` bij (zie hierboven).
2. Zoek het programma van vandaag (Europe/Amsterdam) per sport. WebSearch werkt; directe
   webpagina's ophalen is in de cloud vaak geblokkeerd, dus vergelijk zoekresultaten.
3. Zoek per kandidaat actuele odds (meerdere bronnen), vorm, stand, blessures en
   modelkansen. Noteer de gevonden odd en zet in `oddNote` waar hij vandaan komt.
4. Kies de tips volgens de voorkeuren. Schrijf per tip:
   - `reasoning`: één krachtige zin, de kern van de bet.
   - `keyFactors`: 3-5 korte, concrete feiten (cijfers!).
   - `analysis`: een **lange uitleg** van 3-5 alinea's (samen 200-400 woorden): de vorm
     van beide ploegen, blessures, onderlinge duels, wat modellen en bookmakers zeggen,
     waarom deze markt en niet een andere, en waarom de kans groot is dat hij goed gaat.
   - `risks`: wat er mis kan gaan, in één of twee zinnen.
5. Logo's en live scores: de app haalt echte logo's en live standen bij ESPN op, in de
   browser van de gebruiker. Geef daarom per tip `espn: {"league": "...", "date": "YYYYMMDD"}`
   mee. `date` is de datum zoals ESPN hem gebruikt (Amerikaanse datum: een NBA-wedstrijd
   om 03:00 Nederlandse tijd op de 24e hoort bij `date` van de 23e). Teamnamen in `home.name`
   en `away.name` moeten herkenbaar zijn voor ESPN (bijv. "Trail Blazers", "Ajax",
   "Mönchengladbach"); bij twijfel zet je de volledige ESPN-naam in `home.espnName`.
   Geef ook `short` (2-3 letters) en `c1`/`c2` (clubkleuren hex): dat is de reserve als ESPN
   niets vindt. ESPN-competities (`league`):
   - Voetbal: `soccer/ned.1` (Eredivisie), `soccer/ned.2` (KKD), `soccer/eng.1`, `soccer/eng.2`,
     `soccer/esp.1`, `soccer/ger.1`, `soccer/ger.2`, `soccer/ita.1`, `soccer/fra.1`, `soccer/bel.1`,
     `soccer/por.1`, `soccer/tur.1`, `soccer/sco.1`, `soccer/ksa.1`, `soccer/usa.1`,
     `soccer/uefa.champions`, `soccer/uefa.europa`, `soccer/uefa.europa.conf`, `soccer/ned.cup`
   - `basketball/nba`, `basketball/wnba`, `hockey/nhl`, `football/nfl`,
     `football/college-football`, `baseball/mlb`, `mma/ufc`, `racing/f1`
   - Tennis, darts, handbal, volleybal: geen `espn`-veld (dan toont de app clubkleuren).
6. Schrijf de dag naar de app (zie hieronder) en sluit af met een korte samenvatting: die
   samenvatting is de dagelijkse pushmelding.

## Gegevens in de app

De app is een website op GitHub Pages: https://infotasoh.github.io/trainingslog/voetbalbets/
De gegevens zijn JSON-bestanden in de repo `infotasoh/trainingslog`, op branch `main`:

- `voetbalbets/data/days/YYYY-MM-DD.json`: één bestand per dag (schema hieronder).
- `voetbalbets/data/index.json`: `{"days": ["2026-10-24", "2026-10-23", ...]}`; voeg de nieuwe
  datum toe (nieuwste eerst).

Werk uitslagen bij in de bestanden van eerdere dagen. Commit alles in één commit
("Bets van <datum>") en push naar `main`. Pas nooit code aan, alleen `voetbalbets/data/`.

```json
{
  "date": "2026-10-23",
  "headline": "Korte kop voor de dag",
  "intro": "Eén of twee zinnen over het aanbod van vandaag.",
  "generatedAt": "2026-10-23T09:45:00+02:00",
  "review": "Eerlijke evaluatie van de vorige dag(en) en wat je vandaag anders doet.",
  "picks": [
    {
      "id": "alaves-malaga",
      "sport": "voetbal",
      "match": "Alavés - Málaga",
      "home": { "name": "Alavés", "short": "ALA", "c1": "#1F4E9C", "c2": "#FFFFFF" },
      "away": { "name": "Málaga", "short": "MAL", "c1": "#6CB4E4", "c2": "#FFFFFF" },
      "espn": { "league": "soccer/esp.1", "date": "20261023" },
      "competition": "La Liga",
      "kickoff": "21:00",
      "market": "Uitslag (1X2)",
      "pick": "Alavés wint",
      "odd": 1.80,
      "oddNote": "Betfred en William Hill 1.80, 21 okt",
      "confidence": 4,
      "level": "kern",
      "reasoning": "De kern van de bet in één zin.",
      "keyFactors": ["Feit 1", "Feit 2", "Feit 3"],
      "analysis": ["Alinea 1", "Alinea 2", "Alinea 3"],
      "risks": "Wat kan er misgaan.",
      "lineups": {
        "status": "verwacht",
        "home": { "formation": "3-5-2", "missing": ["Garcés (kruisband)"], "note": "Boyé en Martínez voorin" },
        "away": { "formation": "4-2-3-1", "missing": ["Muñoz (kuit)", "Murillo (twijfel)"], "note": "..." },
        "impact": "Wat de afwezigen en formaties betekenen voor deze bet."
      },
      "lineupCheck": { "at": "19:10", "status": "bevestigd", "note": "Officiële opstelling zoals verwacht." },
      "sources": [{ "label": "Statz", "url": "https://..." }],
      "result": null
    }
  ],
  "quiet": ["Wedstrijden die je bekeek maar bewust oversloeg, met reden (kort)."]
}
```

Een combi in `picks` (zelfde velden als een losse tip, maar met `legs` in plaats van
`match`/`home`/`away`/`market`/`pick`; `odd` is de totale odd):

```json
{
  "id": "combi-3-thuisfavorieten",
  "type": "combi",
  "title": "Drie thuisfavorieten",
  "odd": 1.95,
  "oddNote": "1.25 × 1.22 × 1.28 = 1.95",
  "confidence": 4,
  "level": "kern",
  "legs": [
    {
      "match": "PSV - Heracles", "sport": "voetbal", "competition": "Eredivisie", "kickoff": "20:00",
      "home": { "name": "PSV", "short": "PSV", "c1": "#ED1C24", "c2": "#FFFFFF" },
      "away": { "name": "Heracles", "short": "HER", "c1": "#000000", "c2": "#FFFFFF" },
      "espn": { "league": "soccer/ned.1", "date": "20261024" },
      "market": "Uitslag (1X2)", "pick": "PSV wint", "odd": 1.25, "result": null
    }
  ],
  "reasoning": "...", "keyFactors": ["..."], "analysis": ["..."], "risks": "...",
  "sources": [{ "label": "...", "url": "https://..." }],
  "result": null
}
```

Bij de uitslagen: zet `result` per leg én op de combi zelf (`won` alleen als alle legs
`won`/`void` zijn en minstens één `won`; anders `lost`).

## Toon

Nederlands, concreet, met cijfers. Geen beloftes of "zekerheidjes". Odds veranderen;
zeg dat je de prijs bij je eigen bookmaker checkt. 18+, speel bewust.
