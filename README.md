# Create AWIPS CAVE Application on macOS

## 1. Set up necessary Apple Developer Certificate

A file should exist called **cert.sh** (which is ignored for this repo by the file **.gitignore**) which contains a single line:

    export cert="Developer ID Application: CERTIFICATE_NAME"

Where CERTIFICATE_NAME is something like *University Corporation for Atmospheric Research (\_\_KEY\_\_)*

## 2. Export developer.product from Eclipse

- Right-click on the `developer.product` in the Project Explorer > Click "Export..."
- Choose "Plug-in Development" > "Eclipse product" > "Next"
- Choose a destination directory for the "Directory" section in the middle of the window
- Proceed with other default settings > "Finish"

## 3. Create application folder

- Make a directory for the cave template called `awips2-cave-template`
- Add a symlink for the system Applications dir in this template directory
    - `ln -s /Applications Applications` 
- Add symlink for Info.plist that points to the `awips2-builds` repo
    - `ln -s /Users/awips1/dev/awips2-builds/cave/com.raytheon.viz.product.awips/Info.plist Info.plist`
- Add the `libjep.dylib` file here
    - not sure where you're supposed to get this originally, but can copy from other build repos that have been used before
- Run **create.sh ${cave_export_directory}** to prepare the directory **awips2-cave-template**
    - This will prompt for password, it's expecting the user's password (awips1 for lenny for example)

## 4. Create DMG

- Create a new directory called `osx_release`
- Modify the `dmg.sh` to have the proper, new version number
- Run **dmg.sh** to create a signed DMG for distribution from **awips2-cave-template**
    - This will prompt for password, it's expecting the user's password (awips1 for lenny for example)
