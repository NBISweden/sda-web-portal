---
layout: article
title: Preparing metadata
key: preparing-metadata
sidebar:
  nav: prepare
---

Data submitted to FEGA Sweden must be described with proper metadata. Well
described datasets will be both easier to find and to use for other researchers.
The metadata in FEGA Sweden is divided in eight categories:

Study
: Information about the sequencing study

Samples
: Information about the sequencing samples

Experiments
: Information about the sequencing methods, protocols and machines. Experiments generate the linkage between samples and study. Only necessary for FASTQ and BAM/CRAM submissions.

Runs
: Samples, experiments and files are linked through runs - appropriate objects for FASTQ and BAM/CRAM submissions

Analysis
: References the analysis (BAM) files; associated with samples and study.

DAC
: Information about the Data Access Committee (DAC)

Policy
: Contains the Data Access Agreement (DAA); associated with DAC

Dataset
: Contains the collection of runs/analysis data files to be subject to controlled access; associated with Policy


Study, samples, DAC and Policy metadata can all be registered prior to uploading
files.

After the FEGA Sweden Helpdesk has decided to proceed with your submission
request you will receive credentials for the EGA Submitter Portal. Once you are
logged in to the portal, you should be able to start entering your metadata. 
Please note that some of the metadata only can be entered after data files have
been uploaded.

It is recommended that you start collecting your metadata as early as possible,
preferably before you start working on a submission. Consider storing the
metadata close to your data, as this might make the information easier to find
when you need it.

Read more about the metadata in the [EGA Submitter Portal documentation](https://ega-archive.org/submission/tools/submitter-portal).
To get an initial understanding of the metadata requirements, we recommend the
tutorial videos listed on the web page.


## Recommended workflow

In order to achieve an efficient submission process and to minimize the risk of
delays, always start with preparing the DAC and Policy objects at an early stage.
DAC, Policy and ethical permits of your study needs to be checked by the Swedish
FEGA helpdesk already in the beginning of the submission process.

In the EGA Submitter Portal, start by entering Study, thereafter Samples and
Experiments. When entering Runs, Samples and Experiments should be linked to
Runs. After this step, enter DAC and Policy. Finally, link Runs to DAC and
Policy to define your Dataset.

For detailed information on how to prepare metadata and how to use the EGA
Submitter Portal, please visit https://ega-archive.org/submission/tools/submitter-portal.
