---
title: Automatic schedule and notifications
lang: en
---

On the **Schedule** page:

- a **quick sync** every 15 minutes, 30 minutes, 1 hour or 4 hours;
- a **full check** once a night in the window you choose (01:00–05:00 by
  default), with a time limit per run.

Press **Save schedule**. The first quick sync runs one interval later;
opening the app does not contact the server right away.

## Tray

While a schedule is on, closing the window **hides Sipdb in the tray** (the
icons at the bottom right) and the schedule keeps running. From that icon's
menu you can open Sipdb, sync now, pause, stop, or quit.

The schedule only runs while Sipdb is open or in the tray. If the laptop was
off during the full-check window, the Dashboard reminds you and offers
**Check now**.

## Automatic syncs never ask

When an automatic sync needs an answer (a local table that already holds
data, a new SSH host key), it stops without writing anything. Open Sipdb and
press **Sync now** to answer.

## Notifications

Sipdb shows a Windows notification when:

- an automatic sync fails;
- an automatic sync needs your answer;
- a full-check window passes without a full check.

Each event is notified once, not every interval. Switch them off with the
**System notifications for automatic syncs** box on the Schedule page.

## Syncing from Task Scheduler

To sync even when the app is not open, schedule the `sipdb` command in
Windows Task Scheduler. See [CLI](../cli/).

[Back to the guide](../)
