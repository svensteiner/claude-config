# /data-pipeline:visualize

## Description
Erstellt Datenvisualisierungen und Charts.

## Usage
```
/data-pipeline:visualize <data> <chart_type> [options]
```

## Parameters
- `data` - Datei oder DataFrame
- `chart_type` - line, bar, scatter, heatmap, candlestick, dashboard
- `options` - Chart-spezifische Optionen

## Examples

### Line Chart
```
/data-pipeline:visualize sales.csv line --x=date --y=revenue

-> Erstellt Liniendiagramm
-> X-Achse: Datum
-> Y-Achse: Umsatz
```

### Trading Candlestick
```
/data-pipeline:visualize btc.csv candlestick --indicators=SMA,RSI

-> Candlestick Chart
-> Mit Moving Average Overlay
-> RSI als Subplot
```

### Correlation Heatmap
```
/data-pipeline:visualize data.csv heatmap --columns=price,volume,returns

-> Korrelationsmatrix
-> Farbkodiert
-> Mit Werten annotiert
```

### Dashboard
```
/data-pipeline:visualize monthly_report.csv dashboard

-> 4-Panel Dashboard
-> Trend, Verteilung, Top 10, Vergleich
-> Interaktiv (Plotly)
```

## Chart Types

### Standard Charts
| Type | Use Case | Beispiel |
|------|----------|----------|
| `line` | Trends uber Zeit | Umsatz pro Monat |
| `bar` | Kategorien vergleichen | Umsatz pro Region |
| `scatter` | Korrelation | Preis vs. Volumen |
| `histogram` | Verteilung | Preisverteilung |
| `heatmap` | Korrelation Matrix | Feature-Korrelationen |
| `pie` | Anteile | Marktanteile |

### Trading Charts
| Type | Use Case |
|------|----------|
| `candlestick` | OHLC Daten |
| `ohlc` | Open-High-Low-Close |
| `renko` | Trend-Analyse |

### Advanced
| Type | Use Case |
|------|----------|
| `dashboard` | Multi-Panel Overview |
| `subplot` | Mehrere Charts kombiniert |

## Options
| Option | Beschreibung |
|--------|--------------|
| `--x=<col>` | X-Achsen Spalte |
| `--y=<col>` | Y-Achsen Spalte |
| `--color=<col>` | Farbkodierung nach Spalte |
| `--title=<text>` | Chart-Titel |
| `--save=<path>` | Speichern als PNG/HTML |
| `--interactive` | Interaktiver Plotly Chart |
| `--indicators=<list>` | Trading-Indikatoren hinzufugen |

## Output
- Chart wird angezeigt
- Optional: Datei gespeichert
- Code zum Reproduzieren

## Agents Used
- **viz-specialist** - Chart-Erstellung
- **data-analyst** - Daten-Vorbereitung
