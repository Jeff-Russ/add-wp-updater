# add-wp-updater

`add-wp-updater` is a small script to compliment YahnisElsts's [plugin-update-checker](https://github.com/YahnisElsts/plugin-update-checker). Executing `add-wp-updater` from the working directory of you GitHub hosted plugin integrates YahnisElsts's library into your git project, keeps it up to date, and eases the process or incrementing and hosting updates.  

Instead of using git to actually distribute the update you create a `.zip` inside your repository which is served to WordPress from `https://raw.githubusercontent.com/`   

## Installation

From anywhere in your shell's `PATH` or at your git project root:  

    $ curl -O https://raw.githubusercontent.com/Jeff-Russ/add-wp-updater/master/add-wp-updater
    $ chmod 755 ./add-wp-updater

## First Run 

When you go to you project's root directory and run the script first time:  

1. plugin-update-checker is cloned into your project as `./plugin-update-checker/`
2. a directory `./dist/` is create to contain the json config file and `.zip` distribution
3. you are prompted with question to assemble the json config file
4. a zip of the entire project (excluding `./git/`, `./dist/` and `add-wp-updater` itself) is created and placed in `./dist/`
5. The main php file is searched for and the proper `require` statement is inserted

## Subsequent Runs

Each subsequent run of `add-wp-updater` (without flags) will:

1. run `git pull` in `./plugin-update-checker/`
2. you're given the option to update the json config file
3. a fresh zip of the project is created and placed in `./dist/`

You can optionally skip step #2 by calling:

    $ add-wp-updater --skip-zip

## Keeping plugin-update-checker up-to-date

Each time you run `add-wp-updater` in any any manner, `plugin-update-checker` will be updated if an update is available but if you like to do ONLY this you can run:  

    $ add-wp-updater --update-lib

This is handy if you have no other reason to update your plugin. If you find that there was an update available you can run it again without the option.  

