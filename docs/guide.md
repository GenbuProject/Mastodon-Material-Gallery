# Guide
In this document, a folder name of target profile is called as `{profile_name}` and file name as `{file_name}`.

## For Server Admins
### How to install
If resources have original instructions to install, please follow it.

#### Plugins
1. Download or clone a scss file.
2. Move the file into [`plugins`](https://github.com/GenbuProject/Mastodon-Material/tree/master/src/mastodon-material/plugins) folder of Mastodon Material.
3. Add lines into `profiles/{profile_name}/plugins.scss` like below.  
   ```scss
   @import '../../plugins/{file_name}';
   ```

#### Color
1. Download or clone a scss file.
1. Move the file into [`color`](https://github.com/GenbuProject/Mastodon-Material/tree/master/src/mastodon-material/color) folder of Mastodon Material.
2. Add lines into `profiles/{profile_name}/config.scss` like below.  
   ```scss
   @import '../../color/{file_name}';
   ```

#### Layout
1. Download or clone a scss file.
1. Move the file into [`layout`](https://github.com/GenbuProject/Mastodon-Material/tree/master/src/mastodon-material/layout) folder of Mastodon Material.
2. Add lines into `profiles/{profile_name}/config.scss` like below.  
   ```scss
   @import '../../layout/{file_name}';
   ```

### Update
Replace old files, introduced in step 2 into new ones.  
Some resources show update messages on console.

## For Developers
### About variables
Reference to official resources such as [color/v1-light.scss](https://github.com/GenbuProject/Mastodon-Material/blob/master/src/mastodon-material/color/v1-light.scss) or [layout/material-v2.scss](https://github.com/GenbuProject/Mastodon-Material/blob/master/src/mastodon-material/layout/material-v2.scss) to find available variables.

### Fallback
When compatibility is lost due to version upgrades or specification changes, fallback to official resources may reduce compatibility issues. Add a config like below. The reference should be changed appropriately to fit for the file places.

#### Color
```scss
@import '../color/{file_name}';
```

#### Layout
```scss
@import '../layout/{file_name}';
```

### Specify a target version of plugins
You can show messages on console when the version of Mastodon Material differs from the plugin target version, specified in resources. Add a config at the top of the scss file like below.
```scss
$name: "Plugin Name";  // Plugin name
$plugin-version: "1.0.0";  // Version of plugin
$target-version: "1.0.0";  // Check $version in theme/theme.scss
$website: "";  // Website or Download URL
@include version-check($name, $plugin-version, $target-version, $website);
```

### How to contribute
If you want to distribute your resources on this repository, you have to open pull request according to the following format.
- At least, resource name, description (in any languages) and version should be provided in pull request comment. It will be displayed on [README.md](../README.md). You can include one screenshot.
- If you have more than one file, put them in a single folder. You can nest folder.
- You can include these files except scss files.
  - README file
  - Screenshots
  - LICENSE file
