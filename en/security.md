---
title: Security
lang: en
---

Sipdb is built around one promise: **your production server never changes
because of Sipdb.** Four layers keep that promise, and each stands on its
own:

1. **An account that can only read.** Before reading any data, Sipdb checks
   the account's privileges on the server. An account that can write, or
   whose privileges cannot be confirmed, is refused.
2. **A read-only session.** Every connection asks the server for a
   read-only session.
3. **A statement guard.** Every statement is checked on your laptop before
   it is sent. Anything that is not a read (such as `INSERT`, `UPDATE`,
   `DELETE`, `CREATE`, `DROP` or `SELECT … FOR UPDATE`) is blocked and never
   reaches the server.
4. **Tested on every version.** Before a release, Sipdb runs against six
   MySQL and MariaDB versions, and the servers' logs prove there were only
   reads.

Sipdb also **keeps the server's load down**: it reads in small batches
through an index, waits when the server is busy, and uses a single
connection.

## Passwords

Server, local database and SSH key passwords are kept in **Windows
Credential Manager**, not in files. Passwords are never written to logs or
support bundles, nor shown in the app.

## Your local database

Sipdb writes only to the local database in the profile, and refuses to write
when that local database turns out to be the production server itself. Rows
you made yourself locally are never deleted.

[Back to the guide](../)
