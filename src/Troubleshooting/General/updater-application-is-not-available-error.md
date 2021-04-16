---
title: "Updater application is not available" error
labels: 2.2.x,2.3.x,Magento Commerce,how to,install,update,updater,web setup wizard
---

This article talks about the solution for the "updater application is not available" issue you might face when trying to update/install Magento using the Web Setup Wizard.

## Issue

The following message is displayed in the readiness check:

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](https://support.magento.com/hc/article_attachments/360037722712/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

### Affected products/versions

* Magento Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

 

## Solution

To resolve this issue, see if there is a <code class="highlighter-rouge">&lt;magento\_root>/update</code> directory that contains files and subdirectories. Otherwise, see [Set up the updater](https://devdocs.magento.com/guides/v2.3/comp-mgr/updater/update-updater.html).