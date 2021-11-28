# Mention 10 best practises when logging. Why is log formatting necessary?

## Answer:
The 10 best practises when logging are:
1. **Know What Logs to Monitor, and What Not to Monitor**<br/>
Know what not to log. Just because you can log something doesn’t mean you should — and logging too much data can make it harder to find the data that actually matters. It also adds complexity to your log storage and management processes because it gives you more logs to manage.

2. **Implement a Log Security and Retention Policy**<br/>
Logs contain sensitive data. A log security policy should review sensitive data – like personal data of your clients or internal access keys for APIs. Make sure that sensitive data gets anonymized or encrypted before you ship logs to any third party. GDPR log management best practices teach you about good practices for data protection of sensitive data and personal data in web server logs. The secure transport of log data to log management servers requires the setup of encrypted endpoints for TLS or HTTPS on client and server side.

3. **Design a Scalable and Reliable Log Storage**<br/>
Planning the capacity for log storage should consider high load peaks. When systems run well, the amount of data produced per day is nearly constant and depends mainly on the system utilization and amount of transactions per day.  In the case of critical system errors, we typically see accelerated growth in the log volume. If the log storage hits storage limits, you lose the latest logs, which are essential to fix system errors. The log storage must work as a cyclic buffer, which deletes the oldest data first before any storage limit is applied.

4. **Use the Proper Log Level**<br/>
Among others, one important piece of information each log entry should include is the appropriate log level since it helps differentiate severe and important events from irregular or even regular events. Log levels will depend on the framework, but ERROR, WARNING, INFO, DEBUG are usually available. You need to be consistent in assigning severity to log messages. Overthewise filtering by severity will not work as expected.

5. **Create Meaningful Log Messages**<br/>
Readable and useful log messages are key for faster troubleshooting. If logs contain only some error codes or ‘cryptic’ error messages it can be difficult to understand. As a Developer, you can save your organization a lot of time by providing a meaningful log message.

6. **Use Structured Log Formats**<br/>
The log format should be structured (e.g., JSON or key/value format) having various fields like timestamp, severity, message and any other relevant data fields like process ID, transaction ID, etc. If you don’t use a unique log format for all your applications, normalize the logs in the log shipper. Parse logs and store logs in a structured format.

7. **Make Log Level Configurable**<br/>
Some application logs are too verbose and other application logs don’t provide enough information about the activities. Adjustable log levels are the key to configure the verbosity of logs. Another topic for log reviews is the challenge to balance between logging relevant information and not exposing personal data or security-related information. If so, make sure that those messages can be anonymized or encrypted.

8. **Inspect Audit Logs Frequently**<br/>
Acting on security issues is crucial – so you should always have an eye on audit logs. Setup security tools such as auditd or OSSEC agents. The tools implement real-time log analysis and generate alert logs pointing to potential security issues. On top of such audit logs, you should define alerts on logs in order to be notified quickly of any suspicious activity. For more details, check out a quick tutorial on using auditd, plus you’ll find some complementary frameworks too.

9. **Review & Maintain Your Logs Constantly**<br/>
Unmaintained log data could lead to longer troubleshooting times, risks of exposing sensitive data or higher costs for log storage. Review the log output of your applications and adjust it to your needs. Reviews should cover usability, operational, and security aspects. 

10. **View Logging as an Enabler of GitOps**<br/>
Connect the dots. Logging is one part of an entire monitoring strategy. To practice truly effective monitoring and alerting, you need to complement your logging with other types of monitoring like monitoring based on events, alerts and tracing. This is the only way to get the whole story of what’s happening at any point in time. Logs are great for giving you high-definition details on issues, but this is useful only once you’ve seen the forest and are ready to zoom into the trees. Metrics and events at an aggregate level may be more effective, especially when starting to troubleshoot an issue.

When it comes to creating readable log files, log formatting is key. The fundamental issue with log files, and the necessity for a structured format, is that they are often unstructured text data, making it impossible to extract usable information from them. A log format is a structured format for making logs machine-readable and parsable. This is the power of structured logs and a log management system that can handle them. One of the most important characteristics of log management software is the ability to convert raw data into something that is immediately understandable and easy to read.
