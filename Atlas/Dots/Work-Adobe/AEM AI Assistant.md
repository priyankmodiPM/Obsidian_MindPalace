---
created: 2026-01-18
JIRA:
tags:
  - work
  - jira
  - agent
  - AEM
status: IN-PROGRESS
---
Description: 

> [!NOTE] Important links
> - Setup - [Wiki with setup for all 4 repos](https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=MKTOENG&title=Full+stack+dev+for+ao-reasoning+engine#Fullstackdevforaoreasoningengine-3.InyourAdobe-dx-agent-uirepo)
> - EAA (Advisory agent) - [https://github.com/AEM-Assets-Adobe/aem-experience-advisory-agent](https://github.com/AEM-Assets-Adobe/aem-experience-advisory-agent)
> - NPM Auth Token [^1]
> - Query params for DM manifest [^2]
> - A great [guide](https://github.com/Adobe-dxue/Adobe-dx-agent-registry/blob/4ad635b2f76aaa98dc211bf348080226302a7531/CONTRIBUTING.md) to understanding the various repositories
> - Splunk URL - [https://splunk.or1.adobe.net/](https://splunk.or1.adobe.net/)
> 	- Sample splunk queries [^3] [^4] [^5] 


> Related threads
> 	1. 

# 1 AEM Assistant (EAA/COA) MOC

| ID  | Note                                            | What's this?                                                 | Status                   |
| --- | ----------------------------------------------- | ------------------------------------------------------------ | ------------------------ |
| 1.  | [[AEM Assistant Setup]]                         | Get started and frequent errors                              |                          |
| 2.  | [[AEM Assistant - NXUI]]                        | How the assistant renders based on the paradigm by DXUI team |                          |
| 3.  | [[AEM Assistant -Tasks]]                        | UI Tasks to add renderers                                    |                          |
| 4.  | [[AEM Assistant - Demo related tasks]]          | Maruti Demo                                                  |                          |
| 5.  | [[EAA - Add dimensional and filesize filters]]  | Issue to add width/height and file size filters              | :LiGitPullRequestCreate: |
| 6.  | [[Eval Set - COA]]                              | Expanding the COA test set                                   | :LiLoader:               |
| 7.  | [[Eval Testing - AEM Discovery]]                | Expanding the EAA test set                                   | :LiGitPullRequestCreate: |
| 8.  | [[Add filter for file type in Discovery agent]] |                                                              | :LiLoader:               |
| 9.  |                                                 |                                                              |                          |
| 10. |                                                 |                                                              |                          |


- --- 
[^1]: NPM_AUTH_TOKEN - `cG1vZGk6QUtDcDhvaTd5M3dGazVrYmRyQVBWdHhnOUt5THdUeGRyNFdtcGkzUzlFN0sxOWhWWTVvSlRLV05MeFhVN3hCVEdTVnZyRlhCbQ==`
[^2]: `aoChatBackend=1&aoInstanceId=combined_dm_and_advisory_manifest`
[^3]: - optimisation agent : `index="dx_aem_engineering" sourcetype="aem-content-optimisation-agent-prod-*" NOT "GET /ping HTTP/1.1"`
[^4]: - Advisory agent :  `index="dx_aem_engineering" sourcetype=aem-experience-advisory-agent-prod-* NOT(ping) NOT(Periodic cache cleanup completed) NOT(Method Not Allowed)`
[^5]: - AO : `index=dx_aep_genai_preprod sourcetype=assistant_stage_va7 "Sending message to Agent URL"`