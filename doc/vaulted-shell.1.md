vaulted-shell 1
===============

NAME
----

vaulted shell - starts an interactive shell with the secrets for the vault loaded into the shell

SYNOPSIS
--------

`vaulted shell` *name*

DESCRIPTION
-----------

Starts an interactive shell (uses the `SHELL` environment variable, if set;
otherwise defaults to `/bin/sh`).

AWS KEY
-------

Note: By default, Vaulted substitutes a temporary set of credentials when spawning an environment.
The AWS key input here may not match the key loaded into your environment. This feature can be toggled in the
`vaulted edit` menu.

Vaulted uses the permanent credentials stored in the vault to generate a set of temporary credentials using AWS STS.
The temporary credentials generated are valid for a specific duration, set in the `vaulted edit` menu. This duration
may be set between 15m and 36h.

_**Note:** when Vaulted is configured to assume a role, the maximum duration for a vault is `1h`. Configuring higher
values will cause AWS to return an error when spawning the vault._

This impacts the following environment variables:

 * `AWS_ACCESS_KEY_ID`  
   This is the temporary access key id or the access key id stored in the vault,
   depending on whether substitution is enabled.
 * `AWS_SECRET_ACCESS_KEY`  
   This is the temporary secret access key or the secret access key stored in the vault,
   depending on whether substitution is enabled.
 * `AWS_SESSION_TOKEN` (additionally, `AWS_SECURITY_TOKEN` is set to support legacy SDKs)  
   This is set to "" if temporary credential substitution is disabled.