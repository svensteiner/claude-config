# /multi-agents:audit

## Description
Vollstandiges Security-Audit der Codebase.

## Usage
```
/multi-agents:audit [scope] [--deep]
```

## Parameters
- `scope` - Zu prufender Bereich (default: entire codebase)
- `--deep` - Tiefgehende Analyse inkl. Code-Path-Tracing

## Behavior
1. security-sentinel fuhrt Surface Scan durch
2. Bei --deep: code-explorer tracet vulnerable Paths
3. Findings werden priorisiert
4. Remediation-Plan wird erstellt

## Examples

### Quick Audit
```
/multi-agents:audit

-> OWASP Top 10 Check
-> Dependency Scan
-> Secret Detection
```

### Deep Audit
```
/multi-agents:audit --deep

-> Alles aus Quick Audit
-> Code Path Analysis
-> Attack Vector Mapping
-> Business Logic Review
```

### Scoped Audit
```
/multi-agents:audit src/auth --deep

-> Fokus auf Authentication
-> Token Handling
-> Session Management
-> Access Control
```

## Output Format
```markdown
## Security Audit Report

### Risk Level: [CRITICAL/HIGH/MEDIUM/LOW]

### Executive Summary
[Gesamtbild in 2-3 Satzen]

### Critical Findings
[Sofort zu beheben]

### High Priority
[Innerhalb 24h]

### Medium Priority
[Innerhalb 1 Woche]

### Low Priority
[Nachstes Release]

### Dependency Report
[CVE-Liste mit Fixes]

### Remediation Roadmap
[Priorisierte Schritte]
```

## Compliance Tags
Findings werden automatisch getaggt:
- `GDPR` - Datenschutz-relevant
- `PCI` - Payment-relevant
- `SOC2` - Security Controls
- `HIPAA` - Healthcare-relevant
