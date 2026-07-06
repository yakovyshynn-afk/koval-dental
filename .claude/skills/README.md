# Security review skills

A subset of the [Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills)
library (Apache-2.0), vendored here to support security review of this static
site (client-side form posting to Telegram, hardcoded bot token, GitHub Pages
hosting). See `.claude/CLAUDE.md` for the policy requiring these on every
review/audit/change, mapped to specific checks:

- `performing-security-headers-audit` — security headers validation
- `testing-for-sensitive-data-exposure` — JS security / secrets in responses
- `testing-for-xss-vulnerabilities` — JavaScript security review
- `testing-cors-misconfiguration` — static site security assessment
- `performing-clickjacking-attack-test` — static site security assessment
- `implementing-secret-scanning-with-gitleaks` — static site security assessment
- `implementing-api-key-security-controls` — static site security assessment
- `performing-web-application-vulnerability-triage` — OWASP Top 10 triage
- `testing-api-security-with-owasp-top-10` — OWASP Top 10 checks
- `performing-sca-dependency-scanning-with-snyk` — dependency vulnerability analysis
- `testing-for-broken-access-control` — authentication/session security review
- `performing-ssl-tls-security-assessment` — SSL/TLS best practices

Each skill directory retains its own Apache-2.0 `LICENSE`. See the upstream
repo for the full 817-skill library and framework mappings (MITRE ATT&CK,
NIST CSF, D3FEND, etc.).
