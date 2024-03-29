# Reference

<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

### Classes

* [`resolv_conf`](#resolv_conf): Manage the DNS resolver configuration file /etc/resolv.conf

## Classes

### <a name="resolv_conf"></a>`resolv_conf`

Manage the DNS resolver configuration file /etc/resolv.conf

#### Examples

##### Create resolver config file using default parameters

```puppet

class { resolv_conf': }
```

##### Create resolver config file with specific name servers

```puppet

class { resolv_conf':
  nameservers => [ '8.8.8.8', '8.8.4.4', ],
}
```

##### Create resolver config file with specific name servers & options

```puppet

class { resolv_conf':
  nameservers => [ '8.8.8.8', '8.8.4.4', ],
  options     => [ 'rotate', 'timeout:2, ],
}
```

##### Create resolver config file where a local name server is prefered

```puppet

class { resolv_conf':
  nameservers              => [ '8.8.8.8', '8.8.4.4', ],
  prepend_local_nameserver => true,
}
```

#### Parameters

The following parameters are available in the `resolv_conf` class:

* [`nameservers`](#-resolv_conf--nameservers)
* [`domainname`](#-resolv_conf--domainname)
* [`searchlist`](#-resolv_conf--searchlist)
* [`sortlist`](#-resolv_conf--sortlist)
* [`options`](#-resolv_conf--options)
* [`prepend_local_nameserver`](#-resolv_conf--prepend_local_nameserver)
* [`resolv_conf_file`](#-resolv_conf--resolv_conf_file)
* [`owner`](#-resolv_conf--owner)
* [`group`](#-resolv_conf--group)
* [`mode`](#-resolv_conf--mode)

##### <a name="-resolv_conf--nameservers"></a>`nameservers`

Data type: `Array[String,0,3]`

An array of name servers that the resolver should query for hostname
lookups. A maximum number of three name servers can be specified. The
default value is a single element array containing `127.0.0.1`.

##### <a name="-resolv_conf--domainname"></a>`domainname`

Data type: `Optional[String]`

A string that is used as a single element `searchlist`. The parameter
is obsolete and will be removed.

Default value: `undef`

##### <a name="-resolv_conf--searchlist"></a>`searchlist`

Data type: `Array[String]`

An array of domains that the resolver will search. This parameter cannot
be used together with `domainname`. The old restriction of six entries
has been removed. Check your documentation if your operating system
release supports more than six items.

Default value: `[]`

##### <a name="-resolv_conf--sortlist"></a>`sortlist`

Data type: `Array[String,0,10]`

An array of up to 10 IP/netmask items. These are used by the resolver to
sort the result in case multiple addresses are returned.

Default value: `[]`

##### <a name="-resolv_conf--options"></a>`options`

Data type: `Array[String]`

An array of option settings for the resolver. Each array element must be
the option to include in the configuration. The following options are
recognized: `ndots:n`, `timeout:n`, `attempts:n`, `debug`, `edns0`,
`inet6`, `ip6-bytestring`, `ip6-dotint`, `no-ip6-dotint`,
`no-check-names`, `rotate`, `single-request`, `single-request-reopen`.
The first three options are expected to use a numeric value for `n` after
the colon. Check the man page `resolv.conf(5)` for details.

Default value: `[]`

##### <a name="-resolv_conf--prepend_local_nameserver"></a>`prepend_local_nameserver`

Data type: `Boolean`

A boolean value that determines if a local DNS server should be used
first. Setting this parameter to `true` will add `127.0.0.1` before the
servers given as `nameservers`. The last name server is silently ignored
if this would create a configuration with more than three servers. The
default value is `false`.

Default value: `false`

##### <a name="-resolv_conf--resolv_conf_file"></a>`resolv_conf_file`

Data type: `Stdlib::Absolutepath`

The absolute path of the file to manage. The default is
`/etc/resolv.conf`. In general it does not make sense to change this
parameter.

##### <a name="-resolv_conf--owner"></a>`owner`

Data type: `Optional[String]`

The owner of the file `/etc/resolv.conf`. The default is `root`.

Default value: `undef`

##### <a name="-resolv_conf--group"></a>`group`

Data type: `Optional[String]`

The group of the file `/etc/resolv.conf`. The default is `root` on Linux
and `wheel` on FreeBSD.

Default value: `undef`

##### <a name="-resolv_conf--mode"></a>`mode`

Data type: `Optional[Stdlib::Filemode]`

The file mode of the file `/etc/resolv.conf`. The default is `0644`.

Default value: `undef`

