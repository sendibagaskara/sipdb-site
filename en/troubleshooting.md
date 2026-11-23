---
title: When something goes wrong
lang: en
---

## The account is refused

"Account … REFUSED" means the server account can write, or its privileges
cannot be confirmed. Make a read-only account (see
[read-only account](../read-only-account/)). Test connection on the
Connection page shows the privileges at fault.

## Cannot connect to the server

- Check the host and port, and whether your laptop may reach the server
  (firewall, VPN, allowed IPs).
- When the connection drops during a sync, Sipdb tries again three times
  (after 5, 15 and 45 seconds), then continues where it stopped. The data
  already copied is safe.

## The SSH host key changed

Sipdb refuses to connect when the SSH server's host key differs from the one
you trusted before. Ask your server admin whether the server was really
replaced before you trust a new key.

## "Local database … is being synced by another Sipdb process"

The app and the `sipdb` command (from Task Scheduler, say) cannot sync the
same local database at the same time. Wait until the other one finishes.

## A table is skipped

- **No PK and no unique key:** Sipdb cannot track its rows. Add a primary
  key on the server if the table needs copying.
- **The local table uses an engine other than InnoDB:** change it to InnoDB.

## A function cannot be created (binary log)

A local MySQL with the binary log on refuses functions from normal users.
Run this once in the local MySQL:

```sql
SET GLOBAL log_bin_trust_function_creators = 1;
```

## Support bundle

If the problem stays, make a **support bundle**: the **History** page →
**Export support bundle**, or `sipdb support-bundle` in a terminal.

The zip holds the logs, profiles without passwords, table status and the
last 20 runs. No row contents are included, and the server is not contacted
to make it. **Check it before you send it:** error messages from the
database can contain data values.

Send it to {{ site.support_email }}.

[Back to the guide](../)
