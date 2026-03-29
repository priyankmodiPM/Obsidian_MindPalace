> [!NOTE] Important Links
> - Setup - [[https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=MKTOENG&title=Full+stack+dev+for+ao-reasoning+engine#Fullstackdevforaoreasoningengine-3.InyourAdobe-dx-agent-uirepo]]
> - Advisory agent - https://github.com/AEM-Assets-Adobe/aem-experience-advisory-agent
> - NPM_AUTH_TOKEN - cG1vZGk6QUtDcDhvaTd5M3dGazVrYmRyQVBWdHhnOUt5THdUeGRyNFdtcGkzUzlFN0sxOWhWWTVvSlRLV05MeFhVN3hCVEdTVnZyRlhCbQ==
> - Query params for DM manifest = ?aoChatBackend=1&aoInstanceId=combined_dm_and_advisory_manifest
> - A great guide to understanding the various repositories - https://github.com/Adobe-dxue/Adobe-dx-agent-registry/blob/4ad635b2f76aaa98dc211bf348080226302a7531/CONTRIBUTING.md
> - 
> 
# 1 Setup
| Setup                                                   | Status         |
| :------------------------------------------------------ | -------------- |
| Clone all repos                                         | ✅ Done         |
| Close Advisory agent                                    | ✅ Done         |
| Run advisory agent on 8082                              | ✅ Done         |
| Run ao-reasoning service                                | ✅ Done         |
| Get NPM_AUTH_TOKEN                                      | ✅ Done         |
| ao-reasoning-service                                    | Running (8079) |
| Copied the agent.yamls and manifest from Ritwit's chats | ✅ Done         |
| copilot-engine                                          | Running (8000) |
| gandalf                                                 | Running (8080) |
| Adobe-dx-ui                                             | Running (8013) |
| advisory-agent                                          | Running (8083) |
| optimizer-agent                                         | Running (8082) |
- For running UI - cursor did some `yarn create-version`
- UI runs at - https://experience-stage.adobe.com/?devMode=true&shell_source=dev&shell_devmode=true#/@aem-cloud-demos/ai-assistant/chat?aoChatBackend=1&aoInstanceId=combined_dm_and_advisory_manifest
- Manifest1 - `combined_dm_and_advisory_manifest`
- Manifest - `aem_agent_advisory_and_optimization_manifest`
- ao-reasoning-engine - `export AO_REASONING_ENGINE_SERVICE_PORT=8079 && make server`
- aem-experience-advisory-agent - `./local-setup.sh`
- aep-copilot-engine - `make run-engine`
- aep-gandalf-api - `docker compose up`
- Adobe-dx-agent-ui - `yarn start`
- Run `localStorage.setItem('DXAgentUI.useLocalhost', true);` in assistant browser console
- Prompt - `create instagram renditon for this image. assetid= urn:aaid:aem:f612ada3-6458-4f55-aa3f-32e5471ee9ce , assetName=AdobeStock_615752154_Preview.jpeg , delivery domain=delivery-p102255-e237034-cmstg.adobeaemcloud.com`

## 1.1 SETUP related learnings - #AEM/DM-Concept 
1. The UI decides which manifest to talk to using the query params
2. The reasoning engine communicates with the agents. Make sure the copilot-engine knows to talk to the orchestrator (reasoning engine) on the right port on your local, or the stage URL if required
3. Run the agent on your local, change the url in the manifest and check the logs of the agent repo to make sure the call reaches the respective agent and how it responds
4. If you see this error: `Access denied due to invalid subscription key or wrong API endpoint. Make sure to provide a valid key for an active subscription and use a correct regional API endpoint for your resource.` Make sure environment variables are set. Check README of advisory-agent.
```
export AZURE_OPENAI_ENDPOINT="https://contenthub-aithiru.openai.azure.com/"
export AZURE_OPENAI_DEPLOYMENT="gpt-4.1"
export AZURE_OPENAI_MODEL_VERSION="2025-01-01-preview"
export AZURE_OPENAI_API_KEY="BGkaVLEP00hyXO20knmR5g31GQYGmpXJUalvmG6doGpbkY2YGTKlJQQJ99BHACHYHv6XJ3w3AAABACOGe3aI"
export ARTIFACTORY_UW2_API_TOKEN="cmVmdGtuOjAxOjE4MDEyODQ5OTQ6QnFBN3RVMjF5cGpUczhiaXNHeXpESk8zalRY"
```

