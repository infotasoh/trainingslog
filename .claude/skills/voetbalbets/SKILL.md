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
  Of een **kleine combi van twee** sterke, lage odds. Nooit combi's van meer dan twee.
- **3 tot 6 tips per dag**, verdeeld over sporten waar het aanbod goed is. Kwaliteit gaat
  voor aantal: is er weinig te halen, geef dan minder tips en zeg dat eerlijk.
- Elke tip krijgt een **vertrouwen van 1 tot 5**. Een `hoger`-tip heeft minimaal 4.

## Sporten

Waarde voor `sport` (de app groepeert hierop): `voetbal`, `basketbal` (NBA, EuroLeague),
`ijshockey` (NHL), `tennis`, `american-football` (NFL), `honkbal` (MLB), `darts`,
`handbal`, `volleybal`, `f1`, `mma`, `boksen`, `rugby`, `wielrennen`.
Voetbal blijft de basis. Kijk daarnaast elke dag naar wat er speelt: NBA en NHL
(oktober - juni), NFL (september - februari, vooral zondag/maandag), tennis (ATP/WTA),
darts (PDC), MLB (april - oktober). NBA/NHL/NFL spelen 's nachts in Nederlandse tijd;
geef die tijd dan aan als bijvoorbeeld `02:00 (nacht)`.

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
5. Teamlogo's: de app tekent een clubschild in de clubkleuren. Geef per team `name`,
   `short` (2-3 letters, bijv. AJA, PSV, LAL) en `c1`/`c2` (primaire en secundaire
   clubkleur als hex). Bij tennis/darts/MMA: de spelers met landkleuren.
6. Schrijf de dag naar de app en sluit af met een korte samenvatting: die samenvatting
   is de dagelijkse pushmelding.

## Gegevens in de app

Artifact https://claude.ai/artifact/RU7zftJ1ofXvDM2wjuJUDX met een database.
Collectie `days`, document-id is de datum (`YYYY-MM-DD`). Schrijf met de `ArtifactData`
tool (`set` voor een nieuwe dag, `update` met `if_version` voor een bestaande).

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
      "sources": [{ "label": "Statz", "url": "https://..." }],
      "result": null
    }
  ],
  "quiet": ["Wedstrijden die je bekeek maar bewust oversloeg, met reden (kort)."]
}
```

## Toon

Nederlands, concreet, met cijfers. Geen beloftes of "zekerheidjes". Odds veranderen;
zeg dat je de prijs bij je eigen bookmaker checkt. 18+, speel bewust.
