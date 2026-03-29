---
created: 2026-01-27
JIRA: https://jira.corp.adobe.com/browse/AEMAGT-219
tags:
  - work
  - jira
status: IN-PROGRESS
---
Parent - [[AEM AI Assistant]]

Description: 

> [!NOTE] Important links
> [Word doc with images of issue](https://adobe-my.sharepoint.com/:w:/p/apogupta/EbNyvVn2lkZAnwd1V8rQbsEBOUCGFqL3chw8y3drt9-I9A?e=mE9CwE "Follow link")
> 
> 

> Related threads
	1. [Slack thread with Apoorva's description](https://cq-dev.slack.com/archives/C09L7B53UQH/p1768461269983969)
	2. 

## 0.1 Checklist Tasks
1. [ ] Task1

When we set file type filter to documents, the search query is - https://author-p121852-e1208960.adobeaemcloud.com/adobe/repository/;t=1769;api=search?path=%2Fcontent%2Fdam&assetType=file&limit=50&type=text/*,application/*&embed=http://ns.adobe.com/adobecloud/rel/ac/effective,http://ns.adobe.com/adobecloud/rel/metadata/asset

When multiple file formats are defined in the filters, the search query is - https://author-p121852-e1208960.adobeaemcloud.com/adobe/repository/;t=1769;api=search?path=%2Fcontent%2Fdam&assetType=file&limit=50&property=dc:format==application/xml,application/x-font-ttf&embed=http://ns.adobe.com/adobecloud/rel/ac/effective,http://ns.adobe.com/adobecloud/rel/metadata/asset

# 1 Challenges
**The Problem:** It is hard, might even be impossible, to get an exhaustive list of all mime-types supported by AEM (for new formats it is picked from the asset extension or metadata). The only resource I could find which has some formats listed is [here](https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=cloudservices&title=Media+Type+supported+by+ReS)  
**How Assets View provides the filters:** On first load, Assets view makes a search call, and populates the available filters in that AEM environment in the UI.  
**Possible approaches:**  
1. Add a full list of all mimetypes, to the best of our ability in the `agent context` and map it to the NLP file format - like application/vnd.adobe.photoshop for PSD or Photoshop file. Then add _dc:format=_ filters for all mimetypes that match user prompt.
2. Make a `search call, fetch all the mimetypes in user's AEM` environment, then ask the agent to pick the mimetypes it feels best matches the user prompt. _I dont know if this returns all the asset mimetypes though, will need to confirm this._
3. Some way of filtering smartly? like `*zip*` or `*photoshop*` or `*psd*` ? Not sure how extensive this is.

# 2 Prompts and responses in current build
1. find spreadsheets - ❌ also gave pdf, epub, jpeg
2. find csv files - ✅ this worked
3. find mkv files - ❌ gave jpg only
4. find heic images - ❌ gave jpg only
5. find assets with text content, json, xmls - ❌ gave no result
6. i need adobe design documents from cc apps - ✅ this worked, gave indd, psd, ai files and some jpg with adobe content
7. 

### 2.1.1 ###