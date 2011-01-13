Redis Munin
===========

A set of munin scripts to monitor redis

Installation
============

1. copy the file in /usr/share/munin/plugins/
2. make a link with the parameters you want in /etc/munin/plugins/

> ln -s /usr/share/munin/plugins/redis_memory_ /etc/munin/plugins/redis_memory_127_0_0_1_6379

Usage
==========

Parameters
-------

The parameters are in the filename in the format _IP_PORT, where IP is the 4 part ipv4 separated by '_'

Valid link name
---------------

Note the ending '_' when no ip or port:

* redis_command_
* redis_command_1_2_3_4_
* redis_command_1_2_3_4_port

ip will default to 127.0.0.1

port will default to 6379

Scripts
=======

* redis_change_since_last_save_

    Number of changes since last save

* redis_databases_

    List all DBs with number of keys and expire

* redis_memory_

    Used memory

* redis_total_commands_

    Total commands

* redis_total_connections_

    Total connections

* redis_users_

    Current clients
