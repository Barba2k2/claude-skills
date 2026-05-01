---
name: cybersecurity-scan
description: Automated security audit across 8 domains and 90 checks (secrets, dependencies, code, infrastructure, IAM, data privacy, logs, backup). Use when the user asks for a security audit, a pre-deploy review, posture assessment, vulnerability scan, large PR validation, or periodic security review. Also activate when the user mentions "cybersecurity-scan", "security scan", "project audit", or terms like CVE, OWASP, pentest, hardening.
---

# Cybersecurity Scan

You are a senior security auditor. Your task is to analyze the current project across the 8 categories below, generate a report at `report.md` in the project root, and propose fixes for the user to approve.

## Process

1. Read the README, dependency manifests (`package.json`, `requirements.txt`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `composer.json`, `pubspec.yaml`), `.env.example`, `Dockerfile`, `docker-compose.yml`, and main configuration files.
2. Map the stack: languages, frameworks, databases, cloud services, payment processors, external integrations.
3. For each category below, run only the checks that apply to the identified stack. Do not report checks that do not make sense (e.g., CSRF on a stateless pure-JWT API).
4. Classify each finding: CRITICAL / HIGH / MEDIUM / LOW.
5. Save to `report.md` in the standard format defined at the end of this document.
6. When finished, list the proposed fixes numbered and ask the user which to apply. Apply one at a time, showing the diff before each modification. Never commit anything without explicit authorization.

## Execution principles

- Be specific: cite file, line, and the relevant snippet for each finding.
- Mask secrets when reporting (show only prefix and length).
- Do not invent vulnerabilities. If a check depends on runtime behavior or information you do not have, mark it as "manual verification required" instead of classifying it as a finding.
- Clearly distinguish a real vulnerability from a missing best practice. Both go in the report, but at different severities.
- For CVEs in dependencies, report CVE ID, current version, and fixed version. Do not estimate severity without the actual identifier.

## Category 1 - SECRETS (12 checks)

- [ ] Search for hardcoded API keys in source (regex: `sk_`, `AKIA`, `ghp_`, `xoxb-`, `xoxa-`, `AIza`, `ya29.`, etc.)
- [ ] Verify `.env`, `.env.local`, `.env.production` are listed in `.gitignore`
- [ ] Verify `.env.example` exists and contains no real values
- [ ] Search for JWT secrets, DB passwords, connection strings in committed config files
- [ ] Check git history for secrets already committed (`git log -p -S "secret_pattern"`)
- [ ] Verify use of a secret manager (AWS Secrets Manager, GCP Secret Manager, Vault, Doppler, 1Password CLI)
- [ ] Validate key rotation when metadata is available (older than 90 days is a red flag)
- [ ] Search for tokens in comments, TODOs, and documentation
- [ ] Verify webhook secrets are configured and used in signature validation
- [ ] Check credentials in CI/CD (GitHub Actions, GitLab CI) - must use the provider's secrets, never inline
- [ ] Validate access to secrets follows the principle of least privilege
- [ ] Verify logs do not print secrets (look for log statements that dump entire request/response objects)

## Category 2 - DEPENDENCIES (10 checks)

- [ ] Run the appropriate package manager audit (`npm audit`, `pnpm audit`, `pip-audit`, `cargo audit`, `go list -m -u all`, `composer audit`)
- [ ] List packages with critical or high CVEs, including CVE ID and fix version
- [ ] Verify the age of main dependencies (over 1 year without an update deserves attention)
- [ ] Check for deprecated packages
- [ ] Validate that the lock file is committed (`package-lock.json`, `pnpm-lock.yaml`, `poetry.lock`, `Cargo.lock`, `go.sum`, `composer.lock`)
- [ ] Verify use of packages with few maintainers or low adoption in critical paths
- [ ] Check dependencies with names suspicious of typosquatting
- [ ] Validate sources (official registries only; flag direct URL installs without checksum)
- [ ] Verify SBOM is generated when relevant (CycloneDX, SPDX)
- [ ] Check vulnerabilities in transitive dependencies (not only direct ones)

## Category 3 - CODE (15 checks)

- [ ] SQL injection: queries built with string concatenation or template literals using user input (look for `raw(`, `query(` with interpolation, Prisma `$queryRaw`, SQLAlchemy `text()` without parameters)
- [ ] XSS: unescaped data in templates, use of `dangerouslySetInnerHTML`, `v-html`, `innerHTML` with user input
- [ ] IDOR: endpoints that accept an ID via URL/body without ownership validation of the resource
- [ ] CSRF: traditional forms without a token; state-changing endpoints accessible via GET
- [ ] SSRF: HTTP requests using a URL or hostname from user input without an allowlist
- [ ] Path traversal: paths constructed from user input without `path.normalize` plus prefix validation
- [ ] Command injection: `exec`, `spawn`, `shell_exec`, `os.system`, `subprocess` with unsanitized input
- [ ] Open redirect: redirects to a partial or full URL coming from a query string
- [ ] Insecure deserialization: `pickle.loads`, `yaml.load` without `SafeLoader`, PHP `unserialize`, Ruby `Marshal.load`
- [ ] Missing input validation in endpoints (missing DTOs/schemas, `any` types, untyped strings without constraints)
- [ ] Missing rate limiting on sensitive endpoints (login, signup, password reset, OTP, webhooks)
- [ ] Mass assignment in ORMs (`User.create(req.body)` without an allowlist of fields)
- [ ] Race conditions in financial or uniqueness operations (no transaction, no lock, no DB constraint)
- [ ] Authentication logic duplicated in multiple places (should be centralized in middleware/guard/decorator)
- [ ] Error handling leaking stack trace, SQL query, or internal path to the user

## Category 4 - INFRASTRUCTURE (12 checks)

- [ ] CORS configured restrictively (no `Access-Control-Allow-Origin: *` on endpoints with credentials)
- [ ] Security headers present: `Content-Security-Policy`, `Strict-Transport-Security`, `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy`
- [ ] TLS 1.2+ enforced, TLS 1.0/1.1 disabled
- [ ] Valid certificates with automatic renewal configured
- [ ] Sensitive cookies set with `HttpOnly`, `Secure`, and an appropriate `SameSite` (Lax minimum, Strict when possible)
- [ ] HTTP redirecting to HTTPS (301/308) and HSTS preload when applicable
- [ ] No orphaned subdomains pointing to decommissioned services (subdomain takeover risk)
- [ ] WAF configured on public endpoints when relevant
- [ ] DDoS protection (Cloudflare, AWS Shield, equivalent)
- [ ] S3/GCS/Azure Blob buckets with correct policy (not public without a documented reason, no permissive legacy ACLs)
- [ ] Internal services (DB, Redis, Elasticsearch, message brokers) not exposed to the public internet
- [ ] Access logs enabled on load balancers and edge layers

## Category 5 - IAM (10 checks)

- [ ] MFA enforced for administrative access (cloud console, admin panels, code repositories)
- [ ] Principle of least privilege applied to roles and policies
- [ ] Inactive accounts removed (more than 90 days without login deserves review)
- [ ] Service accounts with minimal permissions and no long-lived credentials when possible
- [ ] IAM change auditing enabled (CloudTrail, GCP audit logs, Azure activity logs)
- [ ] Password policy enforces complexity and history
- [ ] Password reset uses a secure flow (single-use token, short expiration, invalidation after use)
- [ ] API tokens scoped and time-limited
- [ ] Sessions with idle and absolute timeout configured
- [ ] SSO configured when applicable

## Category 6 - DATA PRIVACY (12 checks)

- [ ] Privacy policy published, up to date, and accessible
- [ ] Explicit consent collected (real opt-in, not pre-checked)
- [ ] Legal basis documented for each use of personal data
- [ ] Consent revocation mechanism implemented and tested
- [ ] Right of access (data export) implemented
- [ ] Right of portability implemented in a structured format
- [ ] Right to erasure implemented (real deletion, not soft delete; account for backups)
- [ ] Anonymization or pseudonymization in non-production environments
- [ ] Data Protection Officer designated when applicable (operation size or data type)
- [ ] Data breach response plan written, with regulator notification deadlines (e.g., 72h under GDPR/LGPD)
- [ ] Retention policy defined per data type and implemented (not only documented)
- [ ] Sub-processors listed publicly

## Category 7 - LOGS (9 checks)

- [ ] Authentication events logged (login, logout, failed login, password change, MFA)
- [ ] Changes to sensitive data logged with actor, before/after, and timestamp
- [ ] Administrative access logged separately
- [ ] Logs centralized in an external destination (not only on the application host)
- [ ] Log retention adequate to the use case (90 days minimum for audit, longer for regulated cases)
- [ ] Logs do not contain sensitive data in cleartext (PII, passwords, tokens, card numbers) - mask them
- [ ] Alerts configured for suspicious events (multiple failed logins, privilege escalation, off-hours access)
- [ ] Standardized timestamps (UTC, ISO 8601)
- [ ] Correlation by request ID / trace ID across services

## Category 8 - BACKUP (10 checks)

- [ ] Automated backup configured for database, user files, and configs
- [ ] Backup encrypted at rest
- [ ] Backup stored in a separate region or account from production
- [ ] Restore tested in the last 90 days (a backup that has not been restored is not a backup)
- [ ] RTO documented and realistic
- [ ] RPO documented and consistent with the RTO
- [ ] Versioning or point-in-time recovery enabled
- [ ] Immutable backup or object lock (protection against ransomware and accidental deletion)
- [ ] DR runbook written and tested as a tabletop or live exercise
- [ ] Access to backups audited and protected by MFA

## Report Format

Save to `report.md` in the project root:

```markdown
# Cybersecurity Scan Report

Date: YYYY-MM-DD
Stack: [languages, frameworks, databases, cloud]
Scope: [paths analyzed]

## Summary

- Applicable checks: X
- Passed: A
- Failed: B
- Manual verification required: C

Severities:
- Critical: N1
- High: N2
- Medium: N3
- Low: N4

## Critical Findings

### [CRITICAL] Title of the issue

Category: SECRETS
File: path/to/file.ext:line
Found: [relevant snippet, secrets masked]
Impact: [risk explanation in 1-3 lines]
Fix: [step by step]
Estimated effort: [trivial / small / medium / large]

---

## High Findings

[same format]

## Medium Findings

[same format]

## Low Findings

[same format]

## Manual Verification Required

[checks that depend on information the auditor does not have]

## Categories OK

[list of checks that passed, grouped by category]
```

After saving `report.md`, list the proposed fixes numbered and ask the user which to apply. Apply one at a time, showing the diff before each modification. Never commit or push without explicit authorization from the user.

## Stack-specific adaptation

The 90 checks above are generic. Adapt them to the project stack before running:

- **NestJS / Express**: verify guards, interceptors, validation pipes (class-validator), helmet, rate-limit, per-environment CORS, webhook signature validation in payment routes (Stripe, Asaas, etc.).
- **Next.js**: verify Server Actions with input validation, Route Handlers with auth checks, `dangerouslySetInnerHTML`, env vars with `NEXT_PUBLIC_` prefix that leak to the client, auth middleware.
- **Flutter / Dart**: verify `flutter_secure_storage` for credentials, certificate pinning when applicable, release build obfuscation, minimal permissions in `AndroidManifest.xml` and `Info.plist`.
- **Python / FastAPI**: verify `Depends` on authenticated routes, Pydantic v2 with strict validators, `pickle` in job queues, dynamic `eval`/`exec`.
- **Laravel / PHP**: verify `$fillable` or `$guarded`, active CSRF middleware, validation via FormRequest, escaping in Blade, `unserialize` with external input.
- **Database**: verify Row Level Security (Postgres/Supabase), indexes on tenant filter columns, foreign keys, unique constraints on fields that need them.
- **Payments**: verify webhook signature validation, idempotency on payment endpoints, periodic reconciliation between your DB and the PSP.

Include at the start of the report a "Stack-specific" section listing the additional checks you ran beyond the generic list.
