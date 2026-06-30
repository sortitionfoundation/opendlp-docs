---
title: "Target data format"
description: "Required format for target data"
---

To run a selection on OpenDLP you need to provide data on **targets** (or "categories") and data on **respondents** (or "people").

In each case your data is either a tab in a google sheet, or is a .csv file that you upload onto the system. Whether you use a google sheet or a .csv file, the required format is the same.

## Target data

A sample target data file is [available to download](/files/Categories_csv_example.csv). The following video goes through the key criteria to which your target data file must conform.

<video width="600" controls>
  <source src="/files/target_format.mp4" type="video/mp4">
</video>

These criteria are reproduced below.

1. There are columns headed **category**, **name**, **min** and **max**. (Other columns may be included – we recommend having a column for **Notes** where one keeps track of any key decisions to do with target-setting. However this is not mandatory)
2. The **category** column contains the name of the various stratification categories – e.g. *gender, age, ethnicity etc.* – for which we will be setting targets.
3. The **name** column contains the possible values of the various categories.
   - E.g. for the *gender* category, in our sample file we consider values *Female, Male* and *Non-binary or other*.
   - E.g. in our sample file we consider the age of respondents in terms of various "buckets". Hence we call this category *age\_bucket* and the possible values are *0-17, 18-24, 25-34* and so on.
   - Note: it is vitally important that every single person in your respondents pool can be assigned exactly one of the values listed in the Categories file for each category.
4. The **min** and **max** values are numerical values which specify the minimum and maximum number of people you want to select with the given category value.
   - E.g. For the *gender* category and the *female* value, we might set min=10 and max=11.
5. In order for the selection to be possible:
   1. The number of people to be selected must be greater than or equal to the sum of the **min** values for each category.
   2. The number of people to be selected must be less than or equal to the sum of the **max** values for each category.
   - E.g. if we say we want to select 20 people for an event, but we specify that we want **min 11 older** and **min 11 younger** people, **total min = 22**, then these numbers are in conflict with each other.
   - Note: the requirements at 5.1 and 5.2 imply that the different max and min values must not be in conflict with each other, e.g. if we say we want a total max of 25 people in the **gender** category values, and a total min of 30 people in the **age** category values, then these numbers are in conflict with each other.


