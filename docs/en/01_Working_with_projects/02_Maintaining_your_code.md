title: Maintaining your code
summary: Best practices for keeping your codebase up to date

# Maintaining your code

Let's step through best practices in building your CWP site that will yield the most maintainable codebase.

## Starting off with the recipe

We recommend to start your development by installing via the [cwp-installer](https://gitlab.cwp.govt.nz/cwp/cwp-installer/) using Composer. 
This already sets up a reasonable structure to your site that will make future maintenance easier.

See [Setting up your project](setting_up_your_project).

## Using the cwp modules

Starting with the installer will also imply you use `cwp/cwp` and `cwp/cwp-core` modules on your site. 
This is where the updates to dependencies and essential code required for running your website on CWP infrastructure will be
made available. It will make it much easier to keep your SilverStripe CMS up to date and take advanatage of new feature if you use these modules as the basic of your website.

See [Recipes and supported modules](recipes_and_supported_modules) for more details.

## Maintaining modules using Composer

It's crucial that you don't modify the module code in place, nor commit this code into your site's repository.
Modules are meant to be reusable between multiple agencies, so if there is a problem with a module, submit a pull
request to the open source community (or file a bug report with the Service Desk if you think it's a problem
with CWP modules).

This makes it easy to maintain the site by switching module versions at desired moments so this doesn't happen randomly.
Deploynaut (our deployment tool) will never modify the module versions listed in `composer.lock`, so it's up to the
site developer to choose right versions via `composer.json`, and to run `composer update` in the right moments.

You can also create private modules in GitLab for even better modularity. See [working with modules](working_with_modules)
for more information on module creation, inclusion and sharing.

## Security patches

You need to keep your codebase's dependencies updated with respect to the patch or sub-patch releases of the recipe to
receive immediate security patches.

This is relatively easy - if your `composer.json` is configured as in the installer, it should be as easy as running
`composer update`, doing a smoketest and pushing to the upstream. See the [Upgrading](upgrading) guide for instructions.

See [Recipes and supported modules](recipes_and_supported_modules) for more information on versioning and on how to keep your instance secure.

See [infrastructural considerations](infrastructural_considerations) for hints on how to keep your instance stable.