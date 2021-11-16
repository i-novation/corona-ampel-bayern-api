# Corona Ampel Bayern API

## Ampeldaten

URL: [https://corona-ampel-bayern.de/data/data.json](https://corona-ampel-bayern.de/data/data.json)

```json
{
    "hospitalizationLast7Days": 1019,
    "hospitalizationLast7DaysIncidence": 7.75,
    "lastUpdate": "2021-11-16T16:29:40.639Z",
    "lastSync": "2021-11-16T16:29:39.026Z",
    "stateInfo": {
        "name": "Bayern",
        "population": 13140183,
        "casesPerWeek": 72817,
        "deathsPerWeek": 45,
        "cases": 950702,
        "deaths": 16648,
        "recovered": 810704,
        "weekIncidence": 554.1551438058359,
        "casesPer100k": 7235.0742756017935,
        "delta": {
            "cases": 9015,
            "deaths": 77,
            "recovered": 5913
        }
    },
    "currentIntensiveCarePatients": 814,
    "state": "red",
    "officialState": "red",
    "nextSwitch": null,
    "yellowPercent": 180.9,
    "redPercent": 135.7
}
```

Feld | Beschreibung
-------- | --------
hospitalizationLast7Days | Neu hospitalisierte Covid Fälle der letzten 7 Tage in Bayern
hospitalizationLast7DaysIncidence | Hospitalisierungsinzidenz der letzten 7 Tage in Bayern
lastUpdate | Letzte Aktualisierung der Daten
lastSync | Letzter Abgleich der Daten mit Quellen
stateInfo | Covid Zahlen in Bayern
currentIntensiveCarePatients | Aktuelle Covid Fälle in Intensivstationen in Bayern
state | Aktueller berechneter Status der Bayerischen Krankenhaus Ampel: `green`, `yellow`, `red`
officialState | Derzeitiger offizieller Status der Bayerischen Krankenhaus Ampel: `green`, `yellow`, `red`
nextSwitch | Info über geplantes Umschalten der Ampel (`null` wenn aktuell kein Umschalten geplant ist)
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

URL 7 Tage Historie: [https://corona-ampel-bayern.de/data/history7days.json](https://corona-ampel-bayern.de/data/history7days.json)

URL 14 Tage Historie: [https://corona-ampel-bayern.de/data/history14days.json](https://corona-ampel-bayern.de/data/history14days.json)

```json
[
  {
    "date": "2021-11-16",
    "hospitalizationLast7Days": "1020",
    "hospitalizationLast7DaysIncidence": "7.80",
    "currentIntensiveCarePatients": "814",
    "lastUpdate": "2021-11-16 14:00:06"
  },
  {
    "date": "2021-11-15",
    "hospitalizationLast7Days": "980",
    "hospitalizationLast7DaysIncidence": "7.50",
    "currentIntensiveCarePatients": "801",
    "lastUpdate": "2021-11-15 13:15:05"
  },
  {
    "date": "2021-11-14",
    "hospitalizationLast7Days": "997",
    "hospitalizationLast7DaysIncidence": "7.60",
    "currentIntensiveCarePatients": "752",
    "lastUpdate": "2021-11-14 17:15:05"
  },
  {
    "date": "2021-11-13",
    "hospitalizationLast7Days": "997",
    "hospitalizationLast7DaysIncidence": "7.60",
    "currentIntensiveCarePatients": "713",
    "lastUpdate": "2021-11-13 17:00:06"
  },
  {
    "date": "2021-11-12",
    "hospitalizationLast7Days": "1000",
    "hospitalizationLast7DaysIncidence": "7.60",
    "currentIntensiveCarePatients": "680",
    "lastUpdate": "2021-11-12 19:45:05"
  },
  {
    "date": "2021-11-11",
    "hospitalizationLast7Days": "955",
    "hospitalizationLast7DaysIncidence": "7.30",
    "currentIntensiveCarePatients": "683",
    "lastUpdate": "2021-11-11 13:15:05"
  },
  {
    "date": "2021-11-10",
    "hospitalizationLast7Days": "957",
    "hospitalizationLast7DaysIncidence": "7.30",
    "currentIntensiveCarePatients": "654",
    "lastUpdate": "2021-11-10 15:30:05"
  }
]
```

Feld | Beschreibung
-------- | --------
date | Datum des Eintrags
hospitalizationLast7Days | Neu hospitalisierte Covid Fälle der letzten 7 Tage in Bayern
hospitalizationLast7DaysIncidence | Hospitalisierungsinzidenz der letzten 7 Tage in Bayern
currentIntensiveCarePatients | Aktuelle Covid Fälle in Intensivstationen in Bayern
lastUpdate | Letzte Aktualisierung der Daten

## Hotspots / Land oder Stadtkreisinformationen

URL: [https://corona-ampel-bayern.de/data/districts.json](https://corona-ampel-bayern.de/data/districts.json)

```json
[
  {
    "ags": "09161",
    "name": "Ingolstadt",
    "county": "SK Ingolstadt",
    "weekIncidence": 530.11,
    "ilsName": "Leitstelle Ingolstadt",
    "ilsPercentOccupied": 87.83,
    "ilsDate": "2021-11-16",
    "hasHotSpotCriteria": true,
    "hotSpotCriteria": {
      "hasIncidenceCriteria": true,
      "hasPercentOccupiedCriteria": true
    }
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
ilsPercentOccupied | Prozentuale Belegung der Intensivkapazität
ilsDate | Datum des Intensivregistereintrags
hasHotSpotCriteria | Sind Hotspotkriterien erfüllt?
hotSpotCriteria | Welche der beiden Hotspotkriterien sind derzeit erfüllt

# Datenquellen von corona-ampel-bayern.de

- [Baverisches Landesamt für Gesundheit und lebensmittelsicherheit](https://www.lgl.bayern.de/gesundheit/infektionsschutz/infektionskrankheiten_a_z/coronavirus/karte_coronavirus/index.htm)
- [intensivregister.de](https://www.intensivregister.de/)
- [api.corona-zahlen.org](https://api.corona-zahlen.org/)