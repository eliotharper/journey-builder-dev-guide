# Salesforce Marketing Cloud New Releases: What They Mean for Developers

The two recent releases of Salesforce Marketing Cloud (Nov 2014 and Jan 2015) include several new platform features and enhancements that are specifically relevant to platform development and integration with Salesforce Marketing Cloud. These developer-related enhancements are explained in detail below.

## Journey Builder Enhancements

### Contact Entry Mode (Jan 2015 Release)

In previous versions of Journey Builder, once a Contact has entered an Interaction they could not enter the Interaction again, even if the Contact has already exited the Interaction. If you create a new version of the Interaction and publish it, then the same rule applies; if the Contact has entered any previous version of the Interaction, then they will not enter the new version.

This is an issue for Interactions where you need a Contact to enter an Interaction more than once, for example annually for birthday or anniversary programs.

In this new release, a Contact Entry Mode has been added to the Interaction Canvas that enables you to define whether a Contact can enter an Interaction once (across all Interaction versions), or multiple times.

If the option is set to 'Single Entry' and a Contact is currently in any version of the Interaction, then they will not be allowed to enter future versions of the Interaction. However, if they are not currently in an Interaction version, they will be allowed to enter the Interaction again (if they meet the Contact Filter Entry Criteria defined in the Interaction Trigger).

If the option is set to 'Multiple Entries', when an Event is fired the Contact  Contact can enter the current active version of an Interaction (if they meet the Contact Filter Entry Criteria defined in the Interaction Trigger), even if they have previously exited the Interaction.

![Setting the Contact Entry Mode](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/contact-entry-mode.png "Setting The Contact Entry Mode in Journey Builder Interaction Canvas")<br />*Setting The Contact Entry Mode in Journey Builder Interaction Canvas*

This mode can also be defined when creating an Interaction using the an Interaction method from the Fuel REST API by including one of the following name/value pairs in the WDF payload:

    "entryMode": "MultipleEntries"
    "entryMode": "SingleEntryAcrossAllVersions"

If you do not define an `entryMode` when creating an Interaction, then the Interaction will use `SingleEntryAcrossAllVersions` by default.

### Date-Based Triggers (Jan 2015 Release)

A new 'Date-Based' Trigger option is available in Interaction Triggers that enables date-based Attributes from the Contact model to determine an entry criteria for the Interaction.

![Date-Based Trigger](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/date-based-trigger.png "Date-Based Trigger in an Interaction Trigger")<br />*Date-Based Trigger in an Interaction Trigger*

A threshold defines the number of days, weeks or months and start time that the Contact should be admitted into the Interaction, before or after the selected Attribute date. When the Contact meets the criteria, the Contact will be admitted into the Interaction. 

Use cases include birthday or anniversary programs, subscription dates, or the last time a Contact used a mobile app. When the value of a Contact Attribute changes, the algorithm re-evaluates the Contact for possible inclusion. 

A re-entry criteria defines whether a Contact can re-enter the Interaction (either yearly, monthly or none).

### Trigger Testing

A new status mode allows a Trigger to be changed to 'Test Mode' so an Interaction Trigger can be tested without admitting Contacts into an Interaction. This is helpful when testing if the Contact Filter Criteria defined in a Trigger has been configured correctly.

To set a Trigger to Test Mode in Journey Builder, select **Triggers** from the **Administration** menu and click on the **Availability** link related to the Trigger you want to test.

Only Triggers that are set to 'Unavailable' can be tested. If a Trigger is currently set to 'Available', select the **Unavailable** radio button and click **Save**, then open the Trigger Status dialog for the Trigger again by selecting **Test Mode** and click **Save**. 

![Trigger Test Mode](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/trigger-test-mode.png "Setting a Trigger to Test Mode in Journey Builder Trigger Administration")<br />*Setting a Trigger to Test Mode in Journey Builder Trigger Administration*

A View Results link will then appear in the Trigger Performance column. Fire an Event (using Automation Studio or the contactEvents API method) for the Interaction Trigger to hear the Event, then click on the **View Results** link to preview the percentage of rejected Contacts (that did not meet the entry criteria) and the percentage of Contacts that would have been accepted into the Interaction, if the Trigger was available.

### Join Activity (Nov 2014 Release)

Join Activities reunite Contacts from two or more different branches back to a single branch. For example, if a Decision Split Activity is used to send two or more different messaging activities to Contacts, a Join Activity can be used to merge branches back together, so contacts continue to flow toward the same endpoint. 

Note that in [Workflow Document Format (WDF)](https://code.exacttarget.com/app-development/journey-builder-development/workflow-format/getting-started.html) there is no `Join` type used in the Activity Object for Join Activities. Instead, WDF uses an Activity `Wait` type to reunite Activities from separate branches back to a single branch.

In WDF, Wait Periods (represented as `Wait` type Activities) are reunited into a single branch by using the same target `Wait` type Activity key for their outcome. The flow diagram below illustrates this behavior, where boxes represent Activity Objects and arrows are outcomes from the Activity Objects.

![WDF Join Flow](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/join-flow.png "A WDF Interaction with a Join Activity")<br />*A WDF Interaction Workflow with a Join Activity*

### Personalization Strings in Email (Nov 2014 Release)

Personalization strings are now supported in emails sent from Journey Builder (in previous releases, emails in a Journey Builder Send Email Activity could not be personalized). The data binding context used for personalization strings is the Event Source Data Extension defined in the Interaction Trigger. 

To include an Event Source Data Extension field in an Email use the `%%fieldName%%` personalization string syntax in the email subject line, preheader or body of the email.

You will need to ensure that an Profile Attribute exists for the Data Extension field before it can be used in an email. To create a new Attribute, select **Profile Management** from the **Subscribers** menu in the Marketing Cloud Email app and click the **Create** button. Add the name of the Data Extension field in the New Attribute Properties dialog and include an optional description, then click OK.

![Creating New Profile Attributes in the Email App](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/new-profile-attribute.png "Creating New Profile Attributes in the Email App")<br />*Creating New Profile Attributes in the Email App*

The Send Email Activity creates a Triggered Send in the Marketing Cloud Email app when the Interaction is published. This Triggered Send is used to deliver the email from the Send Email Activity. When an Interaction enters an unpublished state, the Triggered Send is set to inactive until the Activity is re-published.

Note that if the email template is updated while an Interaction is running, you need to publish the changes for the Triggered Email by selecting **Triggered Emails** from the **Interactions** menu in the Marketing Cloud Email app and expand the Journey Builder Sends tree to locate the email. Select the checkbox next to the email and click the **Publish Changes** button.

![Publishing Triggered Sends](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/publishing-triggered-sends.png "Publishing Triggered Sends from Marketing Cloud Email App")<br />*Publishing Triggered Sends from Marketing Cloud Email App*

### Contact History (Nov 2014 Release)

This feature is helpful to be aware of when troubleshooting an Interaction or monitoring the progress of an Interaction. You can view an activity log for Contacts that have entered an Interaction by selecting **Contacts** from the **Administration** menu in Journey Builder.

This page displays a complete transaction history of current and previously published Interactions. A search filter enables filtering by Contacts to display the Interactions they entered and exited, and the status of the Contact in Interactions. You can also filter by a column value, for example 'DidNotMeetEntryCriteria' to filter all Contacts that did not meet the Contact Filter Criteria defined in the Interaction Trigger.

![Contact History](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/contact-history.png "Date-Based Trigger in an Interaction Trigger")<br />*Date-Based Trigger in an Interaction Trigger*

### Wait Period Time (Jan 2015 Release)

While this new feature is not mentioned in the release notes and not yet supported in the Interaction Canvas interface, it's now available through the Fuel REST API and is worth understanding. Wait Periods in an Interaction can now define what time (and time zone) the Wait Period ends and the next Activity in a branch commences.

A typical use case for this feature is that if you want to start a Send Email Activity at a specific time of day (for example, 2pm when the open rate is higher), then you can define this in the WDF Wait Object.

An example JSON payload of a Wait Object in WDF with values for a `specifiedTime` and `timeZoneId` is provided below.

    {
       "key":"best-send-time",
       "name":"Optimised open rate time",
       "type":"Wait",
       "outcomes":[
          {
             "key":"wait-outcome-to-send-email",
             "next":"send-reminder-email"
          }
       ],
       "configurationArguments":{
          "waitDuration":2,
          "waitUnit":"days",
          "specificTime":"14:00",
          "timeZone":"E. Australia Standard Time"
       }
    }

Supported time zone identifiers (used as `timeZoneId` values) are provided in the [Wait Format documentation](https://code.exacttarget.com/app-development/journey-builder-development/workflow-format/activity-formats/wait.html).

What is interesting to note is that there's a new `waitForEventKey` name/value pair option in a Wait Activity object &mdash; while this is currently reserved for future use, it does indicate the direction of Wait Activities. For example, in the future a Send Email Activity used in an 'Abandoned Cart' Interaction could be configured to Wait until a Contact completes a shopping cart transaction in an ecommerce platform (by firing an Event using the contactEvents API method).

## Journey Builder for Apps Enhancements

### Pictures in Android MobilePush Notifications (Nov 2014 Release)

Pictures can now be included in MobilePush Notifications for Android devices. This support adds impact to push notifications and can improve action rates.

To enable picture notifications in Android devices, create a new `et_big_pic` custom key in Journey Builder for Apps SDK Explorer.

![JBA 4 Apps Admin](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/android_mc_bigpic_admin.png "Creating a Custom Key Journey Builder for Apps SDK Explorer")<br />*Creating a Custom Key Journey Builder for Apps SDK Explorer*

Once the custom key is added, you will be able to include a reference to an image when creating a new Outbound Message in MobilePush. From the MobilePush app, select the **Create Message** button, select the **Outbound** template, and the 'et_big_pic' Custom Key you created in the SDK Explorer will appear as an available custom key. Enter a shortened URL to the image.

![MobilePush Message](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/android_mc_bigpic_create_message.png "Creating a Custom Key Journey Builder for Apps SDK Explorer")<br />*Assigning a URL to a Custom Key in a MobilePush Message*

The Android SDK will handle the message display and the image (which will be scaled as required) will appear in the message notification.

![Picture in Push Notification](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/android_sdk_bigpic_picture_message.png "Image in a MobilePush Message")<br />*Image in a MobilePush Message*

### Journey Builder for Apps SDK Explorer (Nov 2014 Release)

Journey Builder for Apps SDK Explorer available from [Google Play Store](https://play.google.com/store/apps/details?id=com.exacttarget.jb4a.sdkexplorer) enables developers to use the SDK without a requiring a Salesforce Marketing Cloud account. An iOS version of this app will be available from the Apple App Store in the coming months.

![SDK Explorer](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/sendmessage-explorer.png "Sending a Message using Journey Builder for Apps SDK Explorer")<br />*Sending a Message using Journey Builder for Apps SDK Explorer*

## MobilePush

### Interactive Notifications (Nov 2014 Release)

This new feature enables an app to display button controls on a mobile device when it receives a push message from MobilePush. For example, a 'View Offer' button that links to a mobile-optimized landing page. 

The category names of these Interactive Notifications are then included in the message payload. Refer to the [Interactive Notifications developer documentation](http://code.exacttarget.com/apis-sdks/journey-builder-for-apps/feature-implementation/implement-interactive-notifications.html) for implementing this functionality in iOS and Android applications.

Once implemented, Interactive Notifications are available in the outbound message template when creating a message from the MobilePush app. You can include up to four buttons specifying actions per message notification.

### Interactive Notifications for Location Messages (Jan 2015 Release)

Extending the previous release, Interactive Notifications have been added to the Locations feature in MobilePush, enabling Location Exit or Entry messages to include Interactive Notifications based on their defined geofence area.

### Push Service Manager (Nov 2014 Release)

A Push Service Manager app accessible from the HubExchange menu in Marketing Cloud facilitates the management of Apple Push Notification (APNS) Certificates and Google API keys for MobilePush configurations. In turn, this provides a faster, more secure way to register apps with MobilePush.

![Push Service Manager](https://raw.githubusercontent.com/eliotharper/journey-builder-dev-guide/master/images/PushServiceManager.png "Managing MobilePush configurations using Push Service Manager")<br />*Managing MobilePush configurations using Push Service Manager*

## About the Author

Eliot Harper is Chief Technology Officer at Digital Logic, a Salesforce Marketing Cloud Partner based in Melbourne, Australia. Eliot specializes in Customer Journey Management and is author of the Journey Builder Developer's Guide http://jbdevelopers.guide.