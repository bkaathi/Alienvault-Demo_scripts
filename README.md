##Sripts to inject demo data and traffic

This will make AV do demo stuff. Dance!
- Author: PacketInspector ([@pkt_inspector](https://twitter.com/pkt_inspector))
This will add named assets with properties, logged in users, netflow, vulnerability scan, and more....



To install:

```
git clone https://github.com/packetinspector/Alienvault-Demo
cd Alienvault-Demo
perl install.pl
```

The script will do all the work. Nothing to do beforehand. Nothing to do afterhand.
You can re-run it with no consequences

Need to start over?

```
alienvault-reconfig -c -d -v --rebuild_db;sleep 15;perl install.pl
```

The installer will install the generators, add them to startup, and run them.  In case you want to start/stop them yourself..

```
/etc/init.d/runpcaps [start|stop|restart]
/etc/init.d/runlogs [start|stop|restart]
```
####Want to add your own pcaps?

- Add them to the `./pcaps` directory
- Done
- The IPs will be rewritten on playback to match the assets

####Want to add your own plugins/logs?
- Add them to the plugins directory.  Everything must have the same basename.  
- You can add .sql/.log/.cfg files.
- Re-run the installer

####Log Samples
Your .log files can just be copies of logs right off a system.  No need to do anything.

You can have IPs substituted for you automatically by adding a variable into your logs

**Key** | **Replaced With**
--- | ---
`<RNDIP>` | Random IP, Totally made up. No bounds.
`<OTXIP>` | IP From OTX.  Uses DB from install

#### Where are all the logfiles going?
All the generated log files are put in
`/var/log/demologs`
They will be seperated by plugin.  A logrotate script for them is installed automatically. 

Forked from Santiago Bassett ([@santiagobassett](https://twitter.com/santiagobassett))

