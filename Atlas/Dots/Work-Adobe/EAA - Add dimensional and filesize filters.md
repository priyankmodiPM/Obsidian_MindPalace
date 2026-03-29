---
created: 2026-01-15
JIRA: https://jira.corp.adobe.com/browse/AEMAGT-206
tags:
  - work
  - jira
status: CODE-COMPLETE
git: https://github.com/AEM-Assets-Adobe/aem-experience-advisory-agent/pull/229/changes
---
*Description*: Scope: to support promtps like - "Gives assets >2MB " or "images with width/height < 2000" in Discovery agent

---

> [!NOTE] Important links
> 1. api=search?path=%2Fcontent%2Fdam&assetType=file&limit=50&**property=repo:createDate%3E=2025-12-01T00:00:00.000Z**
> 2. api=search?path=%2Fcontent%2Fdam&assetType=file&limit=50&**property=tiff:imageWidth>=1500&property=tiff:imageWidth<=3000**&property=repo:createDate%3E=2025-12-01T00:00:00.000Z
> 3. [AEM Query builder with sample query](https://author-p102255-e237034-cmstg.adobeaemcloud.com/libs/cq/search/content/querydebug.html?_charset_=UTF-8&query=type%3Ddam%3AAsset%0D%0Apath%3D%2Fcontent%2Fdam%0D%0Ap.limit%3D50%0D%0Ap.offset%3D0%0D%0Ap.hits%3Dselective%0D%0Ap.properties%3Djcr%3Auuid+jcr%3Apath+%0D%0Afulltext%3D%3F%7B%7D%3Fpremium%0D%0Ap.guessTotal%3Dtrue) - #AEM/DM-Concept
> 4. [AEM Query documentation](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/platform/query-builder/querybuilder-predicate-reference#property) - #AEM/DM-Concept #Documentation
> 5. Note that ***Portrait/landscape*** also works with ***tag based search***

> Related threads
> 	1. [Slack | Query builder doubt](https://adobedx.slack.com/archives/C09F2NDP6TE/p1768491127440699)
> 		1. `property` and `rangeproperty` should be used judiciously - #AEM/DM-Concept 
> 		2. oak index can be seen using `/oak:index/damAssetLucene-13` - #AEM/DM-Concept 
> 	2. [Slack | Clarifying questions](https://cq-dev.slack.com/archives/D048PFWDWF7/p1768543794690399)
> 		1. asking clarifying questions is part of the a2a protocol which ao-sdk supports.  For every task in a2a, `input-required` state is returned back to the client which lets it know that a clarifying question needs to be asked. [https://agent2agent.info/docs/concepts/task/](https://agent2agent.info/docs/concepts/task/) - #AEM/DM-Concept 
> 		2. code reference in advisory agent : [https://github.com/AEM-Assets-Adobe/aem-experience-advisory-agent/blob/main/src/content_advisor/agent_executor.py#L716-L719](https://github.com/AEM-Assets-Adobe/aem-experience-advisory-agent/blob/main/src/content_advisor/agent_executor.py#L716-L719) - #AEM/DM-Concept 

## 0.1 Checklist Tasks
1. [x] Simple prompts like exact match width, height
2. [x] Prompts with maths
3. [ ] Prompts with keyword for width/height - portrait/landscape/wider etc.
4. [x] Add a #TODO note to add validations in the code - min width > max width etc.
5. [x] Sort based on dimension/file size
6. [x] Add a #TODO to Ask clarifying questions in case of invalid ranges/validation failures?
7. [ ] Create backlog JIRAs for invalid width/height/filesize prompts to throw clarifying question
8. [ ] Create CQDOC JIRA for videos/docs with specific width/height? - #TODO

---
# 1 Approach
1. [x] Get the agent to parse the search strings related to file size or dimensions as filters
2. [x] Pass the filters and generate a search string in the right format
3. [x] Verify results
4. [x] Add test cases
5. [x] Support sorting

# 2 Questions
1. [ ] What happens if width/height is applied to asset which does not have width/height?
2. [ ] What happens if width > 100 & wid < 10?
3. [ ] how to get width > height to work?
4. [ ] Can we sort  based on 2 predicates?

# 3 Tested prompts
1. get me images 1500 pixel height
2. get me images 2000 pixel wide
3. get me images with width between 400 and 500 pixels
4. find images with width/height < 500 and > 450
5. find images smaller than 1.7KB and >1.5KB
6. ***find images 1.69KB in size*** - #PASSED
7. ***find product packaging PNG images with minimum width*** -  #FAILED

I also added eval prompts for range queries on metadata properties as discussed in [[Eval Testing - AEM Discovery]]

# 4 Limitations
1. No logical operators allowed at the moment. Width is between 1200-1400 OR between 1800-2000. Same limitation exists for other types as well
2. No error propagation in case of invalid filters