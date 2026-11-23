---
title: Using Sipdb from a terminal
lang: en
---

Sipdb from the Microsoft Store also installs the **`sipdb`** command. Open a
new PowerShell or Command Prompt and run:

```
sipdb version
```

Profiles, passwords and history are shared with the app: a profile made in
the app works in the terminal right away, and the other way round.

## Main commands

| Command | What it does |
|---|---|
| `sipdb init` | Make a connection profile (asks one thing at a time) |
| `sipdb check --profile prod` | Test the connection, check the account, show the strategy per table |
| `sipdb pull --profile prod` | The first sync, then quick syncs |
| `sipdb verify --profile prod --max-time 30m` | Full check, stopping cleanly after 30 minutes |
| `sipdb status --profile prod` | The status of every table, without contacting the server |
| `sipdb log --profile prod` | Sync history, without contacting the server |
| `sipdb support-bundle` | Make a zip to report a problem (see [troubleshooting](../troubleshooting/)) |

`sipdb <command> --help` shows every option.

## Exit codes

| Code | Meaning |
|---|---|
| 0 | Done, every table ok |
| 1 | A table failed, the run was stopped, or the run could not start |
| 2 | The server account was refused because it can write |
| 3 | The local database is being synced by another Sipdb process; nothing was sent to the server |

## Task Scheduler

1. Open **Task Scheduler** → **Create Basic Task**.
2. Choose the schedule, for example daily, repeating every 30 minutes.
3. Action **Start a program**:
   - Program: `%LOCALAPPDATA%\Microsoft\WindowsApps\sipdb.exe`
   - Arguments: `pull --profile prod`
4. For a nightly full check, make a second task with the arguments
   `verify --profile prod --max-time 3h`.

Task Scheduler's **Last Run Result** column shows the exit code above
(`0x0` = success). When the app is syncing the same local database, the
task exits with code 3 and tries again at its next time.

## Language

`sipdb` follows the language chosen in the app. To force one, set the
`SIPDB_LANG` variable to `en` or `id`.

[Back to the guide](../)
