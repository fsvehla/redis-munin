Redis Munin
===========

A set of munin scripts to monitor redis

Installation
============

1. copy the file in /usr/share/munin/plugins/
2. make a link with the parameters you want in /etc/munin/plugins/

        ln -s /usr/share/munin/plugins/redis_memory_ /etc/munin/plugins/redis_memory_127_0_0_1_6379

Usage
==========

Parameters
-------

The parameters are in the filename in the format \_IP\_PORT, where IP is the 4 part ipv4 separated by '\_'.
They can also be set in YAML via a file in the munin `plugin-conf.d` named redis.conf.  

Valid link name
---------------

Note the ending '\_' when no ip or port or when not using a config file:

* redis\_command\_
* redis\_command\_1\_2\_3\_4\_
* redis\_command\_1\_2\_3\_4\_port

ip will default to 127.0.0.1

port will default to 6379

Scripts
=======

* redis\_change\_since\_last\_save\_

    Number of changes since last save

* redis\_databases\_

    List all DBs with number of keys and expire

* redis\_memory\_

    Used memory

* redis\_total\_commands\_

    Total commands

* redis\_total\_connections\_

    Total connections

* redis\_users\_

    Current clients

* resque\_failed\_

    COUNTER for failures

    Need resque-web

    TODO use driver or netcat or telnet 

* resque\_workers\_

    % of working workers

    Need resque-web

    TODO use driver or netcat or telnet

* resque\_queues\_

    COUNTER for in / out jobs per queue.
    This ones needs some hooks to create the stats:

        def self.after_enqueue(*job_args)
            Resque::Stat.incr(@queue.to_s + ":pushed")
        end

        def self.after_perform(*job_args)
            Resque::Stat.incr(@queue.to_s + ":finished")
        end
        
    https://github.com/defunkt/resque/blob/master/docs/HOOKS.md

Changelog
=======

 * added keyspace hit/miss statistics (** Christian Parpart <trapni@gentoo.org> **)
 * fixed redis\_databases\_ labels (thanks japerk)

