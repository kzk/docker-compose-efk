Docker compose file for setting up a EFK service
================================================

A basic docker compose file that will set up Elasticsearch, Fluentd, and Kibana.

Increase virtal memory
----------------------

Elasticsearch uses a mmapfs directory by default to store its indices. The default operating system limits on mmap counts is likely to be too low, which may result in out of memory exceptions.

On Linux, you can increase the limits by running the following command as root:

    sysctl -w vm.max_map_count=262144
    
To set this value permanently, update the vm.max_map_count setting in /etc/sysctl.conf. To verify after rebooting, run sysctl vm.max_map_count.

Example
-------

The file `example/httpd.yml` shows how to configure a service to use EFK as its logging facility. To test using this file, just run:

    docker-compose -f docker-compose.yml -f example/httpd.yml up

with latest elasticsearch 7.0.1 and kibana 7.0.1 run:

    docker-compose -f efk7.yml -f example/httpd.yml 

Then, go to your browser and access `http://localhost:80` (httpd) and `http://localhost:5601` (kibana). You should be able to see the httpd's logs in kibana's discovery tab. By the way, if you are wondering what is this index kibana asks the fist time you access it, it is `fluentd-*`.

After you are done, just run:

    docker-compose -f docker-compose.yml -f example/httpd.yml rm -f

with latest elasticsearch 7.0.1 and kibana 7.0.1 run:
    
    docker-compose -f efk7.yml.yml -f example/httpd.yml up

And all services will be reclaimed.




