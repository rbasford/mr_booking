# Office 365 Code Snippets for Android
[![Build Status](https://travis-ci.org/OfficeDev/O365-Android-Snippets.svg?branch=travis-integration)](https://travis-ci.org/OfficeDev/O365-Android-Snippets)

**Table of contents**

* [Change History](#change-history)
* [Device requirements](#device-requirements)
* [Prerequisites](#prerequisites)
* [Open the project using Android Studio](#open-the-project-using-android-studio)
* [Run the project](#run-the-project)
* [Understand the code](#understand-the-code)
* [Connect to Office 365](#connect-to-office-365)
* [Questions and comments](#questions-and-comments)
* [Additional resources](#additional-resources)

This sample for Android is a repository of simple method examples that access email, calendar events, contacts, and files in Office 365. These "snippet" methods are self contained so you can paste them into your own code or use as reference for learning. This sample has snippets for the most common create, read, update, and delete operations on Office 365 content.

This sample includes the following operations:

**Calendar**

* Get existing calendar events by date range.
* Create an event.
* Create a recurring event.
* Update an event.
* Delete an event.
* Accept an event invitation.
* Decline an event invitation.
* Get the status of an event attendee.

**OneDrive for Business**

* Get existing files and folders.
* Create text files.
* Delete files or folders.
* Read text file contents.
* Update text file contents.
* Upload or download files.

**Mail**

* Get existing mail items.
* Get mail items by subject.
* Delete mail item.
* Send new mail.
* Forward email.
* Reply to email.
* Send email with text file attachment.
* Get email attachments from inbox.
* Remove attachments from email message.

**Contacts**

* Get existing contacts.
* Create a contact.
* Update a contact.
* Delete a contact.

**Azure Active Directory**

* Get users.
* Get groups.
* Get tenant details.

We will continue adding snippets to this sample, so make sure to check back.

## Change History
April 6, 2015:

* Initial release.

April 16, 2015:

* Added snippets for sending email with text file attachments and getting attachments from email in your inbox.

May 14, 2015:

* Added snippets for getting organization users and groups with Azure Active Directory.

June 15, 2015:

* Added a snippet to remove attachments from a draft message.


June 14, 2015:
* Added snippets for removing attachments from email messages.

## Device requirements
To run the snippets project your device needs to meet the following requirements:

* Android API level 16 or newer.

### Prerequisites

To use the Office 365 Code Snippets for Android you need the following:

* The latest version of [Android Studio](http://developer.android.com/sdk/index.html).
* The [Gradle](http://www.gradle.org) build automation system version 2.2.1 or later.
* An Office 365 account. You can sign up for [an Office 365 Developer subscription](https://portal.office.com/Signup/Signup.aspx?OfferId=C69E7747-2566-4897-8CBA-B998ED3BAB88&DL=DEVELOPERPACK&ali=1#0) that includes the resources that you need to start building Office 365 apps.
* [Java Development Kit (JDK) 7](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html).
* A registered Azure application with a client id and redirect uri value. The application must have the following permissions:
	* Windows Azure Active Directory
		* Enable sign-on and read user's profiles.
		* Access your organization's directory.
	* Office 365 SharePoint Online
		* Read and write user files.
	* Office 365 Exchange Online
		* Read and write user mail.
		* Send mail as a user.
		* Read and write user calendars.
		* Read and write user contacts.

## Azure client application registration
Each client application that you register with Azure can have its own unique set of permission requirements, application title, and redirect URL. Unless you have an existing application registration that uses the same combination of permissions, title, and URL, you should create a new registration for each app.

*  [Register a native client application in Azure Active Directory](https://msdn.microsoft.com/office/office365/HowTo/add-common-consent-manually#bk_RegisterNativeApp) and [assign the required permissions](https://github.com/OfficeDev/O365-Android-Snippets/wiki/Grant-permissions-for-the-Snippet-application-in-Azure) to the sample application in Azure.

 > Note: Be sure to select the **native client application** on step 5 of the Azure Management Portal azure application procedure.


## Open the project using Android Studio
Open the project by importing the settings.gradle file.

1. Install [Android Studio](http://developer.android.com/tools/studio/index.html#install-updates) and add the Android SDK packages according to the [instructions](http://developer.android.com/sdk/installing/adding-packages.html) on developer.android.com.
2. Download or clone the [Office 365 Code Snippets for Android](https://github.com/OfficeDev/O365-Android-Snippets).
3. Start Android Studio.
4. From the **Welcome to Android Studio** dialog box, choose **Import project (Eclipse ADT, Gradle, etc)**.
5. Respond to the dialog ("Gradle Sync: Gradle settings for this project are not configured yet. Would you like the project to use the Gradle wrapper? ") by clicking the OK button to use the Gradle wrapper
5. Select the **settings.gradle** file in the **O365-Android-Snippets** folder and click **OK**.
6. Open [```Constants.java```](app/src/main/java/com/microsoft/office365/snippetapp/helpers/Constants.java).
7. Find the [```CLIENT_ID```](app/src/main/java/com/microsoft/office365/snippetapp/helpers/Constants.java#L19) constant and set its String value equal to the client id you registered in step&nbsp;1.
8. Find the [```REDIRECT_URI```](app/src/main/java/com/microsoft/office365/snippetapp/helpers/Constants.java#L20) constant and set its String value equal to the redirect URI you registered in step&nbsp;1.

    ![Office 365 Snippet sample](/readme-images/constants_Modify.png "Client ID and Redirect URI values in Constants file")

> Note: The starter project declares the required dependencies using Gradle. The dependencies are:
> * The [Azure Active Directory Authentication Library for Android](https://github.com/AzureAD/azure-activedirectory-library-for-android).
> * The [Office 365 SDK for Android](https://github.com/OfficeDev/Office-365-SDK-for-Android).
> * The [Google Core Libraries for Java 18.0 API](https://code.google.com/p/guava-libraries/).



## Run the project

Once you've built the snippets project you can run it on an emulator or device.

1. Run the project.

 > Note: The sample is designed to run in landscape mode. If you want to run the sample in portrait mode, change the orientation of the emulator by pressing the ctrl-f12 key combination on a Windows computer and control-f12 on a OSX computer.
3. Click the "Connect" item on the action bar overflow menu and enter your credentials.
4. Click a task in the main activity list to run a task.
5. View the results of the task in the detail pane to the right of the list.
6. Optionally, clear the results of the task by clicking the "Clear Results" action bar item.
7. Run all tasks in the list sequentially by clicking the "Run All" action bar item.


## Understand the code

The starter project uses these classes to manage interactions with Office 365:

* [```CalendarSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/CalendarSnippets.java)
* [```ContactsSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/ContactsSnippets.java)
* [```EmailSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/EmailSnippets.java)
* [```FileFolderSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/FileFolderSnippets.java)
* [```UsersAndGroupsSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/UsersAndGroupsSnippets.java)

These classes have snippet methods that wrap calls to the [```SharePointClient```](https://github.com/OfficeDev/Office-365-SDK-for-Android/blob/master/sdk/file-services/src/main/java/com/microsoft/fileservices/odata/SharePointClient.java) and [```OutlookClient```](https://github.com/OfficeDev/Office-365-SDK-for-Android/blob/master/sdk/outlook-services/src/main/java/com/microsoft/outlookservices/odata/OutlookClient.java) objects in the Office 365 SDK for Android. Look at the classes in the com.microsoft.office365.snippetapp.O365Stories package to see how the snippets are called.


### Connect to Office 365

The Office 365 SDK for Android uses the Azure Active Directory Library (ADAL) for Android for connecting your app to Office 365. The ADAL provides protocol support for OAuth2, Web API integration with user level consent, and two-factor authentication.

The **AuthenticationController** object manages getting a token from ADAL and returning it to your application.

### Calendar API

The [```CalendarSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/CalendarSnippets.java) object wraps the API operations that create, update and delete calendar events in an Office 365 Exchange calendar.

The **getO365Events** method gets a list of events from the Office 365 calendar and loads pages of events into a local list. Changes, deletions, and additions to this list are posted asynchronously to the Office 365 calendar by the **updateCalendarEvent**, **deleteCalendarEvent**, and **createCalendarEvent** methods.

### Files API

The [```FileFolderSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/FileFolderSnippets.java) object wraps the API operations that create, update, and delete files stored on OneDrive for Business.

The **getFilesAndFoldersFromService** method gets a list of all of the files and folders that are stored on OneDrive for Business and loads the list into a local array. Changes, deletions, and additions to the local list of files are posted asynchronously to OneDrive for Business by the **postUpdatedFileToServer**, **deleteFileFromServer**, and **postNewFileToServer** methods.

The **getFilesAndFolders** method returns a list of **Item** objects containing the selected files contents.

### Mail API

The [```EmailSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/EmailSnippets.java) object wraps the API operations that create, update and delete mail items in an Office 365 Exchange mailbox.

The **getMailMessages** method gets a list of mail items from the Office 365 mailbox and loads pages of items into a local list. Deletions to this list, and mail sent from the mailbox are posted asynchronously to the Office 365 calendar by the **deleteMail**, **sendMail**, **forwardMail**, and **replyToEmailMessage** methods.

### Contacts API

The [```ContactsSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/ContactsSnippets.java) object wraps the API operations that create, update and delete contacts in Office 365 Exchange.

The **getContacts** method gets a list of contacts from Office 365 and loads pages of contacts into a local list. Changes, deletions, and additions to this list are posted asynchronously to Office 365 by the **updateContact**, **deleteContact**, and **createContact** methods.

### Azure Active Directory API

The [```UsersAndGroupsSnippets```](app/src/main/java/com/microsoft/office365/snippetapp/Snippets/UsersAndGroupsSnippets.java) object wraps the API operations for working with users, groups, and other Azure Active Directory data. Office 365 users and groups are stored in Azure Active Directory.

The **getUsers** method gets a list of all users from the Office 365 tenant. Similarly **getGroups** gets all the groups from the Office 365 tenant. **getTenantDetails** will retrieve information about the Office 365 tenant itself.

## Questions and comments

We'd love to get your feedback on the O365 Android Snippets project. You can send your questions and suggestions to us in the [Issues](https://github.com/OfficeDev/O365-Android-Snippets/issues) section of this repository.

Questions about Office 365 development in general should be posted to [Stack Overflow](http://stackoverflow.com/questions/tagged/Office365+API). Make sure that your questions or comments are tagged with [Office365] and [API].

<a name="resources"/>
## Additional resources

* [Office 365 APIs platform overview](http://msdn.microsoft.com/office/office365/howto/platform-development-overview)
* [File REST API reference](https://msdn.microsoft.com/office/office365/api/files-rest-operations)
* [Outlook Calendar REST API reference](http://msdn.microsoft.com/office/office365/api/calendar-rest-operations)
* [Outlook Mail REST API reference](https://msdn.microsoft.com/office/office365/api/mail-rest-operations)
* [Office Dev Center](http://dev.office.com/)
* [Office 365 APIs starter projects and code samples](http://msdn.microsoft.com/office/office365/howto/starter-projects-and-code-samples)
* [Office 365 Connect Sample for Android](https://github.com/OfficeDev/O365-Android-Connect)
* [Office 365 APIs Starter Project for Android](https://github.com/OfficeDev/O365-Android-Start)
* [Office 365 Profile sample for Android](https://github.com/OfficeDev/O365-Android-Profile)


## Copyright
Copyright (c) 2015 Microsoft. All rights reserved.
