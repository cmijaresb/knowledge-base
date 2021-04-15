---
title: Exported products .csv file does not appear 
labels: Magento Commerce Cloud,export,exported,products,exportProcessor,how to,2.3.2,csv file
---

This article provides a fix for the issue where you try to export products to a .csv file in Magento Admin, but the file does not appear.

### Affected products and versions

* Magento Commerce Cloud 2.3.2

## Issue

Steps to reproduce

Prerequisites: The Add Secret Key to URLs option is set to _Yes_. The option is configured in the Magento Admin under Stores > Configuration > Advanced > Admin > Security.

1. In the Magento Admin, navigate to System > Data Transfer > Export. 
1. Select
    
    * Entity Type: _Products_
    * Export File Format: _CSV_
    * Field Enclosure: leave unchecked. 
    
    
    
1. Click Continue.
1. The following message is displayed: _"Message is added to queue, wait to get your file soon"_.

Expected result

The .csv file with the exported products is displayed in the grid in a couple of minutes.

Actual result

The .csv file with the exported products is not displayed in the grid in 10 minutes or more.

## Cause

A known issue with the Export functionality in Magento application part version 2.3.1. ## Solution

There are two possible solutions for the issue:

* Disable the Add Secret Key to URL option. 
* Run the the `` bin/magento queue:consumers:start exportProcessor `` command manually, and optionally configure it to be run by cron.

See details for both options in the following paragraphs. 

### Disable the the Add Secret Key to URL option

1. In the Magento Admin, navigate to Stores > Configuration > Advanced > Admin > Security.
1. Set the Add Secret Key to URLs option to _No._
1. Click Save Config. 
1. Clean cache under System > Tools > Cache Management or by running <code class="language-bash">bin/magento cache:clean</code> or in Magento Admin.

### Run the export command manually and optionally add it as cron job

To get the export file, run the `` bin/magento queue:consumers:start exportProcessor `` command. After running this, the file should be displayed in the grid.

 

To add the process as a cron job optionally, you must add the `` CRON_CONSUMERS `` variable to the `` .magento.env.yaml `` file.

#### Add process as a cron job (optional)

1. Make sure your cron is setup and configured. See [Set up cron jobs](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html) for details.
1. Run the following command to return a list of message queue consumers:
    
        ./bin/magento queue:consumers:list
    
    
1. Add the following to your `` .magento.env.yaml `` file in the Magento `` /app `` directory, and include the consumers you would like to add. For example, here is the consumer required for export processing:
    
    <pre><code class="language-yaml">stage:
  deploy:
    CRON_CONSUMERS_RUNNER:
      cron_run: true
      max_messages: 1000
      consumers:
        - exportProcessor
</code></pre>
    
    Then push this updated file and redeploy your environment. Also reference [Add custom cron jobs to your project](https://devdocs.magento.com/cloud/configure/setup-cron-jobs.html#add-cron).

<p class="info">If you cannot find the <code>.magento.env.yaml</code> file for your environment, and you think it was deleted, you need to create a new <code>.magento.env.yaml</code>. It might be empty initially, you can add info there as required. Reference the following Magento DevDocs articles: <a href="https://devdocs.magento.com/cloud/project/magento-env-yaml.html">Build and deploy</a>, <a href="https://devdocs.magento.com/cloud/env/variables-intro.html">Environment variables</a></p>

<p class="info">On Magento Commerce Pro projects, the <a href="https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html#verify-cron-configuration-on-pro-projects">auto-crons feature</a> must be enabled on your Magento Commerce Cloud project before you can add custom cron jobs to Staging and Production environments using <code>.magento.app.yaml</code>. If this feature is not enabled, <a href="https://support.magento.com/hc/en-us/articles/360019088251-Submit-a-support-ticket">create a support ticket</a>, to have the job added for you.</p>

 
 