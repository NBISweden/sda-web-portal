---
layout: article
title: Uploading data from Bianca
key: page-single
sidebar:
  nav: submit
---

This guide describes how you upload data from the [Bianca Cluster](https://www.uppmax.uu.se/resources/systems/the-bianca-cluster/)
at UPPMAX. If your files are not on Bianca, please refer to the 
[general upload instructions](uploading-data) instead.
{:.info}

The guide consists of five major steps:

- [Logging in to UPPMAX](#logging-in-to-uppmax)
- [Installing crypt4gh on Bianca](#installing-crypt4gh-on-bianca)
- [Installing s3cmd on Bianca](#installing-s3cmd-on-bianca)
- [Encrypting files](#encrypting-files)
- [Submitting files](#submitting-files)


## Logging in to UPPMAX

Bianca is part of UPPMAX, so start by logging in to UPPMAX. If you need a
refresher, here are some helpful resources:

- [Getting Started with UPPMAX](https://www.uppmax.uu.se/support/getting-started/)
- [UPPMAX User Guides](https://www.uppmax.uu.se/support/user-guides/)
- [Bianca User Guide](https://www.uppmax.uu.se/support/user-guides/bianca-user-guide/)


## Installing crypt4gh on Bianca

The `crypt4gh` tool is used to encrypt files before they are uploaded to FEGA
Sweden. In order to get `crypt4gh` working on Bianca, you must first download
the tool to a location outside of Bianca and then transfer it to Bianca.

1. Download the relevant `crypt4gh` binary from the
[release page](https://github.com/elixir-oslo/crypt4gh/releases/v1.3.0).

   To download the tool, use the following command:

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

4. Copy `crypt4gh` to the wharf

   Bianca uses a system called the wharf to transfer files without having a
   direct connection to the internet. You can upload files to this system from
   the outside using SFTP, or from UPPMAX by simply mounting the wharf drives.
   You can read more about this in the
   [transit user guide](https://www.uppmax.uu.se/support/user-guides/transit-user-guide/).
 
   From a terminal window, run the following commands to upload your `crypt4gh`
   binary:
 
   Login to transit area by running:
  
   ```bash
   ssh [username]@transit.uppmax.uu.se
   ```
 
   Mount to the Bianca project folder by using the following command:

   ```bash
   mount_wharf [project_name]
   ```

   where `[project_name]` is your bianca project, formatted like 'sens20XXX'.
  
   **Note:** Mounting the wharf follows the same procedure as logging in to
   Bianca, so you will need to provide your password along with your two-factor
   authentication code.
   {:.info}
 
   Copy the `crypt4gh` binary to the project drive in the wharf using the `cp`
   command:
 
   ```bash
   cp crypt4gh ~/<project_name>/
   ```

   Running the `ls` command in this folder, you should be able to see the
  `crypt4gh` file.

5. Copy `crypt4gh` from the wharf to Bianca

   You can now log out from the wharf and log in to Bianca to transfer the files
   out of the wharf and in to your project.
 
   Login to Bianca by running the following command:
 
   ```bash
   ssh -A [username]-[project_name]@bianca.uppmax.uu.se
   ```
   (Remember to use your two-factor authenticator along with your password)
 
   Copy the files from `/proj/[project_name]/nobackup/wharf/[username]/[username]-[project_name]`
   to the folder you want to store the image using the `cp` command:
 
   ```bash
   cp /proj/[project_name]/nobackup/wharf/[username]/[username]-[project_name]/crypt4gh .
   ```
  
   Running the `ls` command in this folder, you should be able to see the
   `crypt4gh` file.


## Installing s3cmd on Bianca

The `s3cmd` tool is used for uploading the files to FEGA Sweden. In order to get
`s3cmd` working on Bianca, you must first download the tool to a location
outside of Bianca and then transfer it to Bianca.

1. Download the correct `s3cmd` binary from the
   [s3cmd GitHub repository](https://github.com/s3tools/s3cmd/releases/tag/v2.2.0).
   This will be the tool that you use to upload your files.

   Use the following command to download the binary:

   ```bash
   wget https://github.com/s3tools/s3cmd/releases/download/v2.2.0/s3cmd-2.2.0.tar.gz
   ```

2. Extract the binary using the tar command

   ```bash
   tar -xvzf s3cmd-2.2.0.tar.gz
   ```

   The executable should be under the `s3cmd-2.2.0` directory.

3. Copy `s3cmd` to the wharf

   The `s3cmd` binary should be transferred to the wharf in the same way as the
   `crypt4gh` binary. You can upload files to this system from the outside using
   SFTP, or from UPPMAX by simply mounting the wharf drives. You can read more
   about this in the [transit user guide](https://www.uppmax.uu.se/support/user-guides/transit-user-guide/).
 
   From a terminal window, run the following commands to upload your `s3cmd`
   binary:
 
   Login to transit area by running:
  
   ```bash
   ssh [username]@transit.uppmax.uu.se
   ```
 
   Mount to the Bianca project folder by using the following command:

   ```bash
   mount_wharf [project_name]
   ```

   where `[project_name]` is your bianca project, formatted like 'sens20XXX'.
  
   **Note:** Mounting the wharf follows the same procedure as logging in to
   Bianca, so you will need to provide your password along with your two-factor
   authentication code.
   {:.info}
 
   Copy the binary and public key files to the project drive in the wharf using
   the `cp` command:
 
   ```bash
   cp s3cmd ~/<project_name>/
   ```

4. Copy `s3cmd` from the wharf to Bianca

   You can now log out from the wharf and log in to Bianca to transfer the files
   out of the wharf and in to your project.
 
    Login to bianca running:
 
    ```bash
    ssh -A [username]-[project_name]@bianca.uppmax.uu.se
    ```
    (Remember to use your two-factor authenticator along with your password)
 
   Copy the files from
   `/proj/[project_name]/nobackup/wharf/[username]/[username]-[project_name]`
   to the folder you want to store the image using the `cp` command:

   ```bash
   cp /proj/[project_name]/nobackup/wharf/[username]/[username]-[project_name]/s3cmd .
   ```
  
  Running the `ls` command in this folder, you should be able to see the
  `s3cmd` file.


## Encrypting files

1. Download the crypt4gh public key

   For FEGA Sweden to be able to read your uploaded files, they need to be
   encrypted with the [correct public key](https://raw.githubusercontent.com/NBISweden/EGA-SE-user-docs/main/crypt4gh_key.pub).
   The file containing the key can be downloaded using the following command:
  
   ```bash
   wget https://raw.githubusercontent.com/NBISweden/EGA-SE-user-docs/main/crypt4gh_key.pub
   ```

2. Copy the encryption key file to the wharf

   Bianca uses a system called the wharf to transfer files without having a
   direct connection to the internet. You can upload files to this system from
   the outside using SFTP, or from UPPMAX by simply mounting the wharf drives.
   You can read more about this in the
   [transit user guide](https://www.uppmax.uu.se/support/user-guides/transit-user-guide/).
 
   From a terminal window, run the following commands to upload your `crypt4gh`
   binary and public key.
 
   Login to transit area by running:
  
   ```bash
   ssh [username]@transit.uppmax.uu.se
   ```
 
   Mount to the Bianca project folder by using the following command:

   ```bash
   mount_wharf [project_name]
   ```

   where `[project_name]` is your bianca project, formatted like 'sens20XXX'.
  
   **Note** mounting the wharf follows the same procedure as logging in to
   Bianca, so you will need to provide your password along with your two-factor
   authentication code.
 
   Copy the binary and public key files to the project drive in the wharf using
   the `cp` command:
 
   ```bash
   cp crypt4gh* ~/<project_name>/
   ```

   3. Copy the key file from the wharf to Bianca
 
   You can now log out from the wharf and log in to Bianca to transfer the files
   out of the wharf and in to your project.
 
   Login to Bianca running:
 
   ```bash
   ssh -A [username]-[project_name]@bianca.uppmax.uu.se
   ```
   
   (Remember to use your two-factor authenticator along with your password)
 
   Copy the files from
   `/proj/[project_name]/nobackup/wharf/[username]/[username]-[project_name]`
   to the folder you want to store the image using the `cp` command:

   ```bash
   cp /proj/[project_name]/nobackup/wharf/[username]/[username]-[project_name]/crypt4gh* .
   ```
 
   Running the `ls` command in this folder, you should be able to see the
   `crypt4gh_key.pub` file.


4. Create a key pair (optional step)

   When encrypting files, the `crypt4gh` will automatically create an encryption
   key. If you prefer to use a specific key, you can provide one using the `-s`
   argument.

   The creation of a key pair is very simple using `crypt4gh`. Run the following
   command, using any name instead of [my-key]:
​
   ```bash
   crypt4gh generate --name=[my-key]
   ```

   To verify that the key pair was created, run the `ls` command and make sure
   the keys you specified exist in the folder.

5. Encrypt the files

   Now that you have the public key and the tools you need, you can encrypt the
   submission files. An encryption key will be created automatically (see
   step 4).

   ```bash
   ./crypt4gh encrypt -p crypt4gh_key.pub -f [my-file]
   ```

   To encrypt the files with a specified secret key:

   ```bash
   ./crypt4gh encrypt -p crypt4gh_key.pub -f [my-file] -s [my-key].sec.pem
   ```

## Submitting files

1. Move encrypted files to the wharf for upload to FEGA Sweden
 
   On Bianca, move the encrypted files to your wharf directory:
   
   ```bash
   mv *.c4gh /proj/[project_name]/nobackup/wharf/[username]/[username]-[project_name]
   ```
 
   Log back in to UPPMAX transit and mount the wharf drive:
   
   ```bash
   ssh [username]@transit.uppmax.uu.se
   mount_wharf [project_name]
   ```
 
   The encrypted files should be secure enough to keep outside of Bianca while
   they are uploaded to the submission system. If you prefer to make the upload
   from a different system than UPPMAX, see the [Bianca user guide](https://www.uppmax.uu.se/support/user-guides/bianca-user-guide/)
   on how to download the encrypted files from the wharf using SFTP.
 
   Once the submission ready files are downloaded, head over to the
   [submitting](/submitter_docs) guide to continue.
 