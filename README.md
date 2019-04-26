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
       echo -n "HOST=`hostname` pq_size="
       du -sm $SPLUNK_DIR | egrep -o "[0-9]*"
       echo tokens over 10MB of queue:
    
       for F in `find $SPLUNK_DIR -type f -size +10M`
       do
          du -sh $F | sed -e "s^$SPLUNK_DIR/^^"
       done
      fi
