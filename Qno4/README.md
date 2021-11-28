## Install logstash in your system. download a sample nginx log from https://github.com/elastic/examples/blob/master/Common%20Data%20Formats/nginx_logs/nginx_logs , parse the logs using logstash. The parsed output must contain the geogriphical information like country, state etc. that the request is originating from. save the parsed output to a file in your system.

Logstash is a log-parsing software used to collect logs and store them on Elasticsearch.
To install Logstash on our system, We need to follow the steps given below:
- Firstly we need to have Java installed in our system. Then only we need to proceed to the next step. We can verify the java installation using the following command on our linux machine:
  - `java -version`<br/>
  ![verify java](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno4/snapshots/verify%20java.png)
- Now we can install Logstash easily with the following command:
  - `sudo apt-get install logstash -y`
- Once the Logstash is installed, we need to enable it to start at system reboot using the following commands:
  - `systemctl start logstash`
  - `systemctl enable logstash`
- We can check if our logstash is running on our system by using following command:
  - `ps -ef | grep logstash`<br/>
  ![verifying logstash](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno4/snapshots/verifying%20logstash.png)
- Now we need to configure the input, filter, and the output plugins inside _/etc/logstash/conf.d/_ directory so as to parse our nginx log file producing the output with the geographical information like country, state etc using the following command:
  - `nano /etc/logstash/conf.d/logstash.conf`<br/>
  ![logstash configuration file](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno4/snapshots/logstash%20configuration%20file.png)
  - We can see the configuration file for our task in the snapshot above.
- After all the steps, let’s navigate to the /usr/share/logstash directory and run the following command so that the logstash will parse our nginx logs file as per configuration:
  - `sudo bin/logstash --path.settings /etc/logstash --path.data sensor39 -f /etc/logstash/conf.d`<br/>
  ![running a parsing command](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno4/snapshots/running%20a%20parsing%20command.png)
- After we execute the above command, we can check the logs out file in this path as we configured /var/log/logstash/nginxlogs_output.<br/>
  ![checking our log output file](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno4/snapshots/checking%20our%20log%20output%20file.png)
- We can see that the new nginxlogs_output file has been generated. This log output file has been push in this repository for the review also, and a small snapshot can be viewed below:<br/>
  ![log output](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno4/snapshots/logs%20output.png)
- In the snapshot above of the parsed output we can see the country, country_code, postal_code, latitude, longitude, timezone etc.

Therefore we have successfully parsed the nginx logs file using logstash as per our requirements.
