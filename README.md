# Create AWIPS CAVE Application on macOS

## 1. Set up necessary Apple Developer Certificate

A file should exist called **cert.sh** (which is ignored for this repo by the file **.gitignore**) which contains a single line:

    export cert="Developer ID Application: CERTIFICATE_NAME"

Where CERTIFICATE_NAME is something like *University Corporation for Atmospheric Research (\_\_KEY\_\_)*

## 2. Export developer.product from Eclipse

## 3. Create application folder

Run **create.sh ${cave_export_directory}** to prepare the directory **awips2-cave-template**

## 4. Create DMG

Run **dmg.sh** to create a signed DMG for distribution from **awips2-cave-template**

