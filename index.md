---
layout: article
titles:
    # @start locale config
    en      : &EN       Swedish Sensitive Data Archive
    # @end locale config
key: fega-sweden
---

The Swedish Sensitive Data Archive (SDA) is a service for permanent archiving
and sharing personally identifiable genetic and phenotypic data resulting from
biomedical research projects. As a national data repository, the SDA aims to
enable researchers to share information that need to be stored within the
Swedish jurisdiction. The repository is hosted by [National Bioinformatics
Infrastructure Sweden (NBIS)](https://nbis.se).

Data in SDA is strongly encrypted according to the standard
[Crypt4GH](https://www.ga4gh.org/news/crypt4gh-a-secure-method-for-sharing-human-genetic-data/),
and stored within Sweden in highly secure data centers. Non-sensitive metadata
is made publicly available to make datasets discoverable.

## Current status

We are now piloting a standalone instance of the repository for storing and
sharing.

In the future, the repository will also be integrated with the [Federated
EGA](https://ega-archive.org/federated) network to make data even more
discoverable and accessible at the same time as preserving the high data
protection.

## How is the SDA being developed?

The Swedish Sensitive Data Archive uses a software stack that has been
developed by [National Bioinformatics Infrastructure Sweden (NBIS)](https://nbis.se)
in collaboration with other Nordic ELIXIR nodes through the [Tryggve project](https://neic.no/tryggve2/)
funded by the [Nordic e-Infrastructure Collaboration (NeIC)](https://neic.no/)
and coordinated with Central EGA through the European research infrastructure 
[ELIXIR](https://elixir-europe.org/communities/human-data).

The entire stack is open source and can be audited.

## How is access to data controlled?

Access to data will be managed through a secure interface where each
data controller can review requests for access to data, and grant or
deny this access.
