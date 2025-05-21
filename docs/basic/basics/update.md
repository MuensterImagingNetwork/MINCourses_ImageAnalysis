# 4. Plugins installieren / Update Sites

!!! tip "Learning Objective"
    Understand how to install and manage plugins in Fiji and keep the software up-to-date.

## Introduction

Fiji (ImageJ) can be extended with a wide range of plugins that add new functionalities for image analysis, visualization, and data management. Staying up-to-date with these plugins and the core software helps you benefit from the latest features and bug fixes.

## Installing and Managing Plugins

* **Automatic Installation and Updates via the Fiji Updater:**
    * Go to `Help > Update...`
    * Fiji will check for available updates to the core application and all installed plugins.
    * To access more plugins, click "Manage update sites" in the updater window and enable the desired sites (e.g. "BioVoxxel", "OME", "CLIJ2", etc.). Update sites are community-maintained repositories with specialized tools.
    * After enabling sites, click "Close" and then "Apply changes" to install updates and new plugins.
    * Restart Fiji after updating.

* **Manual Plugin Installation:**
    * Download the plugin file (usually a `.jar`) from the developer's website.
    * Place the file in the `plugins` folder inside your Fiji installation directory.
    * Restart Fiji to load the new plugin.

* **Tip:** Regularly run the updater via `Help > Update...` to keep Fiji and your plugins current. This reduces compatibility issues and ensures access to the latest tools.

## Using Multiple Fiji Versions

It is possible—and often helpful—to use multiple Fiji installations in parallel by copying and renaming the Fiji installation folder. This is useful for important analyses or reproducibility, as some plugins or update site combinations can conflict or behave differently with updates. Keeping a backup of a "known good" Fiji version can help avoid interruptions in workflows if newly installed plugins cause issues.

---

_Note: Some plugins require additional dependencies. The updater usually installs these automatically when you have the relevant update sites enabled._