# Style Guide

## Contents

* [Introduction](#introduction)
* [Paragraph Styles](#paragraph-styles)
** [#Subhead 1](#subhead-1)
** [#Subhead 2](#subhead-2)
** [#Subhead 3](#subhead-3)
** [#Subhead 4](#subhead-4)
** [#Subhead 5](#subhead-5)
** [#Figure caption](#figure-caption)
** [#Body text fo](#body-text-fo)
** [#List](#list)
** [#Numbered list](#numbered-list)
** [#Code block](#code-block)
** [#box f/o](#box-fo)
* [Character Styles](#character-styles)
** [Strong](#strong)
** [Emphasis](#emphasis)
** [*Inline code](#inline-code)
* [Table Styles](#table-styles)

* * *

## Introduction

The book manuscript (supplied as a Microsoft Word document) uses pre-defined character and paragraph styles.

These styles can be used to link to InDesign character and paragraph styles, so when the document is placed into InDesign, the Word styles will map to InDesign Styles.

This document describes the styles used throughout the manuscript.

* * *

## Paragraph Styles

# #Chapter head

A chapter heading. There is only one chapter heading per chapter. Obviously.

## #Subhead 1

The first subheading in a chapter.

### #Subhead 2

The a subheading in a chapter that appears within a #Subhead 1 section. There can be multiple #Subhead 2 paragraphs (and corresponding sections) within a #Subhead 1.

#### #Subhead 3

The a subheading in a chapter that appears within a #Subhead 2 section. There can be multiple #Subhead 3 paragraphs (and corresponding sections) within a #Subhead 2.

##### #Subhead 4

The a subheading in a chapter that appears within a #Subhead 3 section. There can be multiple #Subhead 4 paragraphs (and corresponding sections) within a #Subhead 3.

###### #Subhead 5

The a subheading in a chapter that appears within a #Subhead 4 section. There can be multiple #Subhead 5 paragraphs (and corresponding sections) within a #Subhead 4.

<a name="figure-caption">*#Figure caption*</a>

A descriptive caption for a supporting figure (screenshot, diagram or illustration). A figure caption appears below a figure. Refer to example below.

![Joining Branches](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/join-branches.png "A Join Activity represented in Interaction Canvas") *A Join Activity represented in Interaction Canvas*

<a name="body-text-fo">#Body text fo</a>

A paragraph of body text. Refer to example below:

Journey Builder Interactions are structured workflows that use a series of hierarchical elements similar to XML, where a single root element (an Interaction) contains child elements (Interaction Components) that cascade from the root element as parent-child relationships. Another way of representing an Interaction would be a tree model, consisting of one trunk (an Interaction) with branches to Interaction Components. These branches can split to form other branches.

### #List

An unordered list consisting of multiple list items prefixed with bullet glyphs. Refer to example below.

* **Draft** state is used when initially defining an Interaction in the Interaction Plan Canvas before it is saved. Interactions in this state cannot receive incoming events. Only one draft version of an Interaction can exist at a time.
* **Saved** state is applied to an Interaction once it has been saved. Interactions in this state cannot receive incoming events.
* **Publishing** state is a temporary state that applies to an Interaction Version while it is being activated. When an Interaction version is published, each Interaction Component in the version is evaluated to check that the Activities are valid for publishing. The evaluation process is described below.
* **Running** state applies to Interactions after they have been validated successfully during the publishing state.
* **Stopped** state refers to a published or running state of an Interaction that has been stopped. When an Interaction is changed to a stopped state, it will not accept any further incoming Events. Contacts are ejected from all versions in an Interaction when it is stopped.

### #Numbered list

An ordered list consisting of multiple list items prefixed with numbering. Refer to example below.

1. The Interaction Trigger is configured
2. Activities are configured
3. Goals, if included, are configured
4. The Interaction is named.

### #Code block

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

### #box f/o

A callout box that appears between or after '#Body text fo' sections used for a sidenote. Although the manuscript prefixes these with '**Note:**', this can be replaced with a graphic symbol, for example a pencil or notepad icon. Optionally, a border is often used around a callout box to indicate separation from body copy.

> **Note:** when using the Update Contact Data Activity to update a boolean field in a Data Extension, set the `arguments` value to `"1"`for true and `"0"` for false.

* * *

## Character Styles

<a name="strong">**Strong**</a>

A character style used within a paragraph to identify a term. Represented in a bold font weight.

<a name="emphasis">*Emphasis*</a>

A character style used within a paragraph to provide emphasis. Represented in an italic font style.

<a name="inline-code">`*Inline code`</a>

A code snippet or reference to code appearing within a '#Body text fo' paragraph. Typically displayed in a slab-serif typeface using a smaller font size and can use a different color or a shaded color background to denote its context. Refer to example below.

In WDF, an `entryMode` name/value pair is used in the Interaction Object with a value `MultipleEntries` or `SingleEntryAcrossAllVersions`. If an `entryMode` is not defined in the Interaction Object, then the Interaction will use `SingleEntryAcrossAllVersions` by default. An example Interaction defining an `entryMode` is provided below.

* * *

## Table Styles

Tables are used to denote tabluar data and are styled using the default 'Table Normal' style in Microsoft Word. Tables include a header row. Optionally zebra stripes are used in table rows to improve readability. An example table is provided below.

|Name|Value|
|----|----|
|`key`|Identifier for Activity|
|`name`|Name of Activity|
|`type`|Use `ContactDecision`|
|`configurationArguments`|A single object in an `outcomes` array consisting of `key` name/value pair providing a unique identifier for the Wait outcome and a `next` key/value pair that defines the key of the next Activity object once the wait period has ended|
|`metaData`|A set of name/value pairs containing properties related to the wait time. Refer to the Configuration Argument Properties table.|


