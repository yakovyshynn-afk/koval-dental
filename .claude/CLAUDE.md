# Security policy for this project

This repo is a static landing page (`index.html`, inline JS, a client-side
form that POSTs to the Telegram Bot API with a token embedded in the page
source) published via GitHub Pages. Treat every code review, audit, or
change to `index.html`, `assets/`, or any future scripts as a security
review, not just a functional one.

## Mandatory: use the vendored skills

`.claude/skills/` contains a scoped subset of the
[Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills)
library. Before finishing any review, audit, or non-trivial change, walk the
checklist below and invoke the matching skill(s) rather than reasoning about
security ad hoc.

| Requirement | Skill(s) to apply |
|---|---|
| OWASP Top 10 checks | `testing-api-security-with-owasp-top-10`, `performing-web-application-vulnerability-triage` |
| Security headers validation | `performing-security-headers-audit` (CSP, HSTS, X-Frame-Options, cookie flags) |
| Dependency vulnerability analysis | `performing-sca-dependency-scanning-with-snyk` |
| JavaScript security review | `testing-for-xss-vulnerabilities`, `testing-for-sensitive-data-exposure` |
| Authentication / session security review | `testing-for-broken-access-control` |
| SSL/TLS best practices | `performing-ssl-tls-security-assessment` |
| Static website security assessment | `performing-clickjacking-attack-test`, `testing-cors-misconfiguration`, `implementing-secret-scanning-with-gitleaks`, `implementing-api-key-security-controls` |

Apply the ones relevant to the diff at hand — e.g. a copy/content-only change
still warrants the secret-scanning and XSS checks if it touches
`index.html`; a change to the Telegram form warrants the CORS, sensitive-data
and API-key skills.

## Standing finding to re-check every time

The Telegram bot token and chat ID are hardcoded in the page's JavaScript
(flagged in this repo's `README.md`). Every review must re-flag this under
`testing-for-sensitive-data-exposure` / `implementing-api-key-security-controls`
until it is moved server-side or replaced with a scoped, rotatable
credential — do not let it go unmentioned just because it's pre-existing.

## Adding skills

If a review needs a skill not yet vendored, pull it from the upstream repo
into `.claude/skills/<skill-name>/` (keep its `LICENSE`) rather than
reasoning without one, and add it to the table above.
