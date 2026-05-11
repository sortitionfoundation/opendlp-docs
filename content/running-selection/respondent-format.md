---
title: "Respondent data format"
description: "Required format for respondent data"
---

To run a selection on OpenDLP you need to provide data on **targets** (or "categories") and data on **respondents** (or "people").

In each case your data is either a tab in a google sheet, or is a .csv file that you upload onto the system. Whether you use a google sheet or a .csv file, the required format is the same.

## Respondent data

A sample respondents file is [available to download](/files/Respondents_csv_example.csv). The following video goes through the key criteria to which your respondent data file must conform.

<video width="600" controls>
  <source src="/files/target_format.mp4" type="video/mp4">
</video>

These criteria are reproduced below.:

1. There is a column (typically the first column) which contains a unique and never-changing ID number for each respondent.
2. For each of the entries in the **category** column of the categories file, there is a column in the respondents file with that header.
   1. E.g. in the sample categories file, the category column contains five entries: *gender, age\_bucket, ethnicity, disability, colour\_bucket*. In the sample respondents file there are five columns with these headers.
3. For each column in the respondents file that corresponds to a stratification category, every single entry below the header must correspond to one of the listed values from the categories file.
   1. E.g. We saw above that our sample category file has three values for the *gender* category: *Female / Male / Non-binary or other.* If you look at column D in our sample respondents file, you will see that its header is *gender* and every entry below the header is one of *Female / Male / Non-binary or other.*
   2. E.g. Likewise in our sample category file, we had an *age\_bucket* category with values *0-17 / 18-24 / 35-34 / etc.* If you look at column K in our sample respondents file, you will see that its header is gender and every entry below the header corresponds to one of the values listed in the category file.

