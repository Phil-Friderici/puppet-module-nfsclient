puppet-module-nfsclient
=======================

[![Build Status](
https://api.travis-ci.org/kodguru/puppet-module-nfsclient.png?branch=master)](https://travis-ci.org/kodguru/puppet-module-nfsclient)

Puppet module to manage nfs client configuration.

NOTE: This module does not manage /etc/krb5.keytab any more.
Use a Keberos module such as [kodguru/puppet-module-krb5](https://github.com/kodguru/puppet-module-krb5/)
(version 1.0.0 or newer) if you need to manage Kerberos itself.

To ensure the service in restarted when /etc/krb5.keytab is updated you could
add logic similar to the code below in your profile to ensure it occurs.

```
...
include ::nfsclient
include ::krb5

if defined(File['krb5keytab_file']) {
  File['krb5keytab_file'] ~> Class['nfsclient']
}
...
```
If statement is in case File['krb5keytab_file'] is relevant if it could be catalogues
missing this resource.

gss
---
Enable GSS. Bool.

- *Default*: false

keytab
------
Location of keytab.

- *Default*: undef
