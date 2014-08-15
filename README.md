Logentries Chef Cookbook
==============

Installs/Configures the Logentries agent to allow logging to [Logentries](https://logentries.com)

Requirements
------------

### Platform:

* Debian
* Ubuntu
* Rhel

### Cookbooks:

The following are dependencies of the Logentries cookbook

* apt
* yum

Attributes
----------

### Default

* `node['le_chef']['account_key']` - your Logentries account_key (this can be found following [this link](https://logentries.com/doc/accountkey/))
* `node['le_chef']['hostname']` - sets the hostname of the log to the machine name, defaults to `node['hostname']`
* `node['le_chef']['name']` - sets the name of the logical name of the log, defaults to `node['hostname']`
* `node['le_chef']['logs_to_follow']` - An array of logs to follow (use absolute paths)

Usage
-----

Put depends 'yum', and 'apt', in your metadata.rb to gain access to the resources.

Using on AWS Opsworks
--------------------------

1. Add the logentries configuration in an 'le' block in the stack configuration. (see sample below)
2. Depending on how you run custom recipes on the stacks, either:
  - add this cookbook to your custom recipes
  - add this cookbook to your custom recipes with Berkshelf
  - use this repo directly as your custom chef recipes repository URL.


```
"le": {
         "account_key":"abc",
         "hostname": "app-99",
         "logs_to_follow": [
           "/var/log/messages",
           "/var/log/secure"
         ]
      }
```


Updating the Logentries Agent
=============================

Restarting the Chef script will allow the recipe to install any updates to the Logentries agent.

License and Author
------------------

Author:: Joe Heung (<joe.Heung@logentries.com>)
Author:: Caroline Fenlon

Copyright (C) 2014, RevelOps Inc.

License:: All rights reserved
