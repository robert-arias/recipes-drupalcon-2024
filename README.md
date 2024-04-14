# Distributions and Recipes DrupalCon 2024

This is a bare bones Drupal site with the required configuration and modules to support Drupal recipes. This site was installed using the `Minimal` profile.

## Prerequisites
- [Composer](https://getcomposer.org/)
- [Lando](https://lando.dev/)

## Installation
- Run `lando start` to start the development environment.
- Run `lando composer install` to install the required dependencies.
- Run `lando drush si --existing-config -y` to install the site.

## Install Standard Recipe
- Go to the `web` directory.
- Run `lando php core/scripts/drupal recipe core/recipes/standard`
- Done! We don't need to unpack dependencies.

## Recipe install on top of minimal profile issue
Currently, if you install a recipe on top of a site with the `Minimal` profile, there will be a duplication of theme blocks. This is a [known issue](https://www.drupal.org/project/distributions_recipes/issues/3436143). The issue is due to another [Core issue that has been documented](https://www.drupal.org/project/drupal/issues/3105597).
To sum it up, this results from Drupal core cloning the blocks of the current theme when a new theme is enabled. Since the recipe is installed on top of `Minimal`, then blocks from the `Stark` theme are duplicated into the admin and frontend themes.

[The phase 2](https://git.drupalcode.org/project/distributions_recipes/-/blob/1.0.x/docs/recipe_roadmap.md?ref_type=heads#phase-2) of Drupal recipes is aiming to add the option to install Drupal sites from recipes, without the need of having first an existing site.