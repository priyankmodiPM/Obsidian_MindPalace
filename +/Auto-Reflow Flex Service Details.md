

> [!NOTE] Important Links
> Flex service: https://devhome.corp.adobe.com/catalog/default/component/SRID_578134
> GPT Key - 8ZHUKAs28RIAbZDbMNA52GXOhTaWb0S8l1FxZeJT9zOVBfrvhgkNJQQJ99BBACYeBjFXJ3w3AAABACOGeWrX
>

# 1 API Routes

| Route            | GET                | POST               |
| :--------------- | ------------------ | ------------------ |
| /ping            | :LiCircleCheckBig: |                    |
| /generateVariant |                    | :LiCircleCheckBig: |
| /brandGuidelines | :LiCircleCheckBig: | :LiCircleCheckBig: |
| /feedback        | :LiCircleCheckBig: | :LiCircleCheckBig: |
| /history         | :LiCircleCheckBig: |                    |
| /authenticate    |                    | :LiCircleCheckBig: |


Links to play with later - 
1. https://experience.adobe.com/?repoId=author-p138017-e1441390.adobeaemcloud.com#/@skylineprodtest017/assets/browse
2. https://experience-stage.adobe.com/?features=ASSETS-43582-DM-Template-MFE-AutoLayout&CQ-assets-dm-templates-mfe_version=PR-266-346930d8a57ca606d2496f0a125a4e8314292d3f&repoId=author-p90772-e330464-cmstg.adobeaemcloud.com#/@aem-cloud-demos/assets/dm/templateeditor/content/dam/ModelTesting/AestheticQ/Frescopa_Banner
3. MDSR Service (search aesthetiq) - https://devhome.corp.adobe.com/catalog/default/Component/SRID_527515/flex?repository=firefly%2Fcolligo-deploy
4. [[Ethos Resources]] - Container images - https://devhome.corp.adobe.com/catalog/container-images

## 1.1 /generateVariant

1. `params`: 
	1. source_variant - #JSON
	2. original_width - #float
	3. original_height - #float
	4. requested_width - #float
	5. requested_height - #float
	6. source_language - #string
	7. requested_language - #string
	8. template_json - #JSON
	9. token - #string
2. `prompt for generating base code` - i want to add a generateVariant route which does the following:
	1. kicks off the 2 parallel workflows for translation and layout change
		1. create 2 abstract classes for different models that will implement translation and layout
		2. create 1 class that implements translation, use minimum mocking for this right now
		3. create 1 class that implements layout change, call this aestheticq
	2. translation function returns the output of translation (a map of layerId and new translated string)
	3. layout function returns a template json
	4. the outputs of translation and layout change are passed to a composition function that returns a new template json which is the response to the api call
3. `AWS Translate`
	1. vault path for aws key - `secret/s7/dmgateway-vaults/dmgateway5-prod`
	2. Correct vault path (not sure where prrevios one came from) - `secret/s7/cloudstack/iam_creds/preprod/dm_template_mc_user` (added this line on 13 Feb)
	3. key - `APAC_PROD_AWS_ACCESSKEY`
	4. vault usage - 
	5. Working vault url - https://vault-amer.adobe.net/ui/vault/secrets/secret/list/s7/
4. `IMS auth`
5. `Logging`
6. AestheticQ service (find IPs here) - https://devhome.corp.adobe.com/catalog/default/resource/ethos503-stage-va6/network-peering
	1. 34.230.194.3
	2. 34.205.176.170
	3. 34.230.137.15
7. https://experience-stage.adobe.com/?CQ-assets-dm-templates-mfe_version=PR-266-346930d8a57ca606d2496f0a125a4e8314292d3f&repoId=author-p90772-e330464-cmstg.adobeaemcloud.com#/@aem-cloud-demos/assets/dm/templateeditor/content/dam/ModelTesting/AestheticQ/Frescopa_Banner
8. Auto-reflow Flex service IPs
	1. 54.225.246.239
	2. 184.73.155.132
	3. 34.192.160.31
	4. 130.248.113.29 (this is my local ip on vpn)

# 2 Logging in to the server - kubectl
1. `kubectl config set-context --current --namespace=ns-team-cq--dynamicmedia-autoreflow-deploy--d5d50d33--27dbed8d`
2. `kubectl -n ns-team-cq--dynamicmedia-autoreflow-deploy--d5d50d33--27dbed8d get pods`
3. `kubectl exec -it cq--dynamicmedia-autoreflow-dev-deploy1-6b466d556-jmlcd -- /bin/bash`

# 3 Closest match aspect ratios

1. 1000x1500  -  2:3
2. 1080x1080  -  1:1
3. 1280x720    -   16:9
4. 1920x1080  -   16:9
5. 2000x1000  -   2:1
6. 3000x1000  -   3:1

Jet2
1. Paths
	1. Path1 - `content/dam/jet2/creative/dynamicmediafolder/25-02-0302%20Save%20On%20Summer`
2. Aspect ratios - 
	1. 1200 x 628, 728 x 90, 640 x 400, 975 x 370, 840 x 370, 590 x 246
	2. 2:1,                     7:1,           3:2,               3:1,             2:1,              2:1
3. Aspect ratios tried on Black Friday campaign with text
	1. 400x200, 1488x906, 2210x500, 840x370, 1486x600, 575x393, 975x370, 450x250
	2. 2:1,                  3:2,           4:1,              2:1,           2:1,             3:2,            5:2            2:1

4. **Web**
	2210 x 500
	2048 x 1536
	2000 x 610
	1488 x 906
	1486 x 600
	1024 x 530
	975 x 370 hmpg
	840 x 370 hmpg
	813 x 375
	768 x 530
	590 x 246 
	575 x 395 hmpg
	450 x 250
	590 x 246

5. **Social**
	820 x 360
	
6. **LED screens**
	1920 x 1080 Logo

7. **Email**
	640 x 400

8. **BOH Screens**
	1920 x 500

9. **Other**
	600 x 300
	750 x 350

Steve
1. Aspect ratios -
	1. 625x1253, 1000x1000, 625x1000, 1730x518, 626x522
	2. 1:2,                    1:1,                5:8,            3:1,            5:4