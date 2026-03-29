---
created: 2026-01-26
tags:
  - concept
  - AEM
  - jira
JIRA: https://jira.corp.adobe.com/browse/NXUI-484
Participants:
  - ashishc
  - pmodi
  - arora
---
Parent - [[AEM AI Assistant]]
# 1 Background - Clarifications
## 1.1 Current implementation in Experience Advisory Agent (EAA)
As of now, the EAA sends a list of upto 20 assets. This list is in fact, a list of objects, each object containing the asset metadata and a base64 of the asset thumbnail (we send the full base64 because AEM images are protected by access control and require a token in the headers to fetch the content).
![[image.png|263x209]]

## 1.2 Problems with current implementation
The current EAA is quite inefficient
1. We're limited to a short list of 20 assets
2. All 20 assets need to be scrolled to get to the next prompt(and this can extend to 60 assets in total - assets + CFs + forms) ^0c7c4b
3. There's no way to minimize the results
4. Each subsequent "View more" needs to whole new prompt and about 8-10 seconds and does not guarantee no overlap (if the context runs out or is outdated) ^d891d1
5. The full base64 of each thumbnail is sent in the payload

## 1.3 Suggested approach
With [[NXUI-484]] the Next Gen UI team agreed to build a core renderer to display the asset list in collapsed view first and then expand to a full, infinite scrolling view.

> [!NOTE] NOTE
> A core renderer is supposed to be generic enough to be reused by multiple teams. AJO team built a few custom renderers, but the NXUI team eventually found this hard to manage - and discouraged creating too many custom renderers

## 1.4 Clarifications
Pagination is being used for 2 different arguments
1. A paginated API (to solve [[#^d891d1|Problem 4]])
2. Loading new results via a scroll v/s a paginated behavious (to solve [[#^0c7c4b|Problem 3]])
I'll leave the solution for (2) to UX experts (Rebecca) and PMs (Apoorva/Ashish/Ankur) who understand our customer better. For why (1) is not possible at the moment, see [[#2 How does pagination work?]]

# 2 How does a paginated API work?
As rightly stated by @ashishc, 
>"Pagination" pertains to the technique of retrieving content [0] from databases/search-engines/API implementations in (reasonably-sized) batches (trading off larger response-time with larger batch-size).

