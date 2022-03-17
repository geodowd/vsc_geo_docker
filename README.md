# Geo Remote Container for VSCode
This repository is designed to be used to create a Remote Container for geospatial python development. Primarily this has been designed to get around issues developing with python on an m1 macbook.

Documentation for using remote containers in vscode can be found at https://code.visualstudio.com/docs/remote/containers.

This creates an environment with a user called 'geo' with password of 'password'! It also creates a python 3.8 conda environment called 'geo' with a lot of useful geospatial packages already installed.

It also loads some vscode extensions and sets some settings to make setup of the environment easier (see the devcontainer.json file)