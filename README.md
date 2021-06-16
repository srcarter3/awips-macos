> **Quick Note:** the latest version of all these files exist in the `awips2-builds` repo, on the latest **mac branch**, in the `/build/macOS` directory  
> Ex: [18.2.1-osx](https://github.com/Unidata/awips2/tree/unidata_18.2.1-osx/build/macOS)

## 1. Set up a "working" build directory

- Create a new directory: For example `~/dev/18.2.1-release/`
- Copy the contents from the `awips2` repo into here
   - `cp -RP ~/awips2/build/macOS/* ./`
   - the `-RP` options are used to make sure the template directory and symlink are copied over properly

## 2. Export from Eclipse

- Right-click on the `developer.product` in the Project Explorer > Click "Export..."
- Choose "Plug-in Development" > "Eclipse product" > "Next"
- Set the "Directory" section in the middle of the window to the [directory created in the previous step](#1-set-up-a-working-build-directory)
- Proceed with other default settings > "Finish"

## 3. Set the proper version

- Update the version strings and tags in `Info.plist`
- Update the version variable in `dmg.sh`

## 4. Create the dmg

- Run `create.sh ${cave_export_directory}` to prepare the directory `awips2-cave-template`
- Run `dmg.sh` to create a signed DMG for distribution from `awips2-cave-template`
    > **Note:* As of right now (June 16, 2021) this needs to be run on Lenny (VNC - not sshing) otherwise the codesign fails

## 5. Submit dmg for notarizing
- Run:
   ```
   xcrun altool --notarize-app --primary-bundle-id "cave-dmg" --username "[username]" --password [password] --file osx_release/awips2-cave-18.2.1-1-release.dmg
   ```
   where the [username and password can be found in this document](https://docs.google.com/document/d/1xSE5EnJCKXqi-AfxObunTSmevBKQ2YmNvpaBM8VKfuE/edit#)
- Check on notarize status and get the url for final output, run:
   ```
   xcrun altool --notarization-info [requestID] --username "[username]" --password [password]` 
   ```
   where the requestID is returned from the previous command
- If it passes successfully the output will look like:
   ```
   No errors getting notarization info.
          Date: 2021-06-16 01:35:29 +0000
          Hash: 03d6995a6ea84b63f2582a1ed6b1a2dcd091e5e22fe54531d30376407dba45af
    LogFileURL: https://osxapps-ssl.itunes.apple.com/itunes-assets/Enigma115/v4/95/74/3f/95743f11-6e16-8a53-e9a9-a1e3ade9244a/developer_log.json?accessKey=1624002717_3979931871900262757_uhWyOrR6xW1EAZuQPoqvcxq56sFkCNqTEXuWN13XiCzQMX6M0TTC3C2OlEtiTCVEP4ZHypIQei%2FUNE%2BamF%2BXjJfOQXX7lPAPo26KvB%2F8578QeZgNCF7p6WD8Ra0LLXGqWgyXtJzaJ2JWnhvtqt6fDlzMi%2B%2FaxHXfXdaGemHw6XU%3D
   RequestUUID: ffb21044-a5b3-4451-9acc-1e7fe4709e34
        Status: success
   Status Code: 0
   Status Message: Package Approved
   ```
## 6. Staple dmg
- Run:
   ```
   xcrun stapler staple osx_release/awips2-cave-18.2.1-release.dmg
   ```

## 7. Upload to Robin
- rsync the file to robin, or wherever the current online repository is!
