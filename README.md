# tutorial-project

Running through [this](https://www.youtube.com/playlist?list=PLpVC00PAQQxGFC06mLqoPT4hHaA1Ykn2Z) tutorial to set up a sample Drupal site. Will be making notes here.

## Initialization

### Project Setup in Terminal
1. Open a terminal in the folder you want your project in
2. Run `composer create-project drupal/recommended-project tutorial-project` where *tutorial-project* is the name of your project
3. cd into the project folder
4. Run `composer config vendor-dir vendor`
5. Run `composer config repositories.1 composer https://asset-packagist.org`
6. Run `composer config preferred-install dist`
7. Install required packages:
    - Drush: `composer require drush/drush`
    - Stage File Proxy: `composer require drupal/stage_file_proxy`
    - Cweagans: `composer require cweagans/composer-patches`
        - y
8. Configure DDEV and launch project
    - `ddev config`
    - `ddev start`
    - `ddev launch`

### Site Setup in Browser

SuperUserLogin: testSuperUser, StrongPassword1!

## Composer vs. Drush

When using Composer to manage Drupal, *use composer*. Do not use Drupal to manage packages/modules in Drupal, and to install/remove dependencies.

Use Drush for site building activity such as clearing cache.

## Checking for updates

### For module updates

Run `composer outdated 'drupal/*'` to check for outdated dependencies

For a minor-version update to a given Drupal module/project, use the following, replacing modulename: `ddev composer update drupal/modulename --with-all-dependencies`. This will update the module you want as well as dependencies of that module for you.

### For DB udpates

First, run `ddev ssh`. Then run `drush -V` to verify you have a current version of Drush installed. Then you can run `drush updatedb` then `drush cache:rebuild` to check for updates.

Guide found [here](https://www.drupal.org/docs/updating-drupal/updating-modules-and-themes-using-composer)


### Appearance

Can upload custom logo and favicon through Appearance settings. Logos need to be resized before upload or size manually edited in file. If too large, Drupal will not give a warning but will just not display it.