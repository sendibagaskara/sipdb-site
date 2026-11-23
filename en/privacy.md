---
title: Privacy policy
lang: en
---

In effect since 23 November 2026.

**Sipdb does not send data to us or to anyone else.** There is no Sipdb
account, no telemetry, no usage statistics, no crash reports and no ads.

## Who Sipdb contacts

Only what you set in a profile:

- your production database server (read only);
- the SSH server, if you use SSH;
- the local database on your laptop.

Sipdb does not check for updates itself; the Microsoft Store does that. The
Help and Privacy links open in your browser.

## What is kept on your laptop

| What | Where |
|---|---|
| Connection profiles (host, port, user, database name, schedule) | Sipdb's app data folder |
| Passwords and SSH key passphrases | Windows Credential Manager |
| Sync logs: table names, row counts and error messages, no passwords. A database error message can quote data values (such as `Duplicate entry '…'`) | Sipdb's app data folder; files rotate at 5 MB, at most six files per log (one log for the app, one for the CLI) |
| The data copy and sync records (the `_sipdb` schema) | Your local database |

All of it stays on your laptop. Uninstalling Sipdb removes the profiles,
settings and logs; passwords in Credential Manager and your local database
are not removed (see [install](../install/)).

## Support bundle

A support bundle is only made when you ask for it, and only sent if **you**
send it. It holds the logs, profiles without passwords, table status and run
history; no row contents. Check it before sending, since error messages from
the database can contain data values. Bundles we receive are only used to
help you and are deleted once the problem is solved.

## Contact

Privacy questions: {{ site.support_email }}.

[Back to the guide](../)
