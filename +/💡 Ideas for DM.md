
1. [ ] Personalisation/templates must have insights after A/B testing or knowing what to promote and what to leave behind
	1. Combine with target
	2. Bring in analytics inside the editor in some way?
2. [ ] 1:1 email personalization with AJO. 
	1. a custom model determines AJO layout
	2. a query is generated for each customer that is given to the LLM to generate text content
	3. recommendation system can split customers into groups/segments based on usage and other attributes - can even make n*2 groups for A/B testing
	4. DM makes a different banner for each user and replaces customer assets in layout at delivery
	5. Author approves the different banner styles and captions for different sections
	6. AJO delivers a new email to everyone. Get back clickthrough stats. Test a new strategy for customers
3. [ ] Automatically determine colours of your layered image:
	1. https://graphicdesign.stackexchange.com/questions/56010/how-to-select-a-font-color-to-go-on-a-very-busy-background
	2. The glow effect is created by repeating the text multiple times with different shadow offsets and intensities:
	- `\shad`: Enables shadowing
	- `\shadx` and `\shady`: Set the horizontal and vertical offset of the shadow
	- `\shadr` and `\shado`: Set the intensity of the shadow (0-255, where 255 is most intense)
	- `\cf2`: Sets the text color to orange (color 2)
	- {\rtf1\ansi\deff0 {\fonttbl{\f0\fswiss\fcharset0 Arial;}} {\colortbl ;\red255\green255\blue255;\red255\green165\blue0;} \viewkind4\uc1\pard\cf1\f0\fs40 {\shad\shadx60\shady-60\shadr238\shado238 \cf2 Glowing Text} {\shad\shadx120\shady-120\shadr221\shado221 \cf2 Glowing Text} {\shad\shadx180\shady-180\shadr204\shado204 \cf2 Glowing Text} {\shad\shadx240\shady-240\shadr187\shado187 \cf2 Glowing Text} }
	- Aesthetic scorer: https://adobe.brightidea.com/D9408
4. [x] Reflow models:
	1. https://adobe.brightidea.com/D21253
5. [ ] Image to PSD: 
	1. https://adobe.brightidea.com/D54521?idea_count=2059
6. [ ] Brand guidelines: 
	1. Image color harmonization: https://adobe.brightidea.com/D54453?idea_count=2059
7. [ ] Image serving modifiers:
	1. [ ] trim white spaces
	2. [ ] autoClip using background removal
	3. [ ] round corners
8. [x] Smarter Crop
	1. Intent based crop - example Levis, crop the eye line and waist
9. [ ] Automatically test the template and flag things (and suggest fixes) that can go wrong while creating variations. For example:
	1. [ ] Using text of varying lengths
	2. [ ] Using images of different aspect ratios
	3. [ ] quality related checks
10. [ ] Fix lighting - harmonize - using a dm modifier with some photoshop harmonize function
11. [ ] Allow easy imports
12. [ ] 

# 1 Nov 2025
https://adobe.brightidea.com/D64772

1. [ ] Auto-generate user specific demos using existing AEM technologies.
	1. [ ] Source content 
	2. [ ] Make new pages 
	3. [ ] Show DM features
	4. [ ] A “Competitive Radar” agent
		1. [ ] Tracks competitors’ releases, pricing shifts, hiring trends
		2. [ ] Detects positioning changes by semantic analysis of web + ads
		3. [ ] Alerts PMM with recommended response messaging
		4. [ ] Auto-generates battlecards, updated daily
2. [ ] OCR-search from images
3. [ ] (Check bynder AI services)
4. [ ] (ITC personalisation - facial recognition - UGC)
5. [ ] Geo tagging on image upload
6. [ ] An agent that works along with the UI
7. [ ] (see what's latest in the agent market)

# 2 Feb 2026
1. The localization use case with Content Hub is interesting. There should be a way for brands to define brand guidelines and let the vendors make small edits to the documents, with the AI making sure all the guidelines are followed, and only then allowing downloads. There might be a manual approval as well, but the brand should see the brand score and make the approval process very quick. Very much like express has the safe zones and locked layers, we can allow editing only in specific zones as well.
2. CF Integration with DM Templates - Create a DB that requires manual sync. DM reads from this and creates the URL instead of creating one at delivery time. We can also create presets in DM to achieve this
3. Templates - new PS based rendering engine. Dont use existing rendering, make a new route that calls pie-wasm to render the image
4. Charts using templates. template does logical analysis and updates content