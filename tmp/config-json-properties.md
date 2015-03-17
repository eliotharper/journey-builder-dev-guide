|Property|Type|Required|Description|
|----|----|----|----|----|
|`workflowApiVersion`|string|yes|The workflow API version; either`0.5` or `1.0` (only use `0.5` for legacy Custom Activities).
|`metaData.version`|string|no|An assigned iterative version number for the Custom Activity.|
|`metaData.icon`|string|yes|The relative path to the Custom Activity icon.|
|`metaData.iconSmall`|string|yes|The relative path to the Custom Activity small icon.|
|`type`|String|yes|Use `REST` for Custom Activities or Custom Split Activities.|
|`outcomes`|array|no|An array of `arguments` objects and `metaData.label` values for Custom Split Activities.|
|`lang`|object|yes|Name and description values of the Custom Activity using within an ISO 639x language tag object, optionally includes branch labels.|
|`outcomeLabelLanguageMap`|object|no|Used in Custom Split Activities to map `outcomes.arguments.branchResult` values to keys in `lang` language tag objects.|
|`userInterfaces`|object|no|Interfaces used as a hover element and a  'More Details' modal dialog for Custom Activities in a running Interaction.|
|`arguments.execute.inArguments`|array|no|Name/value pairs sent in a POST request to the Custom Activity `execute` endpoint url.|
|`arguments.execute.outArguments`|array|no|Outcome name/value pairs from the Custom Activity, available to subsequent Activities in the Interaction.|
|`arguments.execute.url`|string|yes|Request Endpoint URL used by Journey Builder when the Activity is executed.|
|`arguments.execute.verb`|string|no|The HTTP method used for the `url` request.|
|`arguments.execute.body`|string|yes|This field is retained for backward compatibility. Use `""` value.|
|`arguments.execute.header`|string|no|Headers used for the `url` request.|
|`arguments.execute.format`|string|yes|Use `json`. Other formats are not supported at this time.|
|`arguments.execute.useJwt`|string|yes|If set to set to `true` then a JSON Web Token for the account is generated, encoded and sent in as the "jwt" property in the POST body.|
|`arguments.execute.timeout`|string|yes|Timeout value for callback in milliseconds.|
|`configurationArguments.`<br />`applicationExtensionKey`|string|yes|The Custom Activity Key defined when creating Journey Builder Activities in App Center.|
|`configurationArguments.`<br />`defaults`|object|no|Default name/value pairs used in the Custom Activity interface.|
|`configurationArguments.save`|object|yes|Parameters used by Journey Builder to make a REST request to the Custom Activity when the Interaction is saved.|
|`configurationArguments.publish`|object|yes|Parameters used by Journey Builder to make a REST request to the Custom Activity when the Interaction is published.|
|`configurationArguments.validate`|object|yes|Parameters used by Journey Builder to make a REST request to the Custom Activity when the Interaction is validated.|
|`edit.url`|string|yes|The configurable interface endpoint for the Custom Activity displayed in the Interaction Canvas (within an iframe).|
|`edit.height`|string|yes|The iframe height for the configurable interface.|
|`edit.width`|string|yes|The iframe width for the configurable interface.|