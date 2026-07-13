# Security Policy

This policy applies to every repository in the
[tabnas](https://github.com/tabnas) organization.

## Reporting a vulnerability

**Please do not open a public issue for security problems.**

Report vulnerabilities privately, either:

1. **Preferred:** via GitHub's private vulnerability reporting — use
   *"Report a vulnerability"* under the **Security** tab of the affected
   repository; or
2. by email to **richard@ricebridge.com** with a subject line beginning
   `[SECURITY]`.

Please include:

- the affected package(s) and version(s), and whether the TypeScript
  (`@tabnas/*`) or Go (`github.com/tabnas/*/go`) implementation is affected
  (or both);
- a description of the issue and its impact;
- a proof of concept or reproduction steps if possible.

## What to expect

- **Acknowledgement** within 72 hours.
- An initial **assessment** within 7 days.
- We aim to release a fix within **90 days** of the report, and will
  coordinate a disclosure date with you. Credit is given to reporters unless
  they prefer to remain anonymous.

## Supported versions

Parsers are a common attack surface — treat untrusted input with care and keep
packages current. Security fixes are applied to the **latest release** of each
package. Older versions do not receive fixes.

## Scope notes

- Vulnerabilities in third-party dependencies should be reported upstream,
  but do tell us if a Tabnas package is exploitable through one.
- Crashes or hangs on malformed input in a parser (denial of service via
  pathological documents) are in scope.
