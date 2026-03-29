---
created: 2026-01-12
JIRA: https://jira.corp.adobe.com/browse/AEMAGT-256
tags:
  - work
  - jira
status: IN-PROGRESS
---
Description: 

> [!NOTE] Important links
> [Ritwik's implementation of a custom metric](https://github.com/AEM-Assets-Adobe/aem-content-optimisation-agent/blob/main/evaluation/eval/test_utils.py#L36-L259)
> [Current test set for COA](https://git.corp.adobe.com/experience-platform/ao-evals/blob/main/datasets/operator/content_optimization_agent/benchmark.quality.v0.json)

> Related threads
> 	1. [Varun's Slack message](https://cq-dev.slack.com/archives/D048PFWDWF7/p1767943293193379)
> 		1. So, my goal is to do an evaluation run on coa in order to be able to evaluate the agent for different models and different prompts. 
> 		2. I am currently looking into creating a **custom metric** for evaluation the DMwOAPI url

## Checklist Tasks
1. [ ] Define a plan for COA evals
	1. [ ] What does COA do?
	2. [ ] What should a COA do?

# Approach

#### Theme A — Basic Transformation Correctness (Foundational)
1. “Resize this image to 800×600.”
2. “Crop the image to a square from the center.”
3. “Reduce image quality to make it lighter for web.”
4. “Convert this image to WebP format.”

	Eval strategy - *Exact / structural match*
	Validate:
		Correct DM parameters present
		No unnecessary transforms added
		Output is a valid DM URL / transformation object
#### Theme B — Smart Cropping & Framing (AI-assisted DM)
1. “Create a square thumbnail that keeps the main subject visible.”
2. “Crop this for Instagram without cutting off faces.”
3. “Generate a banner crop optimized for hero images.”

	Eval strategy - *Semantic + structural*
	Validate:
		- Use of smart crop / focal preservation
		- Aspect ratio correctness
		- No destructive assumptions (e.g., hard-coded crop)
#### Theme C — Channel / Context-Aware Optimization
1. “Optimize this image for a mobile product listing.”
2. “Prepare this image for email—keep file size under 200 KB.”
3. “Create a version suitable for a homepage hero banner.”

	Eval strategy - *Partial match + heuristic thresholds*
	Validate:
		- Appropriate resolution choices
		- Compression strategy
		- Aspect ratio aligned to channel norms
		- No over-optimization (e.g., excessive blur)
#### Theme D — Multi-Transformation Composition
1. “Crop to 16:9, resize to 1920×1080, and compress for fast loading.”
2. “Make a square thumbnail and convert it to WebP.”
3. “Resize for mobile and slightly sharpen the image.”

	Eval strategy - *Structural + order-aware*
	Validate:
		- All requested transforms applied
		- No conflicting params
		- Reasonable ordering (crop → resize → format/compress)

