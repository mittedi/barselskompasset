# Juridisk verifikationsagent — Barselskompasset

## Formål
Denne agent verificerer at lovhenvisninger og beregningsregler i Barselskompasset er opdaterede og juridisk korrekte.

## Gældende lovgrundlag (opdateret marts 2026)

- **Barselsloven:** LBK nr 206 af 22/01/2026 (nyeste konsoliderede udgave)
  - URL: https://www.retsinformation.dk/eli/lta/2026/206
- **Funktionærloven:** LBK nr 1002 af 24/08/2017 med ændringer
- **API til opslag:** https://retsinformation-api.dk/v1/lovgivning/{år}/{nummer}/markdown
- **Borger.dk vejledning:** https://www.borger.dk/familie-og-boern/barsel-oversigt/barsel-loenmodtagere/barsel-loenmodtagere-ny-orlovsmodel

## Regler for børn født efter 2. august 2022

### Mor (lønmodtager/funktionær)
| Periode | Uger | Type | Øremærket |
|---|---|---|---|
| Graviditetsorlov FØR fødsel | 4 | Dagpenge / løn via overenskomst | Nej |
| Orlov de første 2 uger EFTER fødsel | 2 | Dagpenge / løn | Ja (pligtorlov) |
| Orlov inden for de første 10 uger | 8 | Dagpenge / løn | Ja |
| Forældreorloven — øremærket | 9 | Dagpenge / løn | Ja — kan ikke overdrages |
| Forældreorloven — overdragelig | 5 | Dagpenge | Nej — kan overdrages til far |
| **Total efter fødsel** | **24** | | |

### Far / medforældre (lønmodtager/funktionær)
| Periode | Uger | Type | Øremærket |
|---|---|---|---|
| Orlov de første 2 uger efter fødsel | 2 | Dagpenge / løn | Ja |
| Forældreorloven — øremærket | 9 | Dagpenge / løn | Ja — kan ikke overdrages |
| Forældreorloven — overdragelig | 13 | Dagpenge | Nej — kan overdrages til mor |
| **Total** | **24** | | |

### Vigtigt: Øremærkede uger
- 9 uger per forælder (lønmodtagere) er øremærket og **skal bruges inden barnet fylder 1 år**
- Bruges de ikke, bortfalder de
- Gælder KUN lønmodtagere — ikke selvstændige eller ledige

## Anmeldelsesfrister
| Hvem | Hvad | Frist |
|---|---|---|
| Mor | Graviditetsorlov (FØR fødsel) | Senest 3 måneder før termin |
| Mor | Barselsorlov (EFTER fødsel) | Senest 8 uger efter fødsel |
| Far/medforældre | Al orlov | Senest 4 uger inden start |

Kilde: Barselsloven §15 og §16 — stadig gældende i LBK nr 206 af 2026.

## Hvad der skal opdateres i koden

### Kritisk — LBK-reference er forældet
Koden refererer til **LBK nr. 816 af 03/06/2021** — dette er den **gamle lov** fra før øremærkning.
Skal ændres til: **LBK nr 206 af 22/01/2026**

### Kritisk — Orlovsmodellen er ændret
Den gamle model (14 uger mor + 32 uger delt) er erstattet af ny model:
- Mor: 4 uger FØR + 24 uger EFTER = 28 uger total
- Far: 24 uger total
- Begge har 9 øremærkede uger der ikke kan overdrages

### Funktionærloven §7 — stadig gældende
- Mor: Ret til løn under graviditetsorlov og barselsorlov (halvløn i 14 uger — mange arbejdsgivere betaler fuld løn via overenskomst)
- Far: Ret til løn under fædreorlov afhænger af arbejdsgivers politik

## Brug af agenten

Kør denne prompt i en ny Claude Code-session for juridisk verifikation:

```
Du er en juridisk verifikationsagent for Barselskompasset.
Læs filen /Users/dittepetraeus/git repos/barselskompasset/index.html
og verificer alle lovhenvisninger og beregningsregler mod:
- LBK nr 206 af 22/01/2026 (barselsloven) via https://retsinformation-api.dk
- Borger.dk: https://www.borger.dk/familie-og-boern/barsel-oversigt/barsel-loenmodtagere/barsel-loenmodtagere-ny-orlovsmodel
Rapporter hvilke paragraffer der er forkerte, forældede eller mangler.
```
