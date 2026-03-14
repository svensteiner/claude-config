# Vollständiger PR Review

Führe einen umfassenden Review mit allen verfügbaren Agenten durch.

## Anweisungen

1. Prüfe mit `git diff` welche Dateien geändert wurden
2. Nutze `/pr-review-toolkit:review-pr all` für den vollständigen Review mit allen 6 spezialisierten Agenten:
   - comment-analyzer: Kommentar-Qualität
   - pr-test-analyzer: Test-Abdeckung
   - silent-failure-hunter: Versteckte Fehler
   - type-design-analyzer: Typen-Design
   - code-reviewer: Code-Qualität
   - code-simplifier: Vereinfachung

3. Erstelle einen strukturierten Report mit allen Findings
