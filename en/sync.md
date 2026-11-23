---
title: Syncing and the full check
lang: en
---

## The first sync

On the **Dashboard**, press **Sync now**. Sipdb copies tables, views,
routines and triggers (see below) from the server to the local database,
a little at a time so the server is not loaded.

Before it writes anything, Sipdb may ask:

- **A local table already holds data** (an old manual dump, say): treat it
  as a copy of the server, or as your own data that is never touched.
- **Local triggers are not wrapped yet:** wrap them so they do not fire
  while Sipdb writes, but still fire for your app.
- **A column changed on the server** in a way that may change local values:
  change the local column, or skip that table for now.

A sync can be stopped at any time (**Stop** or **Pause**). The next sync
continues where it stopped.

## Quick sync

After the first sync, every sync reads only the rows that are **new or
changed** on the server, through an index. It usually takes seconds.

- **Your local edits are safe** as long as the server does not change the
  same row. If it does, the server's version wins, and History records the
  overwritten edit.
- **What a quick sync does not catch:** rows deleted on the server, and
  tables without an indexed time column. That is the full check's job.

## The full check

**Full check** compares every table with the server block by block and
repairs what differs, including deleting rows the server deleted.

- Rows you made yourself locally are **never deleted**.
- A full check is heavier for the server. Run it when the server is quiet,
  or schedule it at night (see [schedule](../schedule/)).
- It has a time limit per run; tables not finished continue at the next
  check.

## Triggers

A read-only account cannot read the server's triggers. If your server has
triggers, export their definitions with an admin account in your own tool,
then import them on the **Objects** page → **Import triggers**. Sipdb shows
the right `mysqldump` command.

[Back to the guide](../)
