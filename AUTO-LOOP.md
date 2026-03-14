# Auto-Loop Guide

Universelle Anleitung für automatische Projekt-Arbeit mit Claude Code.

## Quick Start

```bash
cd /pfad/zum/projekt
claude -p "Lies TASKS.md und CLAUDE.md. Erledige die nächste offene Aufgabe. Markiere sie als [x] wenn fertig."
```

## Setup pro Projekt

### 1. TASKS.md erstellen

```markdown
# Projekt Tasks

## Offen
- [ ] Feature X implementieren
- [ ] Bug Y fixen
- [ ] Tests schreiben
- [ ] Dokumentation updaten

## In Arbeit

## Erledigt
```

### 2. Loop-Varianten

**Einmal-Durchlauf:**
```bash
claude -p "Lies TASKS.md. Erledige die nächste offene Aufgabe."
```

**5 Durchläufe:**
```bash
for i in {1..5}; do claude -p "Lies TASKS.md. Erledige die nächste offene Aufgabe."; sleep 5; done
```

**Endlos bis fertig:**
```bash
while true; do
  result=$(claude -p "Lies TASKS.md. Erledige die nächste offene Aufgabe. Sage FERTIG wenn alles erledigt.")
  echo "$result" | grep -q "FERTIG" && break
  sleep 5
done
```

## Projekt-spezifische Regeln

Wenn dein Projekt spezielle Regeln hat (wie Governance), füge sie in CLAUDE.md ein.
Der Loop-Prompt sollte dann sein:

```bash
claude -p "Lies TASKS.md UND CLAUDE.md. Beachte alle Regeln. Erledige die nächste Aufgabe."
```

## Beispiel TASKS.md Templates

### Trading Bot
```markdown
# Trading Bot Tasks
- [ ] Data consistency check: python shared/data_consistency.py
- [ ] Performance Report generieren
- [ ] Neue Strategie backtesten (KEIN Live-Trading!)
- [ ] Unit Tests erweitern
```

### Marketing Bot
```markdown
# Marketing Bot Tasks
- [ ] Content für nächste Woche planen
- [ ] Analytics auswerten
- [ ] A/B Test Ergebnisse analysieren
- [ ] Social Media Posts vorbereiten
```

### Polymarket Observer
```markdown
# Polymarket Tasks
- [ ] Neue Markets scannen
- [ ] Odds-Änderungen tracken
- [ ] Alert-Schwellen prüfen
- [ ] Report generieren
```

### Aktien/Stocks
```markdown
# Aktien Tasks
- [ ] Watchlist aktualisieren
- [ ] Earnings Calendar checken
- [ ] Technical Analysis für Top 5
- [ ] Portfolio Performance Report
```

## Windows-spezifisch

PowerShell:
```powershell
1..5 | ForEach-Object { claude -p "Lies TASKS.md. Erledige die nächste Aufgabe."; Start-Sleep 5 }
```

Git Bash (empfohlen):
```bash
for i in {1..5}; do claude -p "Lies TASKS.md. Erledige nächste Aufgabe."; sleep 5; done
```

## Tipps

1. **Klein anfangen** - Erst mit 1-2 Tasks testen
2. **CLAUDE.md pflegen** - Projekt-Regeln dort festhalten
3. **Logs speichern** - Output in Datei umleiten: `claude -p "..." > log.txt 2>&1`
4. **Nicht unbeaufsichtigt** - Bei neuen Projekten erstmal dabei bleiben
