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
- Run **create.sh ${cave_export_directory}** to prepare the directory **awips2-cave-template**

## 4. Create DMG

- Run **dmg.sh** to create a signed DMG for distribution from **awips2-cave-template**

