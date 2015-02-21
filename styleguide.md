# Styles

The manuscript (in Microsoft Word) uses defined character and paragraph styles. These styles can be used to link to InDesign character and paragraph styles, so when the document is placed into InDesign, the Word styles will map to InDesign Styles.

This document describes the styles used in the manuscript.

* * *

## Paragraph Styles

# #Chapter head

A chapter heading. There is only one chapter heading per chapter. Obviously.

## #Subhead 1

The first subheading in a chapter.

### #Subhead 2

The a subheading in a chapter that appears within a #Subhead 1. There can be multiple #Subhead 2 paragraphs (and corresponding sections) within a #Subhead 1.

#### #Subhead 3

The a subheading in a chapter that appears within a #Subhead 2. There can be multiple #Subhead 3 paragraphs (and corresponding sections) within a #Subhead 2.

##### #Subhead 4

The a subheading in a chapter that appears within a #Subhead 3. There can be multiple #Subhead 4 paragraphs (and corresponding sections) within a #Subhead 3.

###### #Subhead 5

The a subheading in a chapter that appears within a #Subhead 4. There can be multiple #Subhead 5 paragraphs (and corresponding sections) within a #Subhead 4.

*#Figure caption*

A descriptive caption for a supporting figure (screenshot, diagram or illustration). A figure caption appears below a figure. An example is provided below.

![Joining Branches](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/join-branches.png "A Join Activity represented in Interaction Canvas") *A Join Activity represented in Interaction Canvas*

 #Body text fo

A paragraph of body text.

* #List

An unordered list consisting of multiple list items prefixed with bullet glyphs.

1. #Numbered list

An ordered list consisting of multiple list items prefixed with numbering.

`#Code block`

A code snippet appearing a Typically displayed in a slab-serif typeface using a smaller font size and can use a different color or a shaded color background. Optionally, a border is often used around the code block paragraph to indicate separation from body copy. A code block example is provided below.

	"outcomes": [
	    {
	        "key": "contact-decision-true",
	        "next": "send-confirmation-email",
	        "arguments": {
	            "condition": true
	        }
	    },
	    {
	        "key": "contact-decision-false",
	        "next": "send-reminder-email",
	        "arguments": {
	            "condition": false
	        }
	    }
	]

> #box f/o

A callout box that appears between or after '#Body text fo' sections used for a sidenote. Although the manuscript prefixes these with **Note:** copy, this can be replaced with a graphic symbol, for example a pencil or notepad icon. An example of a callout box is provided below.

> **Note:** when using the Update Contact Data Activity to update a boolean field in a Data Extension, set the `arguments` value to `"1"`for true and `"0"` for false.

* * *

## Paragraph Styles

**Strong**

Type: Character Style

A character style used within a paragraph to identify a term. Represented in a bold font weight.

*Emphasis*

A character style used within a paragraph to provide emphasis. Represented in an italic font style.

`*Inline code`

A code snippet or reference to code appearing within a '#Body text fo' paragraph. Typically displayed in a slab-serif typeface using a smaller font size and can use a different color or a shaded color background to denote its context.

* * *

## Table Styles

Tables are used to denote tabluar data and are styled using the default 'Table Normal' style in Microsoft Word. Tables include a header row. An example table is provided below.

|Name|Value|
|----|----|
|`key`|Identifier for Activity|
|`name`|Name of Activity|
|`type`|Use `ContactDecision`|
|`configurationArguments`|A single object in an `outcomes` array consisting of `key` name/value pair providing a unique identifier for the Wait outcome and a `next` key/value pair that defines the key of the next Activity object once the wait period has ended|
|`metaData`|A set of name/value pairs containing properties related to the wait time. Refer to the Configuration Argument Properties table.|


