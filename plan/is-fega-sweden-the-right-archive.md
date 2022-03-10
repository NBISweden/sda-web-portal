---
layout: article
titles:
    # @start locale config
    en      : &EN       Is FEGA Sweden the right archive for my data?
    # @end locale config
key: is-fega-sweden-the-right-archive
sidebar:
  nav: plan
---

Before you start working on a submission to SDA, you should assess whether the
repository is suitable or not. This guide will help you to make this assessment.
If you need help with the assessment, please contact the <a href="mailto:ega-se@nbis.se">SDA Helpdesk</a>.

## Is my data of the right type?

The SDA aims to store the same kind of data as the Central EGA. You can read
more about data types and file formats at the [EGA website](https://ega-archive.org).

## Does my data require controlled access?

Sensitive personal information can normally not be shared publicly due to legal
and ethical constraints. The SDA enables sharing of sensitive personal
information under controlled access. This means that access to any submitted
file will be determined by a formal application procedure. If your data does not
require controlled access, you should consider submitting it to an alternative
repository, such as the [ENA](https://www.ebi.ac.uk/ena/browser/submit).

Read more about [how access data in SDA](/data-access.html).

## Do I have all the required metadata?

The metadata objects required for read submissions are as follows:

- **Study:** information about the sequencing study
- **Samples:** Information about the sequencing samples
- **Experiments:** Information about the sequencing methods, protocols and
  machines. Experiments generate the linkage between samples and study. Only
  necessary for FASTQ and BAM/CRAM submissions.
- **Runs:** Samples, experiments and files are linked through runs - appropriate
  objects for FASTQ and BAM/CRAM submissions
- **Analysis:** References the analysis (BAM) files; associated with samples and
  study.
- **DAC:** contains information about the Data Access Committee (DAC)
- **Policy:** contains the Data Access Agreement (DAA); associated with DAC
- **Dataset:** contains the collection of runs/analysis data files to be subject
  to controlled access; associated with Policy

Study, samples, DAC and Policy metadata can all be registered prior to uploading
files.

Collect your metadata as early as possible, preferably before you start working
on a submission. Consider storing the metadata close to your data, as this might
make the information easier to find when you need it.

Read more about the metadata in the [Submitter Portal documentation](https://ega-archive.org/submission/tools/submitter-portal)
at Central EGA. To get an initial understanding of the metadata requirements, we
recommend the tutorial videos listed on the web page.

## Am I allowed to share the data through SDA?

In order to share personally identifiable research data, you need to consider
all relevant legislations. For Swedish research projects, these include for
example the EU General Data Protection Regulation (GDPR) and the Swedish Ethical
Review Act (SFS 2003:460).

In preparation for submission you need to verify that a data processing
agreement between the data controller and Uppsala University is in
place. For convenience, we have already established [general data processing agreements](https://nbis.se/support/general-processing-agreements.html)
with some Swedish universities. If you are missing a general agreement for
your university, you may contact your Data Protection Officer to establish one.
