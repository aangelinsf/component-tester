# Using component-tester

This project provides a test harness to work with components and other Drupal features so that you can
experiment to see what breaks. It contains some useful modules plus some example content.

## Prerequisites

Everything is set up to work with Lando. Make sure that's on your machine by [installing it](https://docs.lando.dev/basics/installation.html).
 
If you don't have Lando you'll
need to create a database in your local MySQL instance and change the database string in the
sites/default/settings.php file.

## Usage

Download and unpack the zip archive. Use the following commands to:
1. Move into the project directory 
2. Start a Lando container for the project.
3. Perform a system install using the profile included with the project. This enables the modules and imports 
the configuration; it also imports some content using the [default_content](https://www.drupal.org/project/default_content).
4. Import the custom blocks with the Structure Sync module's `import blocks` command (ib). Enter '3' (Force) when asked.

```
cd component-tester
lando start
lando drush si component_tester --existing-config --yes --db-url="mysql://drupal8:drupal8@database/drupal8"  --account-name=admin --account-pass=password
lando drush ib
```
Once the installation finishes, you can log in by visiting 
http://component-tester.lndo.site/user/login and using "admin" / "password" as the credentials.

The configuration sync directory is in web/profles/component_tester/config/sync.

## Exporting blocks

If you want to export blocks, use the Structure Sync export-block drush command then export to the sync directory:
```
lando drush eb
lando drush cex
```
