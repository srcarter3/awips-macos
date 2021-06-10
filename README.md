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
    > **Note:* Both of these will prompt for password, it's expecting the user's password (awips1 for lenny for example)
