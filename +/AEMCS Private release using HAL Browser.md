---
tags:
  - AEM
  - AEM/DM-Concept
  - Documentation
---

- [ ] Complete wiki:[https://wiki.corp.adobe.com/display/WEM/Creating+a+new+private+AEM+release+for+use+in+Trial+envs](https://wiki.corp.adobe.com/display/WEM/Creating+a+new+private+AEM+release+for+use+in+Trial+envs)

Latest AEM release can be found at [Adobe Experience Cloud Uber Release](https://experience.adobe.com/#/@adobedpsdemo/uber-release-registry/releases/23963)

- [ ] jenkins job - [https://jenkins-evergreen.ci.corp.adobe.com/job/Sprouts/job/aemcs-developer-releases/](https://jenkins-evergreen.ci.corp.adobe.com/job/Sprouts/job/aemcs-developer-releases/)
- [ ] once you run the job, you will get the pvt release id via slackbot
- [ ] Then you need to change the releaseId in pipeline of the env you have created.  
	Steps:  
	- [ ] Open CM and check the pipeline associated with the env.
	- [ ] Open [https://git.corp.adobe.com/pages/experience-platform/self-service-hal-browser/#https://ssgadobe.io/api/program/47604/pipelines](https://git.corp.adobe.com/pages/experience-platform/self-service-hal-browser/#https://ssgadobe.io/api/program/47604/pipelines) give the pipeline ID.
	- [ ] Open [https://git.corp.adobe.com/pages/experience-platform/self-service-hal-browser/#https://ssg.adobe.io/api/program/47604/pipeline/348812](https://git.corp.adobe.com/pages/experience-platform/self-service-hal-browser/#https://ssg.adobe.io/api/program/47604/pipeline/348812). (replace the pipeline Id)
	- [ ] In the end there will be SELF. Open Non-GET.
	- [ ] In window replace POST with PUT.
	- [ ] Change releaseId.
	- [ ] Save.
	- [ ] Search for releaseId it should be updated in git (current window).
	- [ ] Go to CM, run the pipeline