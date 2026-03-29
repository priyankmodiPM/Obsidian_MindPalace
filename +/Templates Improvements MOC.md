| ID  | Title                                                 | Time Estimate | Priority | Links                                                                              | Customer  | Status       |
| --- | ----------------------------------------------------- | ------------- | -------- | ---------------------------------------------------------------------------------- | --------- | ------------ |
| 1.  | [[Handle bars outside canvas]]                        |               |          |                                                                                    | Jet2      | :LiLoader:   |
| 2.  | [[Faster first load]]                                 |               |          | [PR #306](https://github.com/Adobe-Dynamic-Media/assets-dm-templates-mfe/pull/306) | Jet2      | 🟡 PR raised |
| 3.  | [[Segregated properties and layers tab]]              |               |          | [PR 311](https://github.com/Adobe-Dynamic-Media/assets-dm-templates-mfe/pull/311)  |           | 🟢 Done      |
| 4.  | [[Dropdown for fonts in preview]]                     |               |          |                                                                                    | Microsoft |              |
| 5.  | [[MFE for preview]]                                   |               |          |                                                                                    |           |              |
| 6.  | [[Rendering text using DM image]]                     |               |          |                                                                                    | Jet2      |              |
| 7.  | [[Cropping image layers]]                             |               |          | [fabric-cropping-demo](https://github.com/fabricjs/fabric.js/discussions/10487)    |           | :LiLoader:   |
| 8.  | [[Copy paste shortcuts]]                              |               |          |                                                                                    | ITC       | 🟢 Done      |
| 9.  | [[Inkdropper]]                                        |               |          |                                                                                    | ITC       |              |
| 10. | [[Strokes for shapes]]                                |               |          |                                                                                    | ITC       |              |
| 11. | [[Drop-shadows]]                                      |               |          |                                                                                    | ITC, Jet2 |              |
| 12. | [[Blur layers/background]]                            |               |          |                                                                                    | ITC       |              |
| 13. | [[Safe zones]]                                        |               |          |                                                                                    | Jet2      | 🟡 PR raised |
| 14. | [[Lock layer positions]]                              |               |          |                                                                                    | Jet2      |              |
| 15. | [[Navigation between Assets and Dynamic Media Asset]] |               |          |                                                                                    | Everyone  |              |
| 16. | [[Opening editor from recently viewed]]               |               |          |                                                                                    |           |              |
| 17. | [[Italic hack on font where italics is not enabled]]  |               |          |                                                                                    | Jet2      |              |
| 18. | [[spectrum s2 icons]]                                 |               |          |                                                                                    |           | 🟢 Done      |
| 19. | [[multiple layer controls]]                           |               |          | [PR #340](https://github.com/Adobe-Dynamic-Media/assets-dm-templates-mfe/pull/340) |           | 🟡 PR raised |
| 20. | Replace Image                                         |               |          |                                                                                    |           |              |
| 21. | CF Connector                                          |               |          |                                                                                    |           | 🟡 PR raised |
Also see [[Template Editor improvements]]

1. Create ITC template
	1. [x] Created via DMC upload
	2. [x] Create manually 1/2
	3. [x] Try reflow
2. [x] Setup Splunk alert - TEST - DID NOT WORK
3. [ ] Optimization - [Reflow JIRA](https://jira.corp.adobe.com/browse/ASSETS-63238)
	1. [ ] Variant options tray (missing image layer in thumbnail)
	2. [ ] TopicCard does not render thumbnail on creating new variant
	3. [x] Missing source variant
	4. [ ] IRSA setup
	5. [x] When VariantOptions is mounted with 1 option, it keeps showing 1
	6. [ ] Only load variants after APP_LOAD is false
4. [x] Setup splunk and on-call for aesthetiq
5. [x] Talk to Piyush about on-call queue
	1. [ ] merge with openapi
	2. [ ] create runbooks
	3. [ ] add Rishabh as secondary contact

### 0.1.1 Feb 13-15
1. [x] Check commit history to see if sync s3 upload is still called
	1. [x] It never was, i had made preview test to async
2. [x] Share all 6 payloads with MDSR
3. [x] Check all errors are added to logs in reflow service
4. [x] Check translation error - fix
5. [x] Setup alerts for timeout/translate/rule-based
6. [ ] Try new aesthetiq v3 model
7. [ ] Faster first load
8. [x] Make scripts for P10/P50/P95 for reflow service and aesthetiq
9. [ ] Figure out splunk for aesthetiq
10. [x] Check stress test script
11. [x] Check stress test of flex service (upto 4 requests) matches timing and logs of aesthetiq
12. [ ] Use uvicorn pipeline debug - [ChatGPT](https://chatgpt.com/share/e/698f8b4b-715c-8011-8565-4acb144ef2e1)
13. [ ] 

13. [ ] Dashboard for likes/dislikes
14. [ ] Tight bounding box for text layers