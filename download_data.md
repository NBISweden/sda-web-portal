---
layout: article
title: Download data script
key: page-single
---



Following script is used to download the encrypted data files from the text file. It allows you to maintain the structure of the dataset.

<a href="/download_data.sh" download="download_data.sh"><button class="btn"><i class="fa fa-download"></i> Download</button></a>

```bash
#!/bin/bash

# Parse input argument if exist else use default
input=${1:-urls_list.txt}

# Name of the folder that the url will be cut in
# order to create the directory structure locally
folder="/public/"
folder_length=${#folder}

# Read the url list line by line
while IFS= read -r line; do
  i=0
  url_length=${#line}
  # Local path where the file will be downloaded
  full_path=${line##*$folder}
  # Download files and keep the folders structure
  echo -e "Downloading data from $line \n"
  mkdir -p $(dirname $full_path)
  curl $line --output $full_path
  echo "File saved in $full_path"
  echo -e "- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - \n"
done < "$input"
```

