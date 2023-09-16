<p align="center">
  <a href="https://github.com/johnkraczek/plugin-tools-server">
    <img alt="YDTB" src="https://github.com/johnkraczek/plugin-tools-server/assets/3604887/4c9694e9-de98-45e2-85a2-be246fe5eb1a" height="100"/>
  </a>
</p>
<p align="center">
  <a href="https://github.com/johnkraczek/plugin-tools-server">
    <img alt="YDTB" src="https://github.com/johnkraczek/plugin-tools-server/assets/3604887/2e93491a-5835-423a-b5da-aad1c162256e" height="100"/>
  </a>
</p>

# Welcome to YDTB Plugin Build Action. 

This action allows you to leave out the tedious work of getting all the built files into the tagged versions of the installable plugin. 

## Usage

yourPlugin/.github/workflows/build_and_tag.yml

``` yaml
name: Build and Release

on:
  workflow_dispatch:
    inputs:
      bumpLevel:
        required: true
        default: patch
        description: 'The level of bump to apply to the version number'
        type: choice
        options:
          - major
          - minor
          - patch

permissions:
  contents: write

jobs:
  build:
    uses: johnkraczek/BuildAndTagWordpressPlugin/.github/workflows/build_and_tag.yml@main
    with:
      bumpLevel: ${{ github.event.inputs.bumpLevel }}
      root_php_file: 'plugin-root-file.php'

```