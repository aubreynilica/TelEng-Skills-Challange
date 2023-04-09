# TelEng-Skills-Challange
This pipeline is configured using a stdin puglin as well as an HTTP input plugin. The HTTP plugin allows for ingestion of data through single or multiline events over http(s). 
This message is then processed and parsed using a custom GROK pattern. I went ahead and parsed the whole message, and then later dropped the unnecessary fields within the muate filter.
I also renamed the neccesary fields within this filter. Using GREEDYDATA was a convenient way to capture the neccesary log information in a single field and later parse that out using key value pairs.
Finally, the data is outputted using the stdout plugin. This is a simple output which prints to the STDOUT of the shell running Logstash.

Additionally, I sent the data to logstash in a seperate terminal window using the command:

curl -XPUT -d '<14>1 2016-12-25T09:03:52.754646-06:00 contosohost1 antivirus 2496 - - alertname="Virus Found" computername="contosopc42" computerip="216.58.194.142" severity="1"' http://127.0.0.1:8080
