---
title: Copy of Able3Gcal Reference
layout: post
author: bellavejayaram
permalink: /copy-of-able3gcal-reference/
source-id: 1fVoB4Y6ROgafc-oGns1B0D8N5o4GGTjmeZi-InEHjZE
published: true
---
[[TOC]]

# PURPOSE OF DOCUMENT

This document is a user's guide for using the Able3 Ventures Gcal library which provides integration capability from AppSheet apps to Google calendar.

# Overview

There are many instances when an app developed for a specific purpose (examples include CRM, Project Management, Training, Supply Chain management, Delivery and tracking) need to be able to integrate with Google calendar. Developed based on some our clients' needs, the Able3 GCal library makes it possible to avail of the rich functionality of Google calendar in AppSheet apps.

Here are a few concrete examples of when a Calendar integration is useful in apps:

1. A company has salesmen who need an app to acquire customers and need to schedule follow ups in order to close the sale. The schedule can be maintained in a Google calendar.

2. A company has a dispatcher who needs an app to schedule workers to various job sites. Each worker's email can be added to events in a Google calendar and it can be shared with the worker.

3. A company has several training sessions and needs an app to enroll students to one of the sessions. They could create events and send calendar invites to the students.

4. A company has an app to keep track of parts inventory and needs to schedule re-orders for low inventory from suppliers. They could use a Google calendar to keep track of promised delivery dates and notifications for staff to prepare to take delivery. 

5. A company has several properties that are available for rent  for a day and when users book and pay for those properties, they need a way to share that reservation calendar with the buyer.

Although it is possible to add a specific [Google calendar as a data source](https://appsheethelp.zendesk.com/hc/en-us/articles/219380317-Using-data-from-Google-Calendar) in AppSheet there are only a few operations that can be performed. Also, as of the date of publication of this manual, AppSheet does not yet have a mobile friendly and traditional calendar view of data. 

Google calendar and Google calendar app available in the Play Store provide a familiar interface and rich functionality that allow you to create events and share them with others. Each person with whom an event is shared can customize their own reminders without affecting others.

# Architecture

 The ABLE3 GCal library is a set of google apps script (GAS) functions that can be easily integrated into any app built using AppSheet. The diagram below shows the various components that are required to use the library.

1. **Appsheet Editor** - if you have used AppSheet before, this should be familiar to you. You can have any number of data sources for your app but, in order to use the Able3 GCal library, at least one of your data sources must be a Google sheet.

2. **Google sheet(s)** - this is the source of data for both the AppSheet app and for any scripts (see below) that are bound to the sheet.

3. **Script Editor** - this is an editor that allows you to extend the functionality of your Google sheet by developing code in a programming language known as google apps script.

4. **Able3 GCal library** -  this is a library of functions written in google apps script that allows you to extend the functionality of your AppSheet app by accessing a Google calendar.

5. **Google calendar** - this is a shared calendar that is used by one or more users to manage appointments and reminders.

The typical scenario of how this works is as follows: 

The app user enters data relating to an event into the app. These events, which can involve locations, dates, times etc. , are stored in the Google sheet. Either via a timed trigger or whenever a change is detected to rows and columns in a particular tab within the Google sheet, a specific function that you write inside the script (attached to the sheet) can be executed. 

Your functions can be simple wrapper functions that make calls to the Able3 GCal library functions or they can do more complex computations as needed for your app. The Able3 GCal library function takes care of interactions between the data in the Google sheet and events in Google calendar. 

# Requirements

There are two (2) main requirements for using the Able3 GCal library.

1. It is required that at least one Google sheet be present as a data source in your app in order to integrate it.  The app can be constructed using any of the data sources supported by AppSheet. 

2. It is required to have a tab named "**_ScriptSetting_**" in the Google sheet. 

# Available Functions

**_findEventSettings_**(*settingpg, seeEachOther, shareEvent, modifyEvent*)   

**_createCalEvent_**(*calid, title, startTime, endTime, location, description, guest, seeEachOther, shareEvent, modifyEvent, reminderType, minutesBefore*) 

**_createRecurringCalEvent_**(*calid, title, startTime, endTime, recurrence, repeat, location, description, guest, seeEachOther, shareEvent, modifyEvent, reminderType, minutesBefore*) 	

**_deleteCalEvent_**(*calid, eventid*) 

# Setting up

(shown as code.gs and is accessible by using the Tools-> Script Editor… in the  Google sheets menu. 

# Addendum

Function Reference

/**

 * Find the calendar id

 * @param {string} settingpg name of the Settings sheet

 * @param {string} settingname named range for Calendar ID

 * @return {string} the Calendar ID

 */

function findCalID(settingpg, settingname)

/**

 * Find the status

 * @param {string} settingpg name of the Settings sheet

 * @param {string} settingname named range for Script Status

 * @return {range} script status range

 */

function findStatus(settingpg, settingname) {

/**

 * Find the calendar event settings

 * @param {string} settingpg name of the Settings sheet

 * @param {string} seeEachOther named range for Calendar Event setting if attendees see each other or not

 * @param {string} shareEvent named range Calendar Event setting if attendees can share the event or not

 * @param {string} modifyEvent named range Calendar Event setting if attendees can modify the event or not

 * @return {boolean} The Calendar Event Settings

 */

/**

 * Create a Calendar Event

 * @param {string} calid calendar id

 * @param {string} title calendar event title

 * @param {string} startTime starting date and time for calendar event

 * @param {string} endTime ending date and time for calendar event

 * @param {string} location calendar event location

 * @param {string} description calendar event description

 * @param {string} [guest] calendar event guests (optional)

 * @param {boolean} seeEachOther named range for Calendar Event setting if attendees see each other or not

 * @param {boolean} shareEvent named range Calendar Event setting if attendees can share the event or not

 * @param {boolean} modifyEvent named range Calendar Event setting if attendees can modify the event or not

 * @param {string} [reminderType] type of reminder for the Calendar Event (optional)

 * @param {number} [minutesBefore] reminder duration in minutes before the Calendar Event (optional)

 * @return {string} event ID

 */

/**

 * Create a Recurring Calendar Event

 * @param {string} calid calendar id

 * @param {string} title calendar event title

 * @param {string} startTime starting date and time for calendar event

 * @param {string} endTime ending date and time for calendar event

 * @param {string} recurrence recurrence type for calendar event for example DAY, WEEK, MONTH

 * @param {number} repeat how many times the calendar event will be recurring

 * @param {string} location calendar event location

 * @param {string} description calendar event description

 * @param {string} [guest] calendar event guests (optional)

 * @param {boolean} seeEachOther named range for Calendar Event setting if attendees see each other or not

 * @param {boolean} shareEvent named range Calendar Event setting if attendees can share the event or not

 * @param {boolean} modifyEvent named range Calendar Event setting if attendees can modify the event or not

 * @param {string} [reminderType] type of reminder for the Calendar Event (optional)

 * @param {number} [minutesBefore] reminder duration in minutes before the Calendar Event (optional)

 * @return {string} event ID

 *//**

 * Delete a Calendar Event

 * @param {string} calid calendar id

 * @param {string} eventid calendar event id

 */

The ScriptSetting tab can be auto-generated by constructing an onOpen() event handler as shown below.

function onOpen() {

 var service = PropertiesService.getScriptProperties();

 var scrProp = service.getProperty("runOnce");

 if (scrProp == null) {

   var setProp = service.setProperty("runOnce","false");

   var getProp = "false";

 }

 if (getProp == "false" || scrProp == "false") {

   var lib = ABLE3GCAL.checkSettingsSheet();

   Logger.log(lib);

   service.setProperty("runOnce", lib);

 }

}

