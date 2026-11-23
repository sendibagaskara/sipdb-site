---
title: A read-only account for Sipdb
lang: en
---

Sipdb only uses an account that **can only read**. An admin account or a
normal application account (one that can `INSERT`, `UPDATE` and so on) is
refused.

Run the SQL below **yourself**, with an admin account and your own tool
(for example HeidiSQL, DBeaver, phpMyAdmin or the `mysql` client). Sipdb
never asks for or uses an admin account.

Replace three things:

- `<your-ip>`: the IP address Sipdb connects from. Through SSH, this is the
  SSH server's address. Use `%` if you are not sure.
- `<strong password>`: a new password for this account.
- `app_prod`: the name of the database to copy.

## MySQL 8.0.20 and later

```sql
CREATE USER 'sipdb'@'<your-ip>' IDENTIFIED BY '<strong password>';
GRANT SELECT, SHOW VIEW ON `app_prod`.* TO 'sipdb'@'<your-ip>';
GRANT SHOW_ROUTINE ON *.* TO 'sipdb'@'<your-ip>';
```

## MySQL 5.7, and MariaDB 10.x to 11.2

```sql
CREATE USER 'sipdb'@'<your-ip>' IDENTIFIED BY '<strong password>';
GRANT SELECT, SHOW VIEW ON `app_prod`.* TO 'sipdb'@'<your-ip>';
GRANT SELECT ON mysql.proc TO 'sipdb'@'<your-ip>';
```

## MariaDB 11.3 and later

```sql
CREATE USER 'sipdb'@'<your-ip>' IDENTIFIED BY '<strong password>';
GRANT SELECT, SHOW VIEW ON `app_prod`.* TO 'sipdb'@'<your-ip>';
GRANT SHOW CREATE ROUTINE ON *.* TO 'sipdb'@'<your-ip>';
```

The last privilege in each example (`SHOW_ROUTINE`, `mysql.proc`, `SHOW
CREATE ROUTINE`) is only for copying stored procedures and functions.
Without it, tables and views are still copied.

## Hosting with cPanel

Make the user in **MySQL Databases**, add it to the database, and tick
**only** `SELECT` and `SHOW VIEW`.

## Checking the result

In Sipdb, open the **Connection** page and press **Test connection**. When
the account is right, the Account line reads **PASSED (read privileges
only)**. When it is refused, Sipdb shows the privileges at fault and the SQL
to make a proper account.

[Back to the guide](../)
