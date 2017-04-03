# Azure Portal Presentation Mode
APPM is a Chrome extension that strips sensitive information from the new Microsoft Azure portal (https://portal.azure.com). This is most useful for individuals doing public presentations or videos on material associated with the portal who do not wish to disclose private details about their subscription or resources.

The following data is intended to be stripped from the portal as of 4/3/2017:
- Subscription IDs from resource pages
- Resource IDs from resource pages
- Tooltip in user header that discloses Directory ID
- Username from user header

Additional data can be stripped by adding a mutation to content.js in the following style:

```javascript
{
	name: "Some Descriptive Name of What This Does",
	selectorString: "string evaluating to a jquery selector pointing to the element that is watched for changes and subsequently passed into the callback",
	observes: {attributes: true, childList:true, characterData:true, subtree:true}, // Pick any subset of these as configuration to the MutationObserver. Chrome follows W3 standard for MutationObservers, which can be found at https://www.w3.org/TR/dom/#mutation-observers
	callback: function(selector) { selector.hide(); } // Perform mutation here, the selector will be the result of selectorString, above
},
```

If you add additional data and create a PR, please include the new functionality in this README.
