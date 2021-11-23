# Corona Ampel Bayern API

API-Dokumentation [Corona Ampel Bayern](corona-ampel-bayern.de)

## Ampeldaten

URL: [https://corona-ampel-bayern.de/data/data.json](https://corona-ampel-bayern.de/data/data.json)

```json
{
    "hospitalizationLast7Days": 1248,
    "hospitalizationLast7DaysIncidence": 9.5,
    "lastUpdate": "2021-11-23T03:02:42.000Z",
    "lastSync": "2021-11-23T21:00:00.729Z",
    "stateInfo": {
        "name": "Bayern",
        "population": 13140183,
        "casesPerWeek": 84737,
        "deathsPerWeek": 61,
        "cases": 1040178,
        "deaths": 17048,
        "recovered": 860942,
        "weekIncidence": 644.8692533429709,
        "casesPer100k": 7916.008475681047,
        "delta": {
            "cases": 8624,
            "deaths": 81,
            "recovered": 9461
        }
    },
    "currentIntensiveCarePatients": 961,
    "currentIntensiveCareUpdateDate": "2021-11-23T20:05:00Z",
    "state": "red",
    "officialState": "red",
    "nextSwitch": null,
    "info": "Breaking Changes! Wavebreaker ...",
    "yellowPercent": 213.6,
    "redPercent": 160.2
}
```

Feld | Beschreibung
-------- | --------
hospitalizationLast7Days | Neu hospitalisierte Covid Fälle der letzten 7 Tage in Bayern
hospitalizationLast7DaysIncidence | Hospitalisierungsinzidenz der letzten 7 Tage in Bayern
lastUpdate | Datenstand der Hospitalisierungsdaten
lastSync | Letzter Abgleich der Daten mit Quellen
stateInfo | Covid Zahlen in Bayern
currentIntensiveCarePatients | Aktuelle Covid Fälle in Intensivstationen in Bayern
currentIntensiveCareUpdateDate | Datenstand der Covid Fälle auf Intesiv
state | Aktueller berechneter Status der Bayerischen Krankenhaus Ampel: `green`, `yellow`, `red`
officialState | Derzeitiger offizieller Status der Bayerischen Krankenhaus Ampel: `green`, `yellow`, `red`
nextSwitch | Info über geplantes Umschalten der Ampel (`null` wenn aktuell kein Umschalten geplant ist)
info | Info Text, der über Änderungen informiert
yellowPercent | Prozent des Schwellwerts von Stufe Gelb
redPercent | Prozent des Schwellwerts von Stufe Rot

Beispiel nextSwitch innerhalb von data.json:

```json
{
    ...
    "nextSwitch": {
        "date": "2021-11-09",
        "state": "red"
    }
    ...
}
```

Feld | Beschreibung
-------- | --------
date | Umschaltedatum der Ampel
state | Status auf den umgeschalten wird

## Historie

URL: [https://corona-ampel-bayern.de/data/history.json](https://corona-ampel-bayern.de/data/history.json)

```json
{
    "ilsHistory": [
        {
            "date": "2021-11-23",
            "currentIntensiveCarePatients": "962",
            "bedsFree": "298",
            "bedsOccipued": "2887"
        },
        ...
        {
            "date": "2021-11-10",
            "currentIntensiveCarePatients": "653",
            "bedsFree": "283",
            "bedsOccipued": "2821"
        }
    ],
    "frozenIncidence": [
        {
            "weekIncidence": 644.8692533429709,
            "date": "2021-11-23"
        },
        ...
        {
            "weekIncidence": 395.7859643202838,
            "date": "2021-11-10"
        }
    ],
    "incidence": [
        {
            "weekIncidence": 644.8692533429709,
            "date": "2021-11-22"
        },
        ...
        {
            "weekIncidence": 431.0137842068105,
            "date": "2021-11-09"
        }
    ],
    "frozenHospitalization": [
        {
            "date": "2021-11-23",
            "hospitalizationLast7Days": 1248,
            "hospitalizationLast7DaysIncidence": 9.5
        },
        ...
        {
            "date": "2021-11-10",
            "hospitalizationLast7Days": 957,
            "hospitalizationLast7DaysIncidence": 7.3
        }
    ],
    "hospitalization": [
        {
            "hospitalizationLast7Days": 1248,
            "hospitalizationLast7DaysIncidence": 9.5,
            "date": "2021-11-23"
        },
        ...
        {
            "hospitalizationLast7Days": 1751,
            "hospitalizationLast7DaysIncidence": 13.33,
            "date": "2021-11-10"
        }
    ]
}
```

Feld | Beschreibung
-------- | --------
ilsHistory | Historiendaten über Intensivauslastung
frozenIncidence | 7 Tage Inzidenz ohne Nachmeldungen
incidence | 7 Tage Inzidenz inkl. Nachmeldungen
frozenHospitalization | Hospitalisierung ohne Nachmeldungen
hospitalization | Hospitalisierung inkl Nachmeldungen

## Hotspots / Land oder Stadtkreisinformationen

URL: [https://corona-ampel-bayern.de/data/districts.json](https://corona-ampel-bayern.de/data/districts.json)

```json
[
    {
        "ags": "09161",
        "name": "Ingolstadt",
        "county": "SK Ingolstadt",
        "weekIncidence": 600.21,
        "ilsName": "Leitstelle Ingolstadt",
        "ilsBedsFree": 11,
        "ilsBedsOccupied": 108,
        "ilsPercentOccupied": 90.76,
        "ilsCurrentCovidCases": 35,
        "ilsPercentCovidCases": 32.41,
        "ilsDate": "2021-11-23",
        "hasHotSpotCriteria": true,
        "hotSpotCriteria": {
            "hasIncidenceCriteria": true,
            "hasPercentOccupiedCriteria": true
        },
        "hasWavebreakerHotSpotCriteria": false
    },
  ...
]
```

Feld | Beschreibung
-------- | --------
ags | AGS Nummer des Kreises
name | Name
county | Detailierter Name
weekIncidence | Aktuelle 7 Tage Inzidenz
ilsName | Name der zuständigen Leitstelle
ilsBedsFree | Freie Intensivvetten der zugehörigen Leitstelle
ilsBedsOccupied | Belegte Intensivvetten der zugehörigen Leitstelle
ilsPercentOccupied | Prozentuale Belegung der Intensivkapazität der zugehörigen Leitstelle
ilsCurrentCovidCases | Anzahl Covid-19 Patienten der zugehörigen Leitstelle
ilsPercentCovidCases | Anteil Covid-19 Patienten der zugehörigen Leistelle
ilsDate | Datum des Intensivregistereintrags der zugehörigen Leitstelle
hasHotSpotCriteria | Sind Hotspotkriterien erfüllt?
hotSpotCriteria | Welche der beiden Hotspotkriterien sind derzeit erfüllt
hasWavebreakerHotSpotCriteria | Ist das Hotspotkriterium der Wellenbrechermaßnahmen erfüllt

# Datenquellen von corona-ampel-bayern.de

- [intensivregister.de](https://www.intensivregister.de/)
- [api.corona-zahlen.org](https://api.corona-zahlen.org/)
