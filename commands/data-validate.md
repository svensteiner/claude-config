# /data-pipeline:validate

## Description
Validiert Datenqualitat und Schema.

## Usage
```
/data-pipeline:validate <data> [schema] [--strict]
```

## Parameters
- `data` - Zu validierende Datei
- `schema` - Optional: Schema-Definition (JSON/YAML)
- `--strict` - Fehler bei Warnings

## Examples

### Quick Validation
```
/data-pipeline:validate data.csv

-> Basis-Checks (Nulls, Duplicates, Types)
-> Generiert Report
-> Empfehlungen
```

### Mit Schema
```
/data-pipeline:validate orders.csv orders_schema.json

-> Pruft gegen definiertes Schema
-> Typ-Validierung
-> Wertebereich-Prufung
-> Required Fields
```

### Trading Data Validation
```
/data-pipeline:validate ohlcv.csv --type=trading

-> OHLCV-spezifische Validierung
-> High >= Low Check
-> Chronologie Check
-> Gap Detection
```

## Validation Checks

### Basis-Checks (immer)
| Check | Beschreibung |
|-------|--------------|
| Null Values | Anzahl und Prozent pro Spalte |
| Duplicates | Doppelte Zeilen |
| Data Types | Konsistente Typen |
| Empty Strings | Leere Strings als Nulls |

### Schema-Checks (mit Schema)
| Check | Beschreibung |
|-------|--------------|
| Required Columns | Pflichtfelder vorhanden |
| Data Types | Erwartete Typen |
| Value Ranges | Min/Max Werte |
| Allowed Values | Enum-Validierung |
| Regex Patterns | Format-Validierung |

### Trading-Checks (--type=trading)
| Check | Beschreibung |
|-------|--------------|
| OHLC Logic | High >= Open, Close >= Low |
| Chronology | Daten in zeitlicher Reihenfolge |
| Gaps | Fehlende Zeitpunkte |
| Negative Values | Keine negativen Preise |
| Volume | Keine negativen Volumen |

## Agents Used
- **data-validator** - Validierung
- **data-analyst** - Anomalie-Erkennung
