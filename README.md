CometChat Android Chat Tutorial: Tab Based Chat Experience

    Best for: Multi-feature chat apps that support tabs for Chats, Calls, Users, and Groups.
    Highlights:
    -Bottom tab navigation with fragments
    -Sidebar for conversation list
    -Full message view with real-time updates
    -Supports text, media, voice/video messages
    -Clean separation of chat areas
1. Set Up CometChat
   
       -Go to CometChat Dashboard and register.
       -Create a new app and note the following:
       -App ID
       -Auth Key
       -Region
2. Add CometChat Dependencies
   
   -Add these to your project:
   
   a. Repository in build.gradle (Project)
   
           dependencyResolutionManagement {
              versionCatalogs {
                  libs {
                      from(files("gradle/libs.versions.toml"))
                  }
              }
          }
   b. Dependencies in build.gradle (App)
   
            dependencies {
             implementation(libs.cometchat.ui.kit)
         
             // (Optional) Include if using voice/video calling features
             implementation(libs.cometchat.calls.sdk)
         }    
   c. Declare versions in libs.versions.toml

       [versions]
       cometchat-ui-kit = "5.0.2"
       cometchat-calls-sdk = "4.1.0"

       [libraries]
       cometchat-ui-kit = { module = "com.cometchat:chat-uikit-android", version.ref = "cometchat-ui-kit" }
       cometchat-calls-sdk = { module = "com.cometchat:calls-sdk-android", version.ref = "cometchat-calls-sdk" } 
3. Initialize CometChat

        -The UI Kit is initialized in `MainActivity.java` using `UIKitSettings`.
        -Initialization requires your `App ID`, `Region`, and `Auth Key`.
4. Authenticate a User
   
        -After initialization, the app logs in a user by their UID.
        -To authenticate a user in CometChat, you need the UID (unique user ID). There are two main options for getting this UID:
        a. Pre-generated test users:
            cometchat-uid-1 
            cometchat-uid-2 
            cometchat-uid-3  
            cometchat-uid-4  
            cometchat-uid-5
   
        b. Or create users:
        create your own users via CometChat Dashboard,CometChat SDK method or via API.
        -Use the provided MainActivity code to initialize CometChat UI Kit and perform user login.
        -Replace appID, region, and authKey with your own credentials.
        -Use one of the pre-generated test UIDs or create your own users.   
5. Create Tabbed Navigation UI
   
       -Design an activity (TabbedActivity) with BottomNavigationView
       -Use fragments for each tab:
              ChatsFragment
              CallLogsFragment
              UsersFragment
              GroupsFragment
       -Each fragment hosts UI Kit components (conversation lists, user lists, group lists, etc.).
6. Implement Fragment Navigation
   
        -Switch between fragments on tab item selection
        -Set default tab (e.g., Chats) on launch
        -Load corresponding fragment content dynamically using FragmentManager

7. Display Message View
   
          -From Chats, Users, or Groups list, launch the Message View screen.
          -Message View includes:
              Chat Header
              Message List
              Message Composer
          -Use CometChatMessageList and CometChatMessageComposer components to build this experience

8. Enable Calling (Optional)
    
          Add cometchat-calls-sdk dependency
          From Call Logs, enable voice/video calling UI
          Works seamlessly with CometChat calling APIs

9. Customize the Theme
    
        Use CometChatTheme.DayNight as the base theme in your app
        Apply it in themes.xml and set it in AndroidManifest.xml
        Customize colors and styles globally for a consistent look

10. Run the App
