## 1. Set up a "working" build directory

- Create a new directory: For example `~/dev/18.2.1-release/`
- Copy the contents from the `awips2` repo into here
   - `cp -RP ~/awips2/build/macOS/* ./`
   - the `-RP` options are used to make sure the template directory and symlink are copied over properly
- Because git only tracks files, you cannot have an empty directory, so now make the `osx_release` directory
   - `mkdir osx_release` 

## 2. Export from Eclipse

- Right-click on the `developer.product` in the Project Explorer > Click "Export..."
- Choose "Plug-in Development" > "Eclipse product" > "Next"
- Set the "Directory" section in the middle of the window to the [directory created in the previous step](#1-set-up-a-working-build-directory)
- Proceed with other default settings > "Finish"

## 3. Create the dmg

- Run `create.sh ${cave_export_directory}` to prepare the directory `awips2-cave-template`
    - This will prompt for password, it's expecting the user's password (awips1 for lenny for example)
- Modify the `dmg.sh` to have the proper, new version number
- Run `dmg.sh` to create a signed DMG for distribution from `awips2-cave-template`
    - This will prompt for password, it's expecting the user's password (awips1 for lenny for example)
