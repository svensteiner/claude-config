# /multi-agents:analyze

## Description
Tiefgehende Codebase-Analyse mit mehreren Perspektiven.

## Usage
```
/multi-agents:analyze [scope] [focus]
```

## Parameters
- `scope` - Was analysiert werden soll (file, module, codebase)
- `focus` - Analyse-Fokus (architecture, patterns, quality, security)

## Behavior
1. code-explorer scannt Struktur
2. Spezialist analysiert je nach Fokus
3. Ergebnisse werden konsolidiert

## Examples

### Architecture Analysis
```
/multi-agents:analyze codebase architecture

Analysiere:
- Modul-Struktur
- Dependency-Graph
- Layer-Separation
- Design Patterns
```

### Quality Analysis
```
/multi-agents:analyze src/services quality

Fokus:
- Code Complexity
- Test Coverage
- Technical Debt
- Best Practices
```

### Security Analysis
```
/multi-agents:analyze . security

Prufe:
- OWASP Top 10
- Dependencies
- Secrets
- Auth/AuthZ
```

## Output Format
```markdown
## Analysis Report: [Scope]

### Executive Summary
[1-2 Satze Gesamtbild]

### Findings

#### Strengths
- [Positiv 1]
- [Positiv 2]

#### Issues
| Priority | Finding | Location | Recommendation |
|----------|---------|----------|----------------|

### Metrics
[Quantitative Daten]

### Recommendations
[Priorisierte nachste Schritte]
```

## Agent Mapping
| Focus | Primary Agent | Support |
|-------|---------------|---------|
| architecture | code-architect | code-explorer |
| patterns | code-explorer | code-architect |
| quality | quality-guardian | code-explorer |
| security | security-sentinel | code-explorer |
