# Flatpurge

A tool to delete leftover user data from [Flatpak](https://github.com/flatpak/flatpak) Applications you no longer have installed from your **Home Folder**.

**THIS TOOL DELETES DATA AND CAN BE DESTRUCTIVE. PLEASE USE WITH CARE.**

This tool works by iterating through directories in `$HOME/.var/app/` and running `flatpak info $app` on each.

This *may* not be fool-proof, so please review **VERY** carefully before you say *"yes"* to anything.

If `flatpak` returns a non-zero exit status, it means the app is (most likely) not installed.

**NOTE:** Any extra directories you or other software has created under `$HOME/.var/app` *WILL* be treated as a [Flatpak](https://github.com/flatpak/flatpak) Application Directory regardless.

## Usage

By default, `flatpurge` will only **list** unused app directories. You can choose to manually delete them.

Passing the `-d` or `--delete` argument will allow `flatpurge` to prompt you for each unused directory.

Passing the `-f` or `--force` argument as well will delete *all* unused directories **WITHOUT** prompting you. This is **NOT** recommended.

## Inspiration
Package Managers sometimes have a way of deleting residual configuration data (For example `sudo apt purge $PACKAGE`)

But one thing they've never done is offer the abillity to clean leftovers out of your **Home Folder**.

With [Flatpak](https://github.com/flatpak/flatpak) all data related to an application is stored nice and tidily under `$HOME/.var/app/$PACKAGE` under normal circumstances.

This means, if we can detect a folder for an app that isn't installed, we can **purge residual user data for that app**.
