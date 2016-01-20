---
layout: documentation
title: Process for data analytics production
permalink: /documentation/process/
order: 1
---

*Draft, January 2016*

The aim of this document is to help streamline the production of data analytics. It should help make the initial data request simpler and more efficient, as well as make it easier to move through the steps from initial data request, to analysis, to presentation.

It should not be seen as a set of rules that must be followed in the production of any analysis, and it should also definitely not discourage experimentation or innovation. Rather, it should be seen as a rough summary of our evolving thinking on how to go about this process. It should help as a guide to producing data analytics in new country contexts but will remain a draft or living document for some time as we learn how best to do this.

It assumes as the starting point demand and interest from country-level stakeholders.

Needless to say, we would warmly welcome feedback on this document: <team@procurement-analytics.org>

## 1. Data requests

Data requests are tricky because:

* it may be unclear exactly what sort of analysis may be desirable (and this set of desired analysis will likely evolve quite rapidly over time)
* it may be unclear what data is required from which organisations to conduct any given set of analysis
* it is hard to know exactly what data is available
* it is hard to know where the data is held (and it may be held by multiple organisations)

Some of these issues can be fairly straightforwardly mitigated against, and others will likely improve over time as we get better at understanding the relationship between specific pieces of information and discrete areas of analysis.

The most obvious way to address all of these issues is to ask for a full dump of the existing procurement database. However, those holding the data may be wary of doing this for a number of reasons (required technical knowledge, confidentiality, data protection, wariness around intended use of the data).

Given these constraints, in most cases, it will likely be necessary to itemise the fields required for specific sets of analysis in a data request. The data request should respond directly to identified priority areas of analysis &ndash; probably focusing on 2-3 core problem statements initially &ndash; and should take care to avoid excessive burden on those holding the data. It will be important to establish a good working relationship.

### Process for data requests

Step | Description
---- | -----------
1.1 | **Confirm who needs to be involved**: who are the stakeholders that we need to work through / with, and how would they like to work?
1.2 | **Agree areas of analysis**: discussion with the country what are the most pressing procurement challenges. Agree on a list of 2-3 priority areas for analysis. Check whether a full database dump may be possible at this stage. Ask about any analysis of procurement system to date.
1.3 | **Check for other stakeholders' data requirements**: consider if there are any other stakeholders who require data in order for the data request and analysis to proceed; if so, reach out to them and ask that they provide their list of required fields (or areas of analysis) within a clear timeframe.
1.4 | **Check for existing analysis of the procurement system or scrapers**: check to see what existing analysis has been done of the procurement system, including by government, CSOs and World Bank staff. Is there any analysis we can build on? Check if any scrapers exist of the procurement portal, as this will be helpful for understanding the range of data fields that may be available.
1.5 | **Draw up a list of fields required for desired analysis**: use the analysis/field spreadsheet to obtain the set of fields that are likely required for the set of desired analysis. Is there anything additional that other stakeholders wanted included in step 1.3?
1.6 | **Share a first draft of the data request informally with those holding the data**: ensure that the data request would accurately address their procurement challenges and that the data request would not be overly burdensome.
1.7 | **Share the final data request formally with the government**: based on feedback received, share the final data request, through appropriate channels, determined in step 1.1.

## 2. Data validation

When we receive the first set of data, it's important to ensure we know what it means and how we should interpret it. This may seem a slightly heavy-handed step, but the aim is to make things much faster later (as it will be clear which columns we could use for other or more detailed areas of analysis) as well as avoiding mistakes (if we misinterpret columns).

We also want to get a rough overview of the quality of the data at this stage. This will help to understand if what we've received is fairly complete, or if there are any obvious extraction or processing areas that could be quickly fixed before proceeding.

### Process for data validation

Step | Description
---- | -----------
2.1 | **Describe list of files received**: list filesize, last modified dates, and basic description of file contents. What does each row mean? What is the scope of the data (does it contain both tenders and simplified procurement from all ministries, and from all levels of government?). Can anything be inferred from the filenames (e.g. `tenders_2014.xls` means X). Provide our best guess at each of these questions as a list of declarative statements.
2.2 | **Confirm column header definitions**: provide our best guess at the meaning of each column header. Check where column headers should be identical (e.g. multiple sheets providing the same sort of data) and confirm any discrepancies. This should be provided as a draft version of definitions, with a few rows of sample data. The definitions should probably be fairly short.
2.3 | **Define codes used in specific columns**: we may not have to do this for all columns, but where we are likely to rely on the codes in certain columns as part of our analysis, we should confirm our understanding of the meaning of these codes.
2.4 | **Basic data quality descriptors**: provide summary of number of missing values; data types of columns (and % of rows deviating from these data types); granularity of CPV codes; illogical values (e.g. negative numbers where positive ones should be expected). Also provide the total value of procurement in each year as a sense-check.
2.5 | **Check we have all the data we need for required analysis**: we could check against the initial data request, to confirm we have all the data we requested. If there are missing fields, discuss whether that will make a significant difference to our overall analysis.
2.6 | **Confirm the above components with country counterparts**: check we're on track with our understanding before proceeding further. This should be a single fairly concise email with a couple of attachments.

## 3. Initial data processing / wrangling / clean up

Once we've confirmed our understanding of the data, we will need to do some processing, wrangling, and possibly clean up of the data to get it ready for analysis. Keeping wrangling and clean up separate from detailed analysis will help to ensure clarity on exactly what is being done at each point, as well as providing a consistent basis for all of the analysis.

### Process for initial data processing

Step | Description
---- | -----------
3.1 | **Integrate dataset**: where the source data breaks data into several files that should logically be part of the same table, combine this data. Provide a source column to identify the source table for each row. At least the core tables (one row per tender) should be integrated together. This will probably vary a lot by country. 
3.2 | **Consider re-labelling column names based on [Open Contracting](http://ocds.open-contracting.org/standard/r/1__0__0/en/schema/reference/)**: consider whether using OCDS field names may help to provide greater clarity or simplicity for the dataset. This shouldn't be a thorough or precise mapping at this stage – the goal is simply to use OCDS as a framework by which we can gain a clearer understanding of the nature of the data.
3.3 | **Keep a record of any significant data clean up**: where data has to be significantly reprocessed, ensure this is clearly marked in the source code. Capturing this information will also help us when we do occasional blogs summarising particular areas of cleaning / wrangling.
3.4 | **Keep data analysis scripts separate**: data analysis should not be interspersed within the wrangling and clean up scripts to the extent that this is practical – this will help to retain clarity in each of the steps. 
3.5 | **Generate basic overview analysis**: this should contain the total value of procurement in the dataset, the total number of projects, the value in each category (goods, works, services) and the way this breakdown in category was defined (e.g. goods = CPV codes 0-44, etc.).

## 4. Detailed analysis

Now that we have a solid, clean dataset with clear definitions, we should be able to proceed rapidly with the detailed analysis. At the outset, we should have a broad discussion about areas of analysis we could conduct (within the parameters of the 2-3 priority areas for analysis that came out of discussions with country partners). This should preferably include both experts on procurement in general as well as procurement in that country.

Once we've agreed the broad strokes of analysis, we will begin iteratively developing analysis over 1-2 week sprints. The analysis will be conducted in R and will output a PDF file as a single repository for our evolving analysis. This should progressively develop a set of content that can be used in a first mission / visit to the country. The analysis should be clear about assumptions, cuts and filters used on the data to generate different charts and tables. It should drive towards the problem definitions and priority areas of analysis that arose from earlier discussions with country counterparts.

By the end of this process, we should have all the content we need for a presentation that contains a clear set of findings and a clear narrative that responds to the agreed priority areas of analysis and problem statements. The priority should be building up the content rather than polishing the language or presentation &ndash; the PDF file itself does not need to be shared externally at this stage.

### Process for detailed analysis

Step | Description
---- | -----------
4.1 | **Discussion of detailed areas of analysis**: dig into the problem definitions and priority areas of analysis outlined by the country and explore ways of addressing these issues through the analysis.
4.2 | **Agree detailed areas for analysis**: the detailed areas of analysis should be agreed among the analysis team following the broader meeting, probably in bullet-point form.
4.3 | **Iterative development of analysis**: check in once per week on progress of analysis and discuss focus of future sprints every 1-2 weeks.
4.4 | **Develop presentation in parallel**: once we have a decent set of analysis, we should begin shaping the presentation, as this will help make clear if there are significant gaps in the content we need.

## 5. Presentation of analysis

The presentation should summarise the findings of the analysis we've reached thus far, responding to the priority areas of analysis previously identified. It should provide a narrative and some suggested further areas for analysis.

We need a nice-looking presentation that will help to convey the analysis but which will also be flexible and easy to edit at short notice. This is particularly important while on mission, if we discover any issues with the analysis or with the way in which it would be received.

Standard presentations can use something like InDesign where the content does not need to change. However, presentations containing detailed analysis must be in PowerPoint so that they can easily be edited. We can use a PowerPoint template that has a similar look and feel to the InDesign presentations generated thus far. We can also get graphics generated in InDesign and insert them directly into the presentation slides.

### Process for presentation

Step | Description
---- | -----------
5.1 | **Develop a PowerPoint template**: we need a standard PowerPoint template particularly for use in missions / country visits.
5.2 | **Generate early skeleton presentation**: early on in the detailed analysis, put together the bare bones of a presentation with some of the findings to date, in order to help work out what further analysis is required.
5.3 | **Discuss skeleton presentation and put together final version**: towards the end of the detailed analysis phase, discuss and put together the final version of the presentation.
5.4 | **Generate static graphics and polish presentation**: using data generated in the detailed phase, generate figures and tables and check formatting.

## 6. Dashboard

The [dashboards](http://mexico.procurement-analytics.org) are a useful tool for wider outreach and for generating further interest in the more detailed analysis. The government could also use them as as basis for their own dashboards (the [source code](https://github.com/procurement-analytics/procurement-analytics/tree/mexico) is all published and openly licensed). 

Given the need to focus on the core analysis, it is probably not an immediate short-term priority to generate further Dashboards, so streamlining the process of visualising the analysis on such a dashboard will not be considered in this document at this stage. 

We will revisit this later as demand for dashboards arises, and as we move to later stages of capacity-building and ensuring that the analysis is sustainable and replicable by others. We will also consider later in this section the process for moving towards making the data accessible to others through OCDS (beyond the initial light-touch mapping in step 3.2). 

******

## General approaches to software development

* Modular
* Separate data wrangling and cleanup from queries onto that data
* Modularise individual data queries and analysis (e.g. one per file, or using functions that are called at the relevant time)
* DRY, provide re-usable functions instead of in-line coding where possible
* Comments for each function and documentation – what are the assumptions / filters / cuts
* Use Github for version control and collaboration
