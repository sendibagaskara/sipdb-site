---
title: Install Sipdb
lang: en
---

## Windows

Install Sipdb from the **Microsoft Store**. The package is signed by
Microsoft, so there is no security warning, and the Store keeps Sipdb up to
date.

What gets installed:

- the **Sipdb** app in the Start menu;
- the **`sipdb`** command in a terminal (PowerShell or Command Prompt), for
  those who prefer the command line or schedule syncs with Task Scheduler.
  See [CLI](../cli/).

Windows 10 version 1809 or later, or Windows 11, is needed.

Sipdb also needs **MySQL or MariaDB on your laptop** as the local database
(for example from XAMPP, Laragon or the MySQL installer). That local
database is what Sipdb fills.

## macOS

The macOS version is on its way.

## Uninstall

Remove Sipdb in **Settings → Apps → Installed apps**.

- **Removed with it:** Sipdb's connection profiles, settings and log files,
  since they all live in the app's package folder.
- **Left in place:**
  - passwords in **Windows Credential Manager** (look for `sipdb` entries) —
    remove them yourself if you no longer need them;
  - your local database, including the `_sipdb` schema with Sipdb's sync
    records. Drop that schema if you no longer use Sipdb.

[Back to the guide](../)
