---
layout: article
title: Uploading data
key: uploading-data
sidebar:
  nav: submit
---

If you are using the [Bianca Cluster](https://www.uppmax.uu.se/resources/systems/the-bianca-cluster/)
at UPPMAX for analysing your data, please follow our specific instructions for
[uploading data from Bianca](bianca.html).
{:.info}

This guide contains instructions on how to upload data to FEGA Sweden. We will
take you through the process step by step. The guide comprises four major
steps:

* [Installing the crypt4gh tool](#installing-the-crypt4gh-tool)
* [Installing the s3cmd tool](#installing-the-s3cmd-tool)
* [Encrypting files](#encrypting-files)
* [Submitting files](#submitting-files)


## Installing the crypt4gh tool

1. Download the `crypt4gh` executable for your operating system from the
   [elixir-oslo GitHub repository](https://github.com/elixir-oslo/crypt4gh/releases/tag/v1.3.0)
  
   If you are on Linux, the command might look something like this:

   ```bash
   wget https://github.com/elixir-oslo/crypt4gh/releases/download/v1.3.0/crypt4gh_linux_x86_64.tar.gz
   ```

2. Extract the binary by using the `tar` command:

   ```bash
   tar -xvzf crypt4gh_linux_x86_64.tar.gz
   ```
   The `crypt4gh` executable should now be in the same directory as the
   downloaded file.
    
3. Make sure that you have the correct version of `crypt4gh`:

   ```bash
   ./crypt4gh --version
   ```

## Installing the s3cmd tool

1. Download the `s3cmd` binary for your operating system. This is the tool you
   will for uploading your files.

   - [binaries for Linux and macOS](https://github.com/s3tools/s3cmd/releases/tag/v2.2.0)
   - [binaries for Windows](https://www.s3express.com/download.htm)

   If you are on Linux, you may for example type the following command:

   ```bash
   wget https://github.com/s3tools/s3cmd/releases/download/v2.2.0/s3cmd-2.2.0.tar.gz
   ```

2. Check your python version

    The `s3cmd` tool requires Python version 3 or higher to be installed on your
    system. Check that you have the right Python version by typing the following
    on the command-line:

    ```bash
    python --version
    ```

    If the version is `2.X.X`, go to the next step. Otherwise, go directly to
    step 3.

3. Create a virtual environment with Python 3
​
   The python virtual environment tools come bundled with Python since version
    3.4, and ​the syntax is the same on all platforms.

   ```bash
   python3 -m venv venv
   ```

   This will create a folder called `venv` under the current directory. The
   environment can be activated by using a simple command (this command has to
   be run every time a new terminal window is opened):​

   To activate the environment on Linux and macOS:
    ​
   ```bash
   source venv/bin/activate
   ```
  
   To activate the environment on Windows:

   ```PowerShell
   .\venv\Scripts\activate
   ```

    **Note:** PowerShell doesn't normally allow script execution, and you may
    need to run the following command before you can activate the
    virtual environment:

    ```PowerShell
    Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
    ```
  

3. Extract the binary using the tar command

   ```bash
   tar -xvzf s3cmd-2.2.0.tar.gz
   ```

   The executable should be under the `s3cmd-2.2.0` directory. Make sure that
   you have the correct version running by running the following command:

   ```bash
   ./s3cmd-2.2.0/s3cmd --version
   ```

   You may get an error looking something like this when you try to run the
   `s3cmd` command:

   ```bash
   ImportError trying to import dateutil.parser.
   Please install the python dateutil module:
   $ sudo apt-get install python-dateutil
   or
   $ sudo yum install python-dateutil
   or
   $ pip install python-dateutil
   ```

   If this happens, run the following command inside the environment and then
   try running the `s3cmd` command again:

   ```bash
   pip install python-dateutil
   ```


## Encrypting files

1. Download the crypt4gh public key

   For FEGA Sweden to be able to read the uploaded files, they need to be
   encrypted with the correct public key. This key can be downloaded from this repository with this command:

   ```bash
   wget https://raw.githubusercontent.com/NBISweden/EGA-SE-user-docs/main/crypt4gh_key.pub
   ```

2. (Optional) Create a personal key pair​

   The creation of a key pair can be done with crypt4gh. Run the following
   command, replacing [my-key] with the name of the key (can be anything). Then,
   specify a passphrase when it is requested:
​
   ```bash
   crypt4gh generate --name=[my-key]
   ```

   To verify that the key pair was created, run the `ls` command and make sure
   the keys you specified exist in the folder.

3. Encrypt the files

   Now that you have the public key, and the tools you need, you can encrypt the
   submission files. An encryption key will be created automatically by the
   tool, but if you prefer to use a specific key, you can provide one using the
   `-s` argument.

   ```bash
   ./crypt4gh encrypt -p crypt4gh_key.pub -f [my-file] [-s [my-key].sec.pem]
   ```

## Submitting files

Once your files are encrypted, you are almost ready to start uploading them.
There is just one more thing that is needed: checksums for all the files.

1. Calculate file checksums

   Once the files have been uploaded, they need to be validated, which will require
   you to enter md5 and sha256 checksums for each file. To prepare for this later
   step, it's advised to calculate checksums for all files as you upload them.

   Check out our short guide on [calculating file checksums](checksums.html) for
   details.
​

2. Obtain the configuration file

   The s3cmd tool requires a configuration file with the relevant settings. You
   can get the configuration file by [logging in to our service with your Elixir ID](https://login.sda.nbis.se/).

   If you choose not to use the downloaded configuration file, we recommend
   setting the multipart chunk size significantly higher than the default 5 Mbyte.
   It can be set up to 2 Gbytes but values above 100 Mbyte will probably have only
   little effect on the throughput.
   The following section requires the usage of `[username]` when
   uploading files. The username refers to the value of the `secret_key` in the
   downloaded configuration file. Make sure to get it from the configuration file
   and use it every time the `s3cmd` command is issued.
   {:.info}


3. Upload the files​

   Files can be uploaded with or without folders. Folder creation is automatic
   when adding a directory name to the file path.
   ​
   For example, if `file1.c4gh` should be stored under the `experiment1` folder,
   the command would look like:
   ​
   ```bash
   ./s3cmd-2.2.0/s3cmd -v -c /path/s3-config put [my-path-to-file1.c4gh] "s3://[username]/experiment1/file1.c4gh"
   ```
   ​
   If no folder needs to be created, the command would look like:
   ​
   ```bash
   ./s3cmd-2.2.0/s3cmd -v -c /path/s3-config put [my-path-to-file1.c4gh] "s3://[username]/file1.c4gh"
   ```
   ​
   Once the upload is finished, make sure that the file was uploaded, by
   running the following command:
   ​
   ```bash
   ./s3cmd-2.2.0/s3cmd -v -c [my-path-to-s3-config] ls "s3://[username]/[my-s3-path]/"
   ```
   ​
   You should now be able to see the file and potentially others stored in the
   same location.
