# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

**Resource types**

* [`puppet_ds`](#puppet_ds): Manages the Directory Services config in PE

**Tasks**

* [`get_ds_data`](#get_ds_data): Task to retrieve current DS data from API https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#get-ds. The output is parsed with pyth
* [`set_ds_data`](#set_ds_data): Task to update DS data for the API as a single json object https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#put-ds. To test this 
* [`set_ds_json_data`](#set_ds_json_data): Set DS data from json data,  {} is accepted but will function as removing all json data (use puppet_ds::unset_ds task) otherwise provide vali
* [`test_ds_data`](#test_ds_data): Task to test DS data from API https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#put-ds-test, test is only valid if you have set th
* [`unset_ds`](#unset_ds): Unset ds data as https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#request-format-01 will unset your external directory settings i

## Resource types

### puppet_ds

This must be applied to the Master which has RBAC running on it as it will use the agent's certs to auth.

#### Examples

##### 

```puppet
puppet_ds { 'https://pe-201921-master.puppetdebug.vlan:4433':
  ensure                              => 'present',
  base_dn                             => 'ou=mathematicians,dc=example,dc=com',
  connect_timeout                     => 30,
  disable_ldap_matching_rule_in_chain => true,
  display_name                        => 'ldap.forumsys.com',
  group_lookup_attr                   => 'ou',
  group_member_attr                   => 'member',
  group_name_attr                     => 'name',
  group_object_class                  => 'ou',
  help_link                           => 'http://techsmruti.com/online-ldap-test-server/',
  hostname                            => 'ldap.forumsys.com',
  login                               => 'cn=read-only-admin,dc=example,dc=com',
  password                            => 'password',
  port                                => 636,
  search_nested_groups                => true,
  ssl                                 => true,
  ssl_hostname_validation             => true,
  ssl_wildcard_validation             => false,
  start_tls                           => false,
  user_display_name_attr              => 'displayName',
  user_email_attr                     => 'mail',
  user_lookup_attr                    => 'uid',
  user_rdn                            => 'uid',
}
```

#### Properties

The following properties are available in the `puppet_ds` type.

##### `ensure`

Data type: `Enum[present, absent]`

Whether this resource should be present or absent on the target system.

Default value: present

##### `base_dn`

Data type: `String`

''

##### `connect_timeout`

Data type: `Integer`

The number of seconds that PE attempts to connect to the directory server before timing out. Ten seconds is fine in the majority of cases. If you are experiencing timeout errors, make sure the directory service is up and reachable, and then increase the timeout if necessary

Default value: 60

##### `disable_ldap_matching_rule_in_chain`

Data type: `Boolean`

Select Yes to turn off the LDAP matching rule that looks up the chain of ancestry for an object until it finds a match. For organizations with a large number of group memberships, matching rule in chain can slow performance.

##### `display_name`

Data type: `String`

The name that you provide here is used to refer to the external directory service anywhere it is used in the PE console. For example, when you view a remote user in the console, the name that you provide in this field is listed in the console as the source for that user. Set any name of your choice.

##### `group_lookup_attr`

Data type: `String`

The value used to import groups into PE

Default value: cn

##### `group_member_attr`

Data type: `String`

Tells PE how to find which users belong to which groups. This is the name of the attribute in the external directory groups that indicates who the group members are.

Default value: member

##### `group_name_attr`

Data type: `String`

The attribute that stores the display name for groups. This is used for display purposes only.

Default value: name

##### `group_object_class`

Data type: `String`

The name of an object class that all groups have

Default value: group

##### `group_rdn`

Data type: `Optional[String]`

The group RDN that you set here is concatenated with the base DN to form the search base when looking up a group

##### `help_link`

Data type: `Optional[String]`

If you supply a URL here, a "Need help logging in?" link is displayed on the login screen. The href attribute of this link is set to the URL that you provide

##### `hostname`

Data type: `String`

The FQDN of the directory service to which you are connecting

##### `login`

Data type: `Optional[String]`

The distinguished name (DN) of the directory service user account that PE uses to query information about users and groups in the directory server

##### `password`

Data type: `Optional[String]`

The lookup user\'s password

##### `port`

Data type: `Integer`

The port that PE uses to access the directory service. The port is generally 389, unless you choose to connect using SSL, in which case it is generally 636

Default value: 636

##### `search_nested_groups`

Data type: `Boolean`

Select true to search for groups that are members of an external directory group. For organizations with a large number of nested group memberships, searching nested groups can slow performance

##### `ssl`

Data type: `Boolean`

Whether to use SSL to connect, StartTLS and SSL are mutually exclusive

Default value: true

##### `ssl_hostname_validation`

Data type: `Boolean`

Select Yes to verify that the Directory Services hostname used to connect to the LDAP server matches the hostname on the SSL certificate. This option is not available when you choose to connect to the external directory using plain text.

Default value: true

##### `ssl_wildcard_validation`

Data type: `Boolean`

Select Yes to allow a connection to a Directory Services server with a SSL certificates that use a wildcard (*) specification. This option is not available when you choose to connect to the external directory using plain text.

##### `start_tls`

Data type: `Boolean`

Whether to use StartTLS to connect, StartTLS and SSL are mutually exclusive

##### `type`

Data type: `Optional`

This is undocumented, not sure what it is for

##### `user_display_name_attr`

Data type: `String`

The directory attribute to use when displaying the user\'s full name in PE

Default value: displayName

##### `user_email_attr`

Data type: `String`

The directory attribute to use when displaying the user\'s email address in PE

Default value: mail

##### `user_lookup_attr`

Data type: `String`

This is the directory attribute that the user uses to log in to PE. For example, if you specify sAMAccountName as the user login attribute, Harold logs in with the username "harold11" because sAMAccountName=harold11 in the example directory service entry provided above

Default value: sAMAccountName

##### `user_rdn`

Data type: `Optional[String]`

The user RDN that you set here is concatenated with the base DN to form the search base when looking up a user. For example, if you specify ou=users for the user RDN, and your base DN setting is ou=Puppet,dc=example,dc=com, PE finds users that have ou=users,ou=Puppet,dc=example,dc=com in their DN

#### Parameters

The following parameters are available in the `puppet_ds` type.

##### `name`

namevar

Data type: `String`

URI of the console to manage, including port i.e. https://mymaster.company.com:4433

##### `force`

Data type: `Optional[Boolean]`

Force will skip validation and force application of the config

## Tasks

### get_ds_data

Task to retrieve current DS data from API https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#get-ds. The output is parsed with python and formatted

**Supports noop?** false

### set_ds_data

Task to update DS data for the API as a single json object https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#put-ds. To test this and ldap connectivity you can use a public LDAP (http://techsmruti.com/online-ldap-test-server/ for example) the data for this is included in the task

**Supports noop?** false

#### Parameters

##### `name`

Data type: `String[1]`

Used to refer to DS elsewhere in the UI. Example: 'My awesome AD server' 

##### `help_link`

Data type: `Optional[String[1]]`

Static link hosted by customer for LDAP login assistance. Example: 'https://doge.com/help-logging-in-with-ldap' 

##### `hostname`

Data type: `String[1]`

Example: 'ldap.forumsys.com' 

##### `port`

Data type: `Integer`

Example: '389' 

##### `lookup_user`

Data type: `Optional[String[1]]`

login user RBAC will use this login to query the directory service when looking for user and group data.

##### `lookup_password`

Data type: `Optional[String[1]]`

login password RBAC will use this login to query the directory service when looking for user and group data. Note: This value will be stored and transmitted in plain text. Example: 's3cr!tz1' 

##### `connect_timeout`

Data type: `Optional[Integer]`

Connection timeout (in seconds) Example: 10

##### `ssl`

Data type: `Boolean`

Required Boolean configuration to use SSL protocol

##### `ssl_hostname_validation`

Data type: `Optional[Boolean]`

RBAC will verify that the DS hostname used to connect matches the certificate hostname when using SSL.

##### `ssl_wildcard_validation`

Data type: `Optional[Boolean]`

RBAC will allow wildcards within certificates when verifying SSL hostname connections to DS

##### `start_tls`

Data type: `Optional[Boolean]`

*

##### `base_dn`

Data type: `String[1]`

Base Distinguished Name, needed for constructing queries and binding as lookup user. Example: dc=puppetlabs,dc=com

##### `user_lookup_attr`

Data type: `String[1]`

User Login Attribute, needed for constructing queries. Example: 'cn' 

##### `user_email_attr`

Data type: `String[1]`

 Needed to pull email of user. Example: 'mail' 

##### `user_display_name_attr`

Data type: `String[1]`

 Needed to pull display name of user. Example: 'displayName' 

##### `user_rdn`

Data type: `String[1]`

Needed for constructing queries. Example: 'cn=Users' 

##### `group_object_class`

Data type: `Optional[String[1]]`

Needed when searching for groups. If not set, will default to '\*'. Example: 'group' 

##### `group_member_attr`

Data type: `String[1]`

Needed to determine group membership. Example: 'member' 

##### `group_name_attr`

Data type: `String[1]`

Needed to pull the name of a group. Example: 'name' 

##### `group_lookup_attr`

Data type: `String[1]`

Needed for constructing queries. Example: 'cn' 

##### `group_rdn`

Data type: `String[1]`

Needed for constructing queries. Example: 'cn=Groups' 

##### `disable_ldap_matching_rule_in_chain`

Data type: `Boolean`

Set via the API only. This disables a performance shortcut that we use for AD 2003 or AD 2008 and greater but that fails on certain datasets. Customers, with the help of support, will set this option as needed. Example: true 

### set_ds_json_data

Set DS data from json data,  {} is accepted but will function as removing all json data (use puppet_ds::unset_ds task) otherwise provide valid json for setting ds.

**Supports noop?** false

#### Parameters

##### `ds_json`

Data type: `Hash`

json hash of DS data, the minimal object is { "base_dn": "ou=mathematicians,dc=example,dc=com", "display_name": "ldap.forumsys.com", "group_lookup_attr": "ou", "group_member_attr": "member", "group_name_attr": "name", "hostname": "ldap.forumsys.com", "port": 389, "ssl": false, "user_display_name_attr": "displayName", "user_email_attr": "mail", "user_lookup_attr": "uid", "user_rdn": "uid", "login": "cn=read-only-admin,dc=example,dc=com", "password" : "password", "group_rdn" : null, "help_link" : null, "connect_timeout" : null, "group_object_class" : "ou"} 

### test_ds_data

Task to test DS data from API https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#put-ds-test, test is only valid if you have set the data. If setting data in the console you must have saved the configuration to test it

**Supports noop?** false

### unset_ds

Unset ds data as https://puppet.com/docs/pe/2017.3/rbac_api_v1_directory.html#request-format-01 will unset your external directory settings in the console

**Supports noop?** false

