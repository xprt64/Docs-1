---
title: "Upgrading to 2.2.x"
_old_id: "1123"
_old_uri: "2.x/administering-your-site/upgrading-modx/upgrading-to-2.2.x"
---

- [Introduction](#Upgradingto2.2.x-Introduction)
- [Media Sources](#Upgradingto2.2.x-MediaSources)
- [Static Elements](#Upgradingto2.2.x-StaticElements)
- [Dashboards](#Upgradingto2.2.x-Dashboards)
- [Other Notables](#Upgradingto2.2.x-OtherNotables)
  - [Sorting Contexts in the Tree](#Upgradingto2.2.x-SortingContextsintheTree)
  - [Primary User Group](#Upgradingto2.2.x-PrimaryUserGroup)
  - [Minify in the Manager](#Upgradingto2.2.x-MinifyintheManager)
  - [Form Customization Tweaks](#Upgradingto2.2.x-FormCustomizationTweaks)
  - [Comment Tags](#Upgradingto2.2.x-CommentTags)
  - [Moving TVs Below the Content Panel](#Upgradingto2.2.x-MovingTVsBelowtheContentPanel)
  - [Upgrading/Installing via Command Line](#Upgradingto2.2.x-Upgrading%2FInstallingviaCommandLine)
  - [Pre-processing Element Default Properties and Property Sets](#Upgradingto2.2.x-PreprocessingElementDefaultPropertiesandPropertySets)
- [See Also](#Upgradingto2.2.x-SeeAlso)



## Introduction

This article describes the major changes to MODX Revolution in the 2.2 release. Please review these changes when upgrading your sites to 2.2 from a prior MODX Revolution install.

## Media Sources

A large change in 2.2 is the introduction of [Media Sources](administering-your-site/media-sources "Media Sources"). These abstract the "Files" tab in MODX to allow multiple sources for the Files tree, such as the filesystem, an S3 bucket, or other source types. They integrate directly into most of the MODX manager, including the MODx.Browser, [Template Variables](making-sites-with-modx/customizing-content/template-variables "Template Variables"), and general file manipulations. What does this mean for an upgrade?

It means that **all filemanager\_\* Settings** **_and_** **basePath/baseUrl TV input options are deprecated**. None of them are in active use by the MODX manager anymore. Sources now determine the basePath and baseUrl of the tree, rather than the Settings or TV input options. This "source-centric" approach allows much more stable scalability and usage.

MODX will attempt to create new Media Sources for any filemanager\_\* settings and any custom image/file TVs that had a custom basePath. In the case of filemanager\_\* system settings, the default Source will have its baseUrl and basePath altered. In the case of TV input options with custom basePath parameters, there will be new Sources that automatically associate with those TVs.

Any filemanager\_\* User Settings will need to be manually migrated, as the idea of User-specific source basePaths no longer exist. Please use ACLs on the Media Source with a User Group, which you can [learn how to do so here](administering-your-site/media-sources/securing-a-media-source "Securing a Media Source").

## Static Elements

MODX 2.2 introduces "Static" Elements, which are Elements that are located on the filesystem, through a Media Source. To use a Static Element, simply create an Element (Chunk/Snippet/Template/etc), and then check the "Is Static" box. This will then popup two fields:

- **Static Source** - This field specifies the Media Source to use when looking up the Static File. Select None to specify an absolute path to the file.
- **Static File** - This field is the path to the file, relative to the media source you selected (or None for absolute paths). You can use tags in this field, such as System Settings, as well.

For example, if you selected a File System Media Source with a relative base path of 'assets/', and then specify the Source File as "templates/test.tpl", it will look for the Template file in "/path/to/my/modx/assets/templates/test.tpl".

## Dashboards

You will note that your main Dashboard will look slightly different. The basic widgets and functionality will be the same; however, you will now be able to create Custom Dashboards for different User Groups, and rearrange and assign Widgets to them. Please refer to the [Dashboards](administering-your-site/dashboards "Dashboards") documentation.

## Other Notables

### Sorting Contexts in the Tree

Sorting of Contexts is now available in the Resources tree; however, this is off by default. To turn it on, set the "context\_tree\_sort" System Setting to Yes, and then change the "context\_tree\_sortby" field to "rank". This will allow you to drag/drop sort the Contexts in the tree.

### Primary User Group

Users can now have a "Primary" User Group that they belong to. This is the User Group that they are assigned to with rank of 0. If they are only in one User Group, that group will be their Primary Group.

### Minify in the Manager

The MODX manager now uses [Google Minify](http://code.google.com/p/minify/) to automatically compress the CSS and JS in the manager. By default this is on; if, however, you would like to turn it off, you can do so by setting the "compress\_js" and "compress\_css" System Settings to 0.

### Form Customization Tweaks

Due to the new user interface improvements on the Resource Editing screen, Form Customization can now target specific columns in tabs to move TVs to. Their IDs are now listed under the "Tabs" tab when editing a Form Customization Set.

### Comment Tags

MODX users can now use comment tags in their content:

``` php 
[[- comment goes here]]
```

Anything within one of these tags will be removed prior to the page rendering.

### Moving TVs Below the Content Panel

In 2.2, you can also move Template Variables below the Content panel when editing them in a Resource. This is done by simply changing the _tvs\_below\_content_ setting to "Yes".

### Upgrading/Installing via Command Line

In 2.2, MODX is installable and upgradable from the command line. See [Command Line Installation](getting-started/installation/command-line-installation "Command Line Installation") for more information.

### Pre-processing Element Default Properties and Property Sets

MODX developers and users can now tell specific Elements to pre-process any MODX tags in default property and property set values. When checked on the Properties tab of an Element, the Element will attempt to parse all tags that appear in default property values or values assigned by property sets so that the behavior is the same as if the property was set in the tag string itself. Otherwise, the behavior is the same: tags in default property values or property set values are passed directly to the Element without being processed.

## See Also

1. [Troubleshooting Upgrades](administering-your-site/upgrading-modx/troubleshooting-upgrades)
2. [Upgrading to 2.2.x](administering-your-site/upgrading-modx/upgrading-to-2.2.x)
3. [Upgrading from 2.0.x to 2.1.x](administering-your-site/upgrading-modx/upgrading-from-2.0.x-to-2.1.x)
4. [Upgrading from Versions Earlier than 2.0.5](administering-your-site/upgrading-modx/upgrading-from-versions-earlier-than-2.0.5)
5. [Upgrading to Revolution 2.0.0-rc-2](administering-your-site/upgrading-modx/upgrading-to-revolution-2.0.0-rc-2)
6. [Upgrading from MODx Evolution](administering-your-site/upgrading-modx/upgrading-from-modx-evolution)
  1. [Functional Changes from Evolution](administering-your-site/upgrading-modx/upgrading-from-modx-evolution/functional-changes-from-evolution)