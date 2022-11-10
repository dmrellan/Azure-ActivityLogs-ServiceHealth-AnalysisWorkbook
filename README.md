# Azure Activity Logs - Service Health Analysis Workbook


**What is Azure Service Health?**

Azure offers a suite of experiences to keep you informed about the health of your cloud resources. This information includes current and upcoming issues such as service impacting events, planned maintenance, and other changes that may affect your availability.
 
Azure Service Health is a combination of three services:
- Azure Status page
- Azure Service Health
- Resource health
 
In this thread, we will be talking about Service Health, which provides a personalized view of the health of the Azure services and regions you are using. This is the best place to look for service impacting communications about outages, planned maintenance activities, and other health advisories because the authenticated Service Health experience knows which services and resources you currently use. The best way to use Service Health is to set up Service Health alerts to notify you via your preferred communication channels when service issues, planned maintenance, or other changes may affect the Azure services and regions you use.
 
The challenge here is we can set up alerts by Subscription. If our environment has many of them, we could have a situation where we receive emails/communications from the same issue (TrackingID) per Subscription.
 
For example:
	_If we have SubA and SubB in our Management Group and we have two Application Insights resources, SubA-AI-01, and SubB-AI-01, in the western Europe region, and suddenly there is an issue in AI service in that region, we are receiving two notifications/emails to communicate that Application Insights service is impacted in WE region, one communication per SubA and other per SubB._
 
Some people do not know that "Service Health" is a category of messages inside Azure Subscription Activity Logs.

![image](https://user-images.githubusercontent.com/35997289/201133909-e95afc3c-c886-4839-b559-f65951843c8f.png)

So we could use Azure Policy to configure all of our Azure Subscriptions to export Activity Logs (in this scenario, Service Health category) to the same Log Analytics workspace and, once there, create KQL queries, workbooks, or notifications based on the centralized information. This will let us generate only one alert to notify an issue (TrackingID) detailing the subscriptions, regions, and services affected.

![image](https://user-images.githubusercontent.com/35997289/201133980-030e3289-4369-419e-9a8d-1c43d43abacc.png)

Here you can find the Activity Logs Service Health Analysis workbook to see incident information in the same visualization. You can filter by TrackingID and check their evolution, subscriptions, and regions affected. Moreover, you could use the queries in the workbook, or the query shared on this site to create an alert (https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-create-new-alert-rule?tabs=log) when a new issue (tracking ID) is detected and so, summarize all notifications by each subscription in only one alert.

![image](https://user-images.githubusercontent.com/35997289/201134056-3856b660-9d07-4534-886e-06d533cb1d62.png)




