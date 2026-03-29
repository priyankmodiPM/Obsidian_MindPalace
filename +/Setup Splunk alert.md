---
created: 2026-02-11
tags:
  - AEM
  - AEM/DM-Concept
  - Documentation
Reference: https://splunk-us.corp.adobe.com/en-GB/app/app_scene7/alerts
---
Parent - [[Auto-Reflow MOC]]
# 1 Steps

1. Created a public channel on Slack
2. Create an app
	1. Go to [Slack API : App integration](https://api.slack.com/apps)
	2. Create the app for your service
	3. Enable incoming webhooks [Incoming Webhooks Slack App](https://api.slack.com/apps/A0AF66H1N2C/incoming-webhooks?)
	4. Add the app to a channel in the workspace
	5. Copy the webhook URL ([My App's details showing webhook URL](https://api.slack.com/apps/A0AF66H1N2C/install-on-team?success=1))
![[Screenshot 2026-02-11 at 5.13.20 PM.png|590x356]]

3. On Splunk
	1. Go to [Splunk dashboard](https://splunk.or1.adobe.net/en-GB/manager/TA-aem_skyline/saved/searches?app=TA-aem_skyline&count=10&offset=0&itemType=&owner=pmodi&search=)
	2. Create a new alert
	3. Setup the query
	4. Add a cron or schedule for running the alerts
	5. Add the channel name (might not be required since webhook takes precedence) but good to add for reference
	6. Add the webhook URL you copied earlier
![[Screenshot 2026-02-11 at 5.13.27 PM.png]]