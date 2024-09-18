#### Notification Platform

High Level Design - 
 - Scaling Issues
 - Microservices , data flow, failure detection and diagnostics
Low Level Design - 
 - Code, Database schema


##### 5 Step Approach for any design project
 - prerequisites
    - Understand the problem statement
    - Discuss the functional requirements
    - Discuss the non-functional requirements (Security, etc)
    - Scale Estimation
 - Design 

##### Problem Statement - Notification System 
    - App Notifications
    - In app notifications
    - SMS or Email Notifications
    - OTPs
    - Social Media Notifications

>Notifications might or might not be just a feature for every organization*

##### Problem Statement - 
Build a SaaS Notification platform that can provide notification service to its clients.

 - What is a Notification?         
    - Any small content (<1kb) that we wish to send to  some user via any means. This can be text, url or media.        

##### Functional Requirements - 
1. Clients should be able to send notifications to their users. 

    [Client App]   --`request`---> [Our System]   --`notifications`---> [Users]

2. System should support multiple channels of notifications, we should be able to plug and play more channels in future without disturbing the whole system.             
3. Clients should be able to **broadcast** the notifications to the users.            
4. Clients should be able to manage the user's list
5. Rate Limiting 
 - client side limits (Quota Limit) 
based on purchase type 
- User side limits
  - no one should get more notifications
  - users should be able customize the notifications -  turn on/turn off the specific notifications
6. Observability 
 - to monitor, observe and fix the issues on the go 
 - to detect the issue
 - to fix the issue 
 - to verify whether the fix is working or not?
 - Analytics - notifications sent to user/client/day 

##### Non Functional Requirements - 
1. Compliance  -  to be inline with services/rules like TRAI 
2. We should consider the Priority of notifications 
 - OTPs - High priority notifications
 - Promotions - low priority notifications
3. High Availability
 - Fault Tolerence
4. Reliability
 - Backups
 - Retry mechanism
5. Low Latency
6. Idempotency or Single Delivery
 - Same notification should not be sent more than once.
7. Security - difficult - so we will leave it to security expert.


##### APIs - 
1. POST - /notify
 Request   
           -  apiKey - clientId
           - userId ( we should not send list of UserIds for broadcast in APIs) so we will go for **filter**
           - content - JSON
           - time - schedule
**content** - 
type - otp/promotional/reminder
channels - {
    sms  : { text, icon, attachment }
    email : { subject, cc/bcc, body, attachments }
    app : { msg, action }
}
 Response - 
           - API Status
           - Success/Failure

##### Scale Estimation - 
1. No. of Users - 2 Billion Users across all clients
2. Avg Count of Notifications send to User per Day - 10
Count of Notifications/Second - 2 * 10^9 * 10 / day -> 2 * 10^10 / 10*5  
Avg Notifications per day -  2 * 10^5
Peak Notifications per day - 50 times of the average - 10 million notifications per second

![image](https://github.com/user-attachments/assets/f63c2761-c28d-4bdc-ba2f-6e4beecdb6ce)

