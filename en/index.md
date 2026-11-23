---
title: Sipdb guide
lang: en
---

Sipdb copies your production MySQL or MariaDB database to a local database
on your laptop, so you can develop and test with production-like data.

- **The server is only read.** Sipdb only uses an account that can read,
  and every statement is checked before it is sent.
- **After the first copy, only what is new or changed is read** (quick
  sync). An occasional full check catches the rest, including rows deleted
  on the server.
- **Your own local data is left alone.** Rows you add for testing are not
  deleted.

## Step by step

1. [Install Sipdb](install/)
2. [Make a read-only account on the server](read-only-account/)
3. [Make a connection profile](profile/)
4. [The first sync, quick syncs and the full check](sync/)
5. [Automatic schedule and notifications](schedule/)

## More

- [Using Sipdb from a terminal (CLI)](cli/)
- [Security: why the server cannot change](security/)
- [When something goes wrong](troubleshooting/)
- [Privacy policy](privacy/)

[Versi bahasa Indonesia](../id/)
