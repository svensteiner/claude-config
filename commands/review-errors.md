# Error Handling Review

Prüfe die Fehlerbehandlung und finde Silent Failures.

## Anweisungen

1. Prüfe mit `git diff` welche Dateien geändert wurden
2. Nutze den `pr-review-toolkit:silent-failure-hunter` Agent um zu prüfen:
   - Catch-Blöcke die Fehler verschlucken
   - Fehlende Error-Handling
   - Unzureichendes Logging
   - Fallback-Verhalten das Probleme maskiert

3. Liste alle gefundenen Silent Failures mit Schweregrad
