---
name: voetbalbets
description: Dagelijkse voetbalbets kiezen voor de app "Bets van de dag". Gebruik dit wanneer je de tips voor een dag samenstelt, de app vult of de uitslagen van eerdere tips bijwerkt. Richtlijn - odd rond de 2.00, niet te riskant, met ruimte voor uitschieters als het vertrouwen daarom vraagt.
---

# Voetbalbets van de dag

Doel: elke dag een fijn overzicht met inspiratie voor leuke voetbalbets. Geen garanties,
wel goed onderbouwde ideeën die passen bij hoe ik graag wed.

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
  zonder veel extra risico: winst + over 1.5, handicap -1, winst + BTTS nee, enz.
  Of een **kleine combi van twee** sterke, lage odds (label afhankelijk van totale odd).
  Nooit combi's van meer dan twee wedstrijden.
- Liever **3 tot 5 tips** van goede kwaliteit dan een lange lijst. Is er weinig
  te halen (rustige doordeweekse dag), geef dan minder tips en zeg dat eerlijk.
- Elke tip krijgt een **vertrouwen van 1 tot 5**. Een `hoger`-tip heeft minimaal 4.

## Werkwijze

1. Zoek het programma van vandaag (Europe/Amsterdam). Begin bij de grote competities
   (Eredivisie, KKD, Premier League, Championship, Bundesliga, La Liga, Serie A,
   Ligue 1, Jupiler Pro League, Champions/Europa/Conference League) en kijk breder
   als het daar stil is.
2. Zoek per kandidaat de actuele odds (meerdere bronnen), vorm, stand, blessures en
   modelkansen. WebSearch werkt; directe webpagina's ophalen is in de cloud vaak
   geblokkeerd, dus vertrouw op zoekresultaten en vergelijk bronnen.
3. Kies de tips volgens de voorkeuren hierboven. Noteer de odd die je vond, en zet in
   `oddNote` waar die vandaan komt of dat hij indicatief is.
4. Aftraptijden altijd in Nederlandse tijd (`HH:MM`).
5. Werk ook de **uitslagen van de vorige speeldag** bij (`result`: `won`, `lost`,
   `void`), zodat de app een eerlijk scorebord bijhoudt.
6. Schrijf de dag naar de app (zie hieronder) en sluit af met een korte samenvatting:
   die samenvatting is de dagelijkse melding op mijn telefoon.

## Gegevens in de app

De app is een Claude Artifact met een database. Collectie `days`, document-id is de
datum (`YYYY-MM-DD`). Schrijf met de `ArtifactData` tool (`set` voor een nieuwe dag,
`update` met `if_version` voor een bestaande).

```json
{
  "date": "2026-10-23",
  "headline": "Korte kop voor de dag",
  "intro": "Eén of twee zinnen over het aanbod van vandaag.",
  "generatedAt": "2026-10-23T09:45:00+02:00",
  "picks": [
    {
      "id": "alaves-malaga",
      "match": "Alavés - Málaga",
      "competition": "La Liga",
      "kickoff": "21:00",
      "market": "Uitslag (1X2)",
      "pick": "Alavés wint",
      "odd": 1.78,
      "oddNote": "Gemiddelde van meerdere bookmakers, 21 okt",
      "confidence": 4,
      "level": "lager",
      "reasoning": "Waarom deze bet, in 2-4 zinnen.",
      "sources": [{ "label": "Statz", "url": "https://..." }],
      "result": null
    }
  ],
  "quiet": ["Wedstrijden die je bekeek maar bewust oversloeg, met reden (kort)."]
}
```

## Toon

Nederlands, kort en concreet. Geen beloftes of "zekerheidjes". Odds veranderen;
zeg dat je de prijs bij je eigen bookmaker checkt. 18+, speel bewust.
