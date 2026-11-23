---
title: Connection profiles
lang: en
---

A profile holds how to reach the **production server** and your **local
database**. One profile = one server database copied into one local
database.

## Making a profile

1. Open Sipdb and pick **+ New profile** at the top left.
2. Fill in **Server**: host, port (usually 3306), the read-only user (see
   [read-only account](../read-only-account/)), password and database name.
3. Fill in **Local**: host (usually `127.0.0.1`), port, user, password and
   the target database name. A local database that does not exist yet is
   created.
4. Press **Test connection**. Sipdb checks the account's privileges and
   shows the strategy for every table.
5. Press **Save**.

**Passwords are kept in Windows Credential Manager**, not in the profile
file.

## A server behind SSH

When the database server can only be reached through an SSH server
(bastion), fill in **SSH**: host, user, and an SSH key file or a password.

On the first connection Sipdb asks about the SSH server's **host key**.
Compare its fingerprint with the one your server admin gave you before you
press **Trust**. If that key changes later, Sipdb refuses to connect: the
server may have been replaced, or someone may be listening in.

## TLS

Choose the TLS mode your server needs. `verify-ca` and `verify-identity`
check the server's certificate against the CA file you give.

[Back to the guide](../)
