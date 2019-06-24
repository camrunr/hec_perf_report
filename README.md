# hec_perf_report

HEC stats shown in this report:

* HEC Health: Overall Health, Forwarding Health, Queue Health
* Persistent queue size (requires collecting this info via scripted input, sample below)
* Events/sec by receiving host and input definition
* Bytes/sec by receiving host and input definition
* HEC batching efficiency showing events and volume per post, and posts/sec

Reqs:

* Assumes you are installing on your MC
* You will need a custom group defined on your MC: hec (used as dmc_customgroup_hec)
* You will need to modify the env selection dropdown to fit your environment.

* The script I use to collect PQ size info

      #!/bin/bash
      SPLUNK_DIR=/opt/splunk/var/run/splunk/httpin
      if test -d $SPLUNK_DIR
      then
       date +"%F %T %z"
       echo -n "pq_size="
       du -sm $SPLUNK_DIR | egrep -o "[0-9]*"
      fi
