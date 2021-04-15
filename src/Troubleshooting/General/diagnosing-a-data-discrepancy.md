---
title: Diagnosing a data discrepancy
labels: troubleshooting,Magento Business Intelligence,data discrepancies
---

This article provides solutions for troubleshooting discrepancies between a Magento BI report and a query or third-party report.

Depending on the complexity of your analysis, generating the corresponding Magento BI report may require familiarity with a number of different facets of the platform. This checklist and the related links will help you understand the logic behind your report, allowing you to identify the source of any discrepancies. 

1. If another member of your team created the report, begin by confirming the objective and parameters of their analysis
1. Generate expected data points to compare to the Magento BI report based on a query, a third-party reporting tool, or a formula
1. Review and confirm the [metric](https://support.magento.com/hc/en-us/articles/360016504592-Create-metrics) definition(s), either from the metric link in Report Builder or by visiting the [System Summary](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) tab:

* Data table
* Operation
* Operand column, including its calculation if it is derived (via System Summary)
* Timestamp
* For subscription metrics: start and end dates
* Filters, including those contained in any [filter sets](https://support.magento.com/hc/en-us/articles/360016505492-Create-filter-sets) applied
* Review and confirm other data manipulation within the report:

<li>Formulas calculated</li>
<li><a href="https://support.magento.com/hc/en-us/articles/360016730831-Create-analyses-using-the-Report-Builder#groupsegment">Groupings</a></li>
<li><a href="https://support.magento.com/hc/en-us/articles/360016730831-Create-analyses-using-the-Report-Builder#filtersperspectivetime">Perspectives</a></li>
<li><a href="https://support.magento.com/hc/en-us/articles/360016730831-Create-analyses-using-the-Report-Builder#settime">Time options</a></li>
<li>For <a href="https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis">cohort analysis</a>: Cohort date</li>
<li>For <a href="https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis">cohort analysis</a>: Cohort perspective</li>
<li>If the discrepancy involves recent data, confirm the latest available data point by consulting the Update Details section on the Connections page</li>
<li>If a metric used in the analysis is built on a table from your database where rows are ever deleted from that table, confirm with the Magento BI Support Team that the table is being checked for deleted rows, as well as the frequency of the recheck and the <a href="https://support.magento.com/hc/en-us/articles/360016731631-Best-practice-Optimizing-your-database-for-analysis">replication method</a> for the table</li>
<li>Similarly, if columns used in the analysis can be modified after a row is added, confirm with support that these columns are being <a href="https://support.magento.com/hc/en-us/articles/360016506452-Configuring-data-rechecks">checked for modifications</a>, as well as the frequency of the recheck</li>

Still stumped? Don't worry - we're here to help. Send us a request using [these instructions](https://support.magento.com/hc/en-us/articles/360016505312).