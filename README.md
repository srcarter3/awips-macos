# Create AWIPS CAVE Application on macOS

## 0. Set up necessary Apple Developer Certificate

A file should exist called `cert.sh` (which is ignored for this repo by the file `.gitignore`) which contains a single line:

    export cert="Developer ID Application: CERTIFICATE_NAME"

Where CERTIFICATE_NAME is something like *University Corporation for Atmospheric Research (__KEY__)*

## 1. Export developer.product from Eclipse

## 2. Run `create.sh ${cave_export_directory}` to prepare the directory `awips2-cave-template`

## 3. Run `dmg.sh` to create a signed DMG for distribution from `awips2-cave-template`

