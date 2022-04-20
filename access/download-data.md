---
layout: article
title: Download data
key: download-data
sidebar:
  nav: access
---


This sections provides intructions on how to download the data files. The instructions
contain the following steps: 

* Prepare your system
* Generate public and secret key
* Decrypt the files
* Validate the decrypted files


### Prepare your system

In order to download and decrypt files, you need to first get the tool
[crypt4gh](https://www.ga4gh.org/news/crypt4gh-a-secure-method-for-sharing-human-genetic-data/). 


### Generate Public and Secret Key

The first step is to generate a keypair using the `crypt4gh` encryption tool. This can be done using the following command. There are two keys generated - `user.sec` is the secret key and `user.pub` is the public key. You must reply to the FEGA-SE helpdesk by sending them the generated public key - `user.pub`. 

```bash
crypt4gh-keygen --sk user.sec --pk user.pub
```

### Decrypt the data files

You recieve an email from the FEGA-SE helpdesk that contains a URL. This URL contains links to download the encrypted data files. Get our [script for downloading data](download-data-script.html) and then use the following command.


```bash
./download_data.sh
```
In case the name of the text file is changed or it exists in a different path than the download script, run:

```bash
./download_data.sh path/filename
```

This downloads all the encrypted files from the text file and allows it to maintain the structure of the dataset. Next, you must transfer the downloaded encrypt files and the secret key to a secure environment. Use the following command to decrypt files inside the secure environment using the secret key - `user.sec` that was generated in the previous step.

```bash
crypt4gh decrypt --sk user.sec < encrypted-file.c4gh > encrypted-file
```
Ensure that the `encrypted-file.c4gh` and the corresponding `encrypted-file` are in the same folder. 


### Validate the decrypt files

The next step is to validate the decrypted files. This can be done using calculating checksums of the downloaded files. Executing the `download_data` script downloads a file `checksums_list.sha256` that contains the list of checksums. Following command is used to validate the decrypted file.

```bash
sha256sum -c checksums_list.sha256
```

In the end, you must reply to FEGA-SE helpback to confirm successful download and decryption.
