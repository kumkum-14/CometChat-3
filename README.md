Building an Android Chat App with CometChat UI Kit

Description

This repository provides an Android sample app that demonstrates integrating CometChat’s UI Kit for tab-based messaging functionality.

It features:

    -A tab-based messaging UI 
    -Sections for Chats, Calls, Users, and Groups.
    -Real-time messaging with session persistence
    -Seamless navigation using Activities (can be extended to Fragments or Jetpack Navigation)
    -Lightweight, responsive, and optimized for mobile devices.

Features

        -Bottom Navigation for quick feature switching
        -Dedicated Fragments: Chats, Calls, Users, Settings
        -No Sidebar; mobile-first stack-based design
        -Modular & Extensible for adding tabs
        -Unified interface for chat, VoIP, user management
        -Responsive layouts for various screens

Getting Started

1️. Create a CometChat Account

    Visit the CometChat Dashboard:
    https://app.cometchat.com/signup
    Register or log in to access the Dashboard.

2. Create an App on CometChat Dashboard

        -In the Dashboard, click + Add App.
        -Enter a name for your app and click Create App.
        -Navigate to Application → Credentials and copy the following values:
            App ID
            Auth Key
            Region
        -Store these values securely; you will reference them in your Android project configuration.

3. Install Dependencies

       All dependency declarations and version catalogs are managed with Gradle.

       -Project-level Build Configuration

       Open build.gradle.kts to verify that mavenCentral() and the CometChat Maven repository are included under allprojects → repositories.

-App-level Build Configuration

Open app/build.gradle.kts and confirm the following dependencies:

        com.cometchat:chat-uikit-android (CometChat UI Kit)
        com.cometchat:calls-sdk-android (CometChat Calls SDK; optional if you want voice/video features)

For exact versions, refer to the version catalog in                 

    gradle/libs.versions.toml.

Sync Your Project

    In Android Studio, click Sync Now after making changes to Gradle files. This ensures the CometChat SDKs are downloaded.

4. Initialize CometChat UI Kit

        -Open the  main activity file MainActivity.java.
        -Replace the placeholder values for App ID, Region, and Auth Key with the credentials you copied from the Dashboard.
        -Verify that CometChat.init(…) is invoked in the onCreate() method so the SDK initializes before any UI is rendered.
   
5. User Authentication

        -Open the main activity file MainActivity.java.
        -Review the login logic, which calls CometChat.login(uid, authKey, …).
        1)You can use pre-generated test UIDs (e.g., cometchat-uid-1, cometchat-uid-2) or create your own users via the Dashboard, the SDK, or the REST API.
        -Confirm that the Auth Key placeholder has been replaced with your own value.
   
6. Build the Chat Experience

-Layout Overview

    Review layout files in app/src/main/res/layout/ for fragment-based UI:
        activity_tabbed.xml 
        fragment_chats.xml
        fragment_call_logs.xml
        fragment_users.xml 
        fragment_groups.xml
        TabbedActivity
        
-See Tabbed Activity to understand how the CometChat UI Kit fragment is loaded.
        
        app/src/main/java/com/example/cometchatdemo3/TabbedActivity.java

-Key Components
    
    -TabbedActivity.java — Handles bottom navigation and fragment switching
    -ChatsFragment.java — Shows chat conversations
    -CallLogsFragment.java — Displays call history
    -UsersFragment.java — Lists users
    -GroupsFragment.java — Manages chat groups
    -activity_tabbed.xml — Layout with BottomNavigationView and fragment container
    -fragment_chats.xml — Chats UI layout
    -fragment_call_logs.xml — Call logs UI layout
    -fragment_users.xml — Users UI layout
    -fragment_groups.xml — Groups UI layout
    -bottom_nav_menu.xml — Bottom navigation menu items

-Integration Steps

    i. Set Up Layouts
    ii. Implement Fragments(Chat, Call, User, Group)
    iii. Create TabbedActivity
    iv. Initialize and Login User
    v. Verify Navigation and UI

7. Customize Theme

-To apply a global theme that matches CometChat’s styling, open:

    app/src/main/res/values/themes.xml.
-Ensure your root theme is set to inherit from CometChatTheme.DayNight:

    <style name="AppTheme" parent="CometChatTheme.DayNight" />
-Open AndroidManifest.xml and confirm that <application> uses @style/AppTheme as its android:theme.

8. Run the App 

        -Connect an Android device or start an emulator.
        -In Android Studio, click Run > Run ‘app’ or use the toolbar ▶ icon.
        -The Message View interface should load.
        -Open a second instance or a separate device, log in with a different UID, -and send a message to verify real-time delivery.
   
9. Troubleshooting 

        1.Problem: SDK not initializing
        Check: Correct App ID, Region, and Auth Key
        2.problem: Gradle sync fails
        Check: libs.versions.toml for correct versions
        3.problem:Login fails
        check:Ensure UID exists in CometChat (via dashboard or API)

Repository Structure


cometchatdemo3/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/cometchatdemo3/
│   │   │   │   ├── TabbedActivity.java
│   │   │   │   ├── ChatsFragment.java
│   │   │   │   ├── CallLogsFragment.java
│   │   │   │   ├── UsersFragment.java
│   │   │   │   └── GroupsFragment.java
│   │   │   ├── res/
│   │   │   │   ├── layout/
│   │   │   │   │   ├── activity_tabbed.xml
│   │   │   │   │   ├── fragment_chats.xml
│   │   │   │   │   ├── fragment_call_logs.xml
│   │   │   │   │   ├── fragment_users.xml
│   │   │   │   │   └── fragment_groups.xml
│   │   │   │   └── menu/
│   │   │   │       └── bottom_nav_menu.xml
│   │   │   └── AndroidManifest.xml
├── gradle/libs.versions.toml
├── build.gradle.kts
├── settings.gradle.kts
└── README.md

Resources
 CometChat UI Kit Docs – Getting Started
 CometChat Conversations Guide



