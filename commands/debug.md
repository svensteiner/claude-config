# Systematic Debugging

Du verwendest jetzt das **4-Phasen Systematic Debugging Framework**.

**KERNREGEL: Niemals direkt Fixes versuchen - IMMER erst Root Cause finden!**

---

## Phase 1: Root Cause Investigation (PFLICHT)

Bevor du IRGENDETWAS fixst:

1. **Symptom dokumentieren**: Was genau passiert?
2. **Reproduktion**: Wie kann das Problem reproduziert werden?
3. **Logs analysieren**: Alle relevanten Logs und Stack-Traces sammeln
4. **Ursprung zurückverfolgen**: Den Bug bis zur Quelle verfolgen
5. **Hypothese aufstellen**: Was ist die wahrscheinlichste Root Cause?

**Output**: Klare Root-Cause-Hypothese mit Beweisen

---

## Phase 2: Pattern Analysis

1. **Ähnliche Issues**: Gibt es ähnliche Probleme im Codebase?
2. **Verwandte Stellen**: Könnte das Problem an mehreren Stellen auftreten?
3. **Gemeinsame Ursachen**: Gibt es ein systemisches Problem dahinter?

**Output**: Liste aller betroffenen Stellen

---

## Phase 3: Fix Development

**NUR nach Abschluss von Phase 1+2!**

1. Fix adressiert die **Root Cause**, nicht das Symptom
2. Defense-in-Depth: Mehrere Schutzschichten wo sinnvoll
3. Condition-based statt Time-based: Auf Bedingungen warten, nicht auf Zeit

---

## Phase 4: Verification

1. Fix testen - Problem ist behoben
2. Regression-Check - Keine neuen Bugs eingeführt
3. Ähnliche Stellen prüfen - Gleiches Problem dort auch gefixt?

---

## Regeln

| Regel | Beschreibung |
|-------|--------------|
| **Ohne Phase 1 keine Fixes** | Keine Fix-Vorschläge ohne Root Cause Investigation |
| **3+ fehlgeschlagene Fixes** | Architektur hinterfragen, tiefer analysieren |
| **Condition-based Waiting** | Nicht auf Timing verlassen |

---

## Jetzt starten

Beschreibe das Problem das du debuggen möchtest:
- Was ist das **Symptom**?
- Wann tritt es auf?
- Gibt es **Fehlermeldungen** oder **Logs**?

Ich werde dann systematisch durch alle 4 Phasen gehen.
