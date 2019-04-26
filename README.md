# hec_perf_report

HEC stats shown in this report:

* Events/sec by receiving host and input definition
* Bytes/sec by receiving host and input definition
* HEC batching efficiency showing events and volume per post, and posts/sec
* Persistent queue size (requires collecting this info via scripted input, sample below)
* You will need to modify the env selection dropdown to fit your environment.


      #!/bin/bash
      SPLUNK_DIR=/opt/splunk/var/run/splunk/httpin
      if test -d $SPLUNK_DIR
      then
       date +"%F %T %z"
       echo -n "pq_size="
       du -sm $SPLUNK_DIR | egrep -o "[0-9]*"
