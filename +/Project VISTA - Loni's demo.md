---
created: 2026-01-29
tags:
  - AEM
  - concept
---

> [!NOTE] Important links
>[Adobe Express PPT Garage week](https://express.adobe.com/id/urn:aaid:sc:VA6C2:90db9af0-e782-540b-bcef-947227a08905?invite=true&accept=true%3Fpreload%3Dsharesheet&promoid=Z2G1FQKR&mv=other)
> 

# 1 Ankush's plan
1. to enable the flow of uploading multiple audio tracks to video  
2. lets say a creative who wants to add audio asks discovery agent to locate a video
3. discovery agent shows that asset
4. end user says he/she wants to add multiple audio tracks
5. agent (dispatches events for navigation) helps automatically navigate/open up the wizard where multiple audio tracks can be uploaded

# 2 Original Project VISTA Story

1. **UI-Agent handoff:** Agent understands user’s current folder and can create subfolder inside or give a summary of assets or search inside current folder without explicitly telling it the path
2. **Assistive UI:** UI will communicate with agent in the background (unaided by user). So, if u switch to an asset detail page, UI will show a popup of missing metadata. (UI -> (send request to agent on path change) -> agent tells what’s missing -> UI shows popup)
3. **Agent-UI handoff:** let’s say i uploaded a csv to the agent chat, agent can pass on this context to the UI and autopopulate the bulk import form or a bulk metadata edit form.
4. **Micro-UIs:** Based on user prompt, a micro-UI pops up which acts as a form for user to give input. for example - to create renditions of assets in current folder, a micro-UI can show filters for missing renditions and let the user select assets/sort and even preview renditions. This uses genAI to make the UI which can be sometimes not very accurate, but we can give strict UI rules to make it follow our design language.
5. **Adaptive UI:** As the agent learns more about the user, the UI starts to look different for each user. for example, the metadata on each asset card can change, to show number of social renditions for a marketer or flag assets which have publish date very close, or preselect search filters based on activity etc. _this part is hacked right now since we cant store user behvaiour anywhere at the moment._

# 3 Final story
1. lets say a creative who wants to add audio asks discovery agent to locate a video somewhere in the current campaign (folder)
2. discovery agent shows that asset by using UI's info about current path
3. end user says he/she wants to add multiple audio tracks
4. agent (dispatches events for navigation) helps automatically navigate/open up the wizard where multiple audio tracks can be uploaded
5. User uploads some audio tracks and subtitles
6. User now asks if this matches all languages covered in previous campaign?
7. We see missing subtitle for 1 language
8. AI assistant suggests AI-generated captions
9. On confirmation, triggers UI flow to generate new captions
10. after doing it, UI gives a tooltip where user can view and verify the generated caption.
11. User saves