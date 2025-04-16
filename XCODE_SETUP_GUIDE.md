# Xcode Setup Guide for DocumentFlow iOS

If you're experiencing issues running the project in Xcode, follow these steps to fix the most common problems:

## First-Time Setup Issues

1. **Open the project in Xcode**
   ```
   Open DocumentManager.xcodeproj in Xcode
   ```

2. **Fix Core Data Model Issues**
   - If you see errors related to Core Data models, do the following:
     - Delete the reference to `DocumentManager.xcdatamodeld` from the Project Navigator (but not from disk)
     - Right-click on the DocumentManager group and select "Add Files to DocumentManager"
     - Navigate to DocumentManager/Models/DocumentManager.xcdatamodeld and add it
     - When prompted, check "Copy items if needed" and add to target "DocumentManager"

3. **Fix Missing Files**
   - If Xcode shows missing files in red:
     - Remove them from the project (delete reference only, not from disk)
     - Add them back using "Add Files to DocumentManager" with proper targets selected

4. **Update Bundle Identifier**
   - Select the project in the navigator
   - Select the "DocumentManager" target
   - In the "General" tab, update the Bundle Identifier to a unique value
     (e.g., "com.yourname.DocumentFlow")

5. **Fix Build Settings**
   - Select the project in the navigator
   - Select the "DocumentManager" target
   - In the "Build Settings" tab, search for "Swift Compiler - Language"
   - Make sure "Swift Language Version" is set to "Swift 5" or later

6. **Clean and Rebuild**
   - Select Product > Clean Build Folder
   - Build and run the project again

## Common Error Solutions

### "Cannot find type 'MainTabView' in scope"
This means Xcode can't find your SwiftUI views. Ensure:
- MainTabView.swift is added to the project
- There are no syntax errors in MainTabView.swift
- All required imports (SwiftUI, etc.) are included

### "Failed to load model named DocumentManager"
This means Core Data can't find your data model. Fix:
- Make sure DocumentManager.xcdatamodeld is properly added to the project
- Check that CoreDataStack.swift has the correct model name

### "Multiple commands produce..."
If you see duplicate file errors:
- Go to the Build Phases tab of your target
- Check "Copy Bundle Resources" for duplicate entries
- Remove duplicates from the project

### Framework Linking Issues
If you see errors about missing frameworks:
- Go to the General tab of your target
- Under "Frameworks, Libraries, and Embedded Content"
- Click "+" and add the missing frameworks (UIKit, SwiftUI, CoreData)

## After Everything is Set Up

Once you have the project running, you should:

1. Test creating, editing, and deleting documents
2. Verify offline functionality works by turning off network access
3. Check that the sync mechanism properly updates when coming back online
4. Verify favorites functionality works across the app

If you continue to experience issues, see the Common Error Solutions section above for more troubleshooting steps.