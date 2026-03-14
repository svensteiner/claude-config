# Projekt-Erinnerung Setup

Template für projekt-spezifisches Lernen. Claude merkt sich Patterns pro Projekt.

## Quick Setup (Copy & Paste)

```bash
# 1. In dein Projekt wechseln
cd /pfad/zu/deinem/projekt

# 2. .claude Ordner erstellen
mkdir -p .claude

# 3. Settings erstellen
cat > .claude/settings.json << 'SETTINGS'
{
  "learning": {
    "enabled": true,
    "scope": "project"
  }
}
SETTINGS

# 4. Learnings-Datei erstellen
cat > .claude/LEARNINGS.md << 'LEARNINGS'
# Projekt - Gelernte Patterns

> Claude speichert hier was er über dieses Projekt lernt.
> Projekt-isoliert - beeinflusst keine anderen Projekte.

## Projekt-Regeln
<!-- Aus CLAUDE.md übernommen -->

## Gelöste Fehler
<!-- Claude fügt automatisch hinzu -->

## User-Korrekturen  
<!-- Wenn du sagst "Nein, mach es SO" -->

## Code-Patterns
<!-- Wiederkehrende Muster -->

LEARNINGS

echo "✅ Setup fertig!"
```

## Projekt-spezifische Templates

### Trading Bot
```bash
cat > .claude/LEARNINGS.md << 'EOF'
# Trading Bot - Gelernte Patterns

## Governance
- KEINE automatischen Parameter-Änderungen
- Proposals brauchen Human Review
- Bot-Restart nach Config-Änderungen

## Data
- trading_bot.db = Single Source of Truth
- paper_trades.json = nur Cache

## Gelöste Fehler

## User-Korrekturen
