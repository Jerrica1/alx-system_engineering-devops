<p align="center">
  <img src="https://github.com/Jerrica1/alx-system_engineering-devops/blob/master/0x19-postmortem/postmortem%20diagram.png" width="75%" height="75%" alt="Image Description">
</p>



### Issue Summary:

#### Outage Duration: 

3 hours (08:00 AM - 11:00 AM, UTC)

Impact: Slowdown of Payment Processing Service, affecting 20% of users, causing delayed transactions and user frustration.

Root Cause: Database connection pool exhaustion led to service degradation.

#### Timeline:

* 08:00 AM: The issue was detected when monitoring alerts showed a sudden increase in transaction processing times.
* 08:15 AM: Engineers began investigating the issue, suspecting high traffic initially.
* 08:30 AM: After monitoring revealed unusual spikes in database connections, focus shifted to the database layer.
* 09:00 AM: Misleadingly, initial debugging pointed towards inefficient query execution.
* 09:30 AM: Escalated the incident to the database team for in-depth analysis.
* 10:00 AM: Database team identified database connection pool exhaustion as the root cause.
* 10:30 AM: Database team applied configuration changes to optimize connection pooling.
* 11:00 AM: Issue was resolved, and payment processing service returned to normal.

#### Root Cause and Resolution:

Root Cause: Database connection pool was set too low, causing exhaustion during peak traffic, leading to slow transactions.

Resolution: The connection pool configuration was increased to handle higher traffic, and database resources were optimized.

#### Corrective and Preventative Measures:

Improvements:

Review and adjust connection pool settings for all critical services.
Implement dynamic scaling of connection pools based on traffic patterns.

#### Tasks to Address the Issue:

* Patch database connection pool configurations across all services to prevent future exhaustion.
* Implement proactive monitoring to detect connection pool depletion and potential bottlenecks.
* Set up automated scaling of connection pools based on incoming traffic, reducing the risk of slowdowns during peak times.

