Run a comprehensive security audit on the codebase.

Usage: /security-audit [scope] [--deep]

## Checks
### OWASP Top 10
- SQL Injection
- XSS (Cross-Site Scripting)
- Command Injection
- Path Traversal
- Insecure Deserialization

### Authentication
- Password storage
- Session management
- Token validation

### Data Protection
- Sensitive data encryption
- Secure transmission
- Secret detection

### Dependencies
- Known vulnerabilities (CVE)
- Outdated packages

## Severity Levels
- CRITICAL: Immediate fix required
- HIGH: Fix within 24h
- MEDIUM: Fix within 1 week
- LOW: Next release

## Output
- Executive summary
- Findings by severity
- Remediation recommendations

Reference: C:\Chatgpt_Codex\_skills\multi-agents\workflows\security-audit.md
