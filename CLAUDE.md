- hat der bot also gelernt
- You are implementing a GOVERNED PROPOSAL NOTIFICATION AND REVIEW SYSTEM
for a trading bot with strict human-in-the-loop rules.

CONTEXT:
- Multiple agents (auto-trainer, optimizer, learning engine) write proposal JSON files
- Live trading components MUST NOT read proposals
- Humans must be notified and review proposals OUTSIDE the running system

ABSOLUTE RULES:
- Telegram is INFORMATION ONLY (no approve/deny buttons)
- No live parameter changes
- Proposal application requires bot shutdown + restart
- No agent may apply or request approval directly

TASKS:

1. PROPOSAL NOTIFIER
   - Implement a small service/script that:
     - Watches /proposals/** for new proposal_*.json files
     - Tracks already-notified proposal IDs (local state file)
     - Sends a Telegram message ONCE per new proposal
   - Telegram message must include:
     - source
     - parameter + proposed change
     - short reason
     - proposal_id
     - explicit text: "Human review required"

2. REVIEW COCKPIT (LOCAL)
   - Implement a local CLI-based review tool:
     - Command: python review_proposals.py
     - Lists all OPEN proposals
     - Displays full details (reason, risk, metrics)
     - Read-only (no apply here)

3. APPLY SCRIPT (EXPLICIT HUMAN ACTION)
   - Implement python apply_proposal.py <proposal_id>
   - Preconditions:
     - Trading bot processes are NOT running
   - Actions:
     - Update strategy_config.json with proposed value
     - Mark proposal as APPROVED with timestamp and operator
     - Archive proposal to /proposals/approved/
   - Print clear instruction:
     "Restart bot to activate changes (new session required)"

4. SAFETY GUARDS
   - Ensure:
     - Live components cannot import or read proposal files
     - apply_proposal.py hard-fails if bot is running
   - Add clear comments explaining governance intent

DELIVERABLES:
- Proposal notifier code
- review_proposals.py
- apply_proposal.py
- Example Telegram message
- Short explanation of the governance flow

If any step risks live self-modification, STOP and flag it.
- state wieder den bot im hintergrund und checke das auch wirklich alle bots starten
- Das heisst sind wir bereit einen dienstplan für februar zu erstellen

---

# Code Review Quick Reference

## Verfügbare Review-Commands (global)

| Command | Beschreibung |
|---------|--------------|
| `/review` | Schneller Code-Review (5 parallele Agenten) |
| `/review-full` | Vollständiger PR-Review mit allen Aspekten |
| `/review-tests` | Test-Coverage analysieren |
| `/review-errors` | Fehlerbehandlung & Silent Failures prüfen |
| `/review-types` | Typen-Design analysieren |
| `/review-simplify` | Code-Vereinfachungspotenzial finden |

## Review-Agenten Übersicht

### /review (5 parallele Agenten)
- CLAUDE.md Compliance
- Bug Detection
- Historical Context
- PR History Analysis
- Code Comments Quality

### /review-full (6 spezialisierte Agenten)
- comment-analyzer: Kommentar-Qualität
- pr-test-analyzer: Test-Abdeckung
- silent-failure-hunter: Versteckte Fehler
- type-design-analyzer: Typen-Design
- code-reviewer: Code-Qualität
- code-simplifier: Vereinfachung

## Security-Guidance (automatisch aktiv)
Warnt bei: Command Injection, XSS, eval(), SQL Injection, Hardcoded Secrets, unsichere Crypto

## Best Practice Workflow
1. Code schreiben
2. `/review` ausführen
3. Issues beheben
4. `/review-tests` für Test-Check
5. `/commit` für sauberen Commit

---

# Global Skills Library

**Pfad:** `C:\Chatgpt_Codex\_skills\`

## Alle verfügbaren Commands

### Code Review
| Command | Beschreibung |
|---------|--------------|
| `/code-review` | 5-Agenten Code-Review |
| `/pr-review-toolkit:review-pr` | Vollständiger PR-Review |
| `/pr-review-toolkit:review-pr tests` | Nur Test-Coverage |
| `/pr-review-toolkit:review-pr errors` | Nur Fehlerbehandlung |
| `/pr-review-toolkit:review-pr types` | Nur Typen-Design |
| `/pr-review-toolkit:review-pr simplify` | Code vereinfachen |

### Git & Commits
| Command | Beschreibung |
|---------|--------------|
| `/commit` | Git Commit erstellen |
| `/commit-push-pr` | Commit + Push + PR |
| `/clean_gone` | Gelöschte Branches aufräumen |

### Feature Development
| Command | Beschreibung |
|---------|--------------|
| `/feature-dev` | 7-Phasen Feature-Entwicklung |
| `/superpowers:brainstorm` | Ideen sammeln |
| `/superpowers:write-plan` | Plan schreiben |
| `/superpowers:execute-plan` | Plan ausführen |

### Multi-Agents (wshobson/agents)
| Command | Beschreibung |
|---------|--------------|
| `/multi-agents:orchestrate` | Multi-Agent Task koordinieren |
| `/multi-agents:analyze` | Codebase analysieren |
| `/multi-agents:audit` | Security Audit |

### Data Pipeline
| Command | Beschreibung |
|---------|--------------|
| `/data-pipeline:analyze` | Daten analysieren, Insights finden |
| `/data-pipeline:transform` | ETL-Pipeline ausführen |
| `/data-pipeline:visualize` | Charts erstellen |
| `/data-pipeline:validate` | Datenqualität prüfen |

### Frontend & Design
| Command | Beschreibung |
|---------|--------------|
| `/skill frontend-design:frontend-design` | UI/Frontend erstellen |

### Dokumente
| Skill | Beschreibung |
|-------|--------------|
| `docx` | Word-Dokumente |
| `xlsx` | Excel-Tabellen |
| `pptx` | PowerPoint |
| `pdf` | PDF-Dateien |

## Kurzreferenz

```
REVIEW:    /code-review, /pr-review-toolkit:review-pr
GIT:       /commit, /commit-push-pr
FEATURE:   /feature-dev, /superpowers:*
AGENTS:    /multi-agents:orchestrate|analyze|audit
DATA:      /data-pipeline:analyze|transform|visualize|validate
FRONTEND:  /skill frontend-design:frontend-design
```

## Nach Anwendungsfall

| Ich will... | Befehl |
|-------------|--------|
| Code prüfen | `/code-review` oder `/pr-review-toolkit:review-pr` |
| Committen | `/commit` oder `/commit-push-pr` |
| Feature bauen | `/feature-dev` oder `/multi-agents:orchestrate` |
| Security checken | `/multi-agents:audit --deep` |
| UI bauen | `/skill frontend-design:frontend-design` |
| Daten analysieren | `/data-pipeline:analyze data.csv` |
| Daten transformieren | `/data-pipeline:transform raw.csv clean.csv` |
| Charts erstellen | `/data-pipeline:visualize data.csv candlestick` |
| Planen | `/superpowers:brainstorm` → `/superpowers:write-plan` |

## Automatisch Aktiv
- **security-guidance** - Warnt bei Sicherheitslücken
- **frontend-design** - Aktiviert bei UI-Tasks

## Skills-Dokumentation
Vollständige Dokumentation: `C:\Chatgpt_Codex\_skills\CHEATSHEET.md`
- thomas kuhn kommt raus, vero ist ärzting
- mach das alles
- ja
- eine session dauer 6 Stunden
- You are acting as a release engineer adding non-negotiable governance gates.

Goal:
Create a hard release gate that prevents deployment/merge if any evidence exists of:

a RETWEET action executed in any cycle

more than one posting action attempted per cycle

SOURCE_BOUND content posted as STANDALONE

missing audit records

Context:
We now have:

core/posting_cycle_executor.py emitting audit JSONL records

tests/e2e/test_live_mode_invariants.py validating invariants

production_sim_runner producing traces

Non-negotiable constraints:

Deterministic

No network access

No changes to posting semantics

Gates must work in CI and locally

Tasks:

Implement an audit log validator:

Input: posting_audit.jsonl (or configured path)

Parse JSONL deterministically

Validate:
a) Each cycle_id appears exactly once
b) attempted_actions length <= 1
c) If source_tweet_id != null then final_action must be QUOTE or DROP only
d) RETWEET must never appear as attempted_action or final_action
e) Missing required fields => FAIL wi
- ````text
You are Claude Code. Task: introduce a strict, fail-closed EngineConfig + ConfigLoader layer that guarantees customer configs (rules, staff, absences, hours) are valid, normalized, and complete before entering the engine.

GOAL
Ensure the engine (Scheduler, RuleEngine, Governance) can ONLY run with a fully validated EngineConfig.
Raw customer configs must never reach engine internals.

SCOPE
Minimal, production-ready implementation.
No feature work. No behavior change beyond earlier validation failures.

TARGET ARCHITECTURE

Raw Customer Config (dict / json)
        ↓
ConfigLoader (single entry point)
        ↓
Schema + semantic validation
        ↓
Normalization
        ↓
EngineConfig (immutable)
        ↓
Scheduler / RuleEngine / Governance

If ANY step fails → raise ConfigError and abort (fail-closed).

---

PART 1 — Define EngineConfig (mandatory boundary object)

Create: engine/config/engine_config.py

Requirements:
- Use dataclass (frozen=True)
- Explicit fields only (no **kwargs)

Structure (adjust types to existing models):

```python
@dataclass(frozen=True)
class EngineConfig:
    staff: Dict[str, Staff]                  # normalized staff objects
    absences: AbsencesDict                   # Dict[str, List[NormalizedAbsence]]
    rules: ValidatedConfig                   # already validated rules
    planning_horizon: DateRange              # start/end
    workload: Dict[str, NormalizedWorkload]  # per staff_id
    metadata: ConfigMetadata                 # version, hash, source, timestamps
````

Notes:

* No raw dicts inside EngineConfig
* Everything inside must already be normalized + validated

---

PART 2 — ConfigLoader (single ingress)

Create: engine/config/loader.py

Public API (ONLY):

```python
def load_engine_config(raw_config: dict) -> EngineConfig
```

Responsibilities (in this exact order):

1. Basic structure validation

* raw_config must be dict
* required top-level keys:

  * "staff"
  * "rules"
  * "planning_horizon"
* absences / workload optional but validated if present
* else: raise ConfigError("Missing required config field: …")

2. Planning horizon

* Parse start/end
* Validate start < end
* Normalize to DateRange

3. Staff normalization

* Accept list or dict
* Enforce:

  * staff_id (string, unique)
  * role
* Normalize to Dict[str, Staff]
* No defaults hidden in engine

4. Absences

* Use existing normalize_absences()
* Reject absences with unknown staff_id

5. Workload / hours

* Normalize contract / weekly hours
* Define ONE internal format (NormalizedWorkload)
* If missing:

  * either explicit documented default
  * or ConfigError (choose conservative fail-closed)

6. Rules

* Raw rules → existing validation pipeline
* Produce ValidatedConfig
* Reject invalid rules early (no silent drop)

7. Metadata

* Compute config_hash (stable hash of raw_config)
* Include:

  * version (if provided, else "unknown")
  * loaded_at (UTC)
  * source ("customer")

Return EngineConfig.

---

PART 3 — Wire engine to EngineConfig ONLY

Changes required:

* Scheduler.**init** must accept EngineConfig, NOT raw pieces
* RuleEngine.**init** same
* Remove / block alternative constructors

Example:

```python
Scheduler(engine_config: EngineConfig)
```

If someone tries to pass raw dicts → TypeError.

---

PART 4 — Governance integration

Extend GovernanceRunReport to include:

* config_hash
* config_version
* staff_count
* absence_count
* rule_count

Values must come from EngineConfig, not raw inputs.

---

PART 5 — Errors & messaging

Create:
engine/config/errors.py

Define:

```python
class ConfigError(RuntimeError):
    pass
```

All customer-facing config failures must raise ConfigError with:

* exact field name
* reason
  No stack-trace leaking into customer output.

---

PART 6 — Tests (minimal, critical)

Add tests in tests/test_config_loader.py

Must cover:

1. Happy path: minimal valid config → EngineConfig
2. Missing required field → ConfigError
3. Absence with unknown staff_id → ConfigError
4. Invalid rule → ConfigError
5. Engine rejects raw config (Scheduler(raw_dict) raises)

Do NOT add more than necessary.

---

CONSTRAINTS

* No scheduling logic changes
* No relaxation of governance
* No silent defaults unless explicitly documented
* Keep changes localized to config + init boundaries

---

IMPLEMENTATION ORDER (MANDATORY)

1. Create EngineConfig
2. Implement ConfigError
3. Implement ConfigLoader
4. Wire Scheduler / RuleEngine
5. Update governance report
6. Add tests
7. Run full pytest suite

---

DELIVERABLE

* Engine only runs with EngineConfig
* Clear failure when customer config is invalid
* Full test suite remains green

NOW START.
Inspect repository structure and begin with PART 1.

```

Das ist der Schritt, der aus deiner Engine **ein belastbares Kundensystem** macht.  
Ab hier gibt es keinen „Zufallseingang“ mehr – nur noch Verträge.
```