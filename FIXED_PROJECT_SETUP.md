# DocumentFlow iOS - Fixed Project Setup Guide

I've identified and fixed several issues that were preventing the project from running correctly in Xcode. Here's a summary of the changes and additional steps you might need to take:

## Changes Made to Fix Issues

1. **Fixed Entry Point Conflict**
   - Removed `@main` annotation from AppDelegate.swift
   - Updated main.swift to serve as the clear entry point

2. **Resolved Core Data Model Duplication**
   - Removed duplicate Core Data model at DocumentManager/DocumentManager.xcdatamodeld
   - Left the correct model at DocumentManager/Models/DocumentManager.xcdatamodeld

3. **Created Comprehensive Setup Guide**
   - See XCODE_SETUP_GUIDE.md for detailed troubleshooting steps

## How to Open the Project in Xcode

1. Clone the repository:
   ```
   git clone https://github.com/TheNuckingfut/DocumentFlow-iOS.git
   ```

2. Open the project in Xcode by double-clicking on `DocumentManager.xcodeproj`

3. If Xcode shows any missing file references (red files in the navigator):
   - Right-click on the file and select "Delete" (choose "Remove Reference Only")
   - Right-click on the appropriate group folder
   - Select "Add Files to DocumentManager"
   - Navigate to the actual file location and add it

## Common Error Fixes

### If You See "No such module" Errors:
1. In Xcode, go to Product > Clean Build Folder
2. Close and reopen Xcode
3. Build the project again

### If Core Data Model Isn't Found:
1. In CoreDataStack.swift, verify that line 19 has the correct model name:
   ```swift
   let container = NSPersistentContainer(name: "DocumentManager")
   ```
2. Make sure the DocumentManager.xcdatamodeld is properly added to the target:
   - Select the file in the Project Navigator
   - Open the File Inspector (right panel)
   - Under Target Membership, ensure "DocumentManager" is checked

### If Build Fails with Duplicate Symbol Errors:
This could be because both main.swift and AppDelegate have entry points.
1. Make sure AppDelegate.swift does NOT have the `@main` annotation
2. Make sure main.swift has the UIApplicationMain call as shown in the fixed code

## Running the Project

1. Select an iOS simulator (iPhone 13, etc.)
2. Click the Run button (▶) or press Cmd+R
3. The app should launch in the simulator

## If You're Still Having Issues

If you continue to experience problems after following these steps, you may need to recreate the Xcode project file:

1. Create a new Single View App in Xcode
2. Use the same bundle identifier (com.example.DocumentManager)
3. Manually add all the existing files from the repository to the new project
4. Configure Core Data and other settings as needed

Feel free to reach out if you have any questions or need further assistance!