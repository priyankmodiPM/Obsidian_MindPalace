# 1 Handle bars outside canvas
A good resource - [Ability to grab handles of elements at the edge of the canvas · Issue #5334 · fabricjs/fabric.js](https://github.com/fabricjs/fabric.js/issues/5334)

An example using the described approach - [Create Photo Editor and Graphic Design Maker | Shutterstock](https://www.shutterstock.com/create/editor)


# 2 Faster loading
## 2.1 Load only required fonts
Instead of loading all the fonts, we should first load fonts that are used in current canvas. only then should we load remaining fonts in the backgroud (non-blocking)

[PR #296](https://github.com/Adobe-Dynamic-Media/assets-dm-templates-mfe/pull/296/changes)

## 2.2 Load layers in parallel
Right now, all layers load synchronously. This is not required, especially becomes slow when there are multiple image layers, and each makes a fetch request taking time.

[PR #306](https://github.com/Adobe-Dynamic-Media/assets-dm-templates-mfe/pull/306)
