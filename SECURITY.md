# Security

## Reporting a vulnerability

Please do not report security vulnerabilities in public issues. Report them privately through GitHub's private vulnerability reporting: **https://github.com/civicpro/civicpro/security/advisories/new**. Reports are visible only to the project maintainers.

Please include the affected version, steps to reproduce, and the impact. We aim to give a first response within 7 days.

## Scope

Findings in these areas are especially important:

- Access to one company's data with another company's permissions
- An encrypted database, attachment or backup left unprotected
- The audit log being altered without a trace
- Writing to a locked period, or deleting journal entries
- Requests to the local service from another website (CSRF, Origin, DNS rebinding)
- Privilege escalation, session hijacking, or bypassing the second approval
- Installing an unsigned update or country pack

## Design principles

- By default the service listens only on 127.0.0.1. Local network access is a separately enabled mode that works only over HTTPS. Exposing the service to the internet is not supported.
- There is no telemetry. Outbound requests are made only for update checks, country pack updates, and error reports the user chooses to send; packages are signature-verified.
- Passwords are hashed with Argon2id; 2FA and sign-in with Microsoft/Google are supported. On a single-computer installation the database is encrypted with SQLCipher.
- Backups are encrypted; the backup password is separate from the sign-in password.
