---
title: "Hiding API keys in python using anaconda environment variables"
date: "2019-08-06"
categories: 
  - "security"
---

First you should have anaconda ;)

Then we need to find out where the environment is located

`echo $CONDA_PREFIX`

We'll create create the sub-directories

`cd $CONDA_PREFIX mkdir -p ./etc/conda/activate.d mkdir -p ./etc/conda/deactivate.d touch ./etc/conda/activate.d/env_vars.sh touch ./etc/conda/deactivate.d/env_vars.sh`

We'll have to input the variables in

`./etc/conda/activate.d/env_vars.sh`

For example here we will add a secret key and a path

`#!/bin/sh  export MY_KEY='secret-key-value' export MY_FILE=/path/to/my/file/`

Also important to unset the variables when we deactivate the environment we will need to edit the file

`./etc/conda/deactivate.d/env_vars.sh`

and we will add the following commands

`#!/bin/sh  unset MY_KEY unset MY_FILE`

If we are inside the environment and we run python we can import the key and the path the following way

`import os os.environ.get('MY_KEY')`

and you will get -for this example- as output

`'secret-key-value'`

This is the way to prevent committing to the repo private keys or private information
