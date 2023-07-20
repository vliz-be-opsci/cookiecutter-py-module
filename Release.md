# Git Releases
Documentation regarding publishing/releases methods.

To minimalize errors during the tedious proces of proper releasing and publishing of your python module this project tries to automate as much as possible.

## Initial Setup

Before PyPi publishing will work on a new project several steps need to be taken:
  - An account needs to be created at https://pypi.org/ and/or https://test.pypi.org/
  - An auth token needs to be created for each account
  - This token needs to be stored as a secret on the github project

Complete instructions and more informaction can be found [here](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-python#publishing-to-package-registries).


## Steps towards your next «RELEASE»

These are the basic steps to follow in order to publish a new version of this code onto PyPi:

 - Complete your changes to the code base, make sure `make build` succeeds
 - Update the `__version__.py` with new version number (see section 'what version number to use')
 - Run `make release`. This runs
    - the dependent targets init-dev, check, test, docu, build, thus assuring the release is "sound"
    - reads the python code version from `__version__.py`,
    - creates a git tag based off the python version, thus assuring that release number is available
    - commits, tags, and pushes to the project repo (with rollbacks if fail)
 - Next, go to the "releases" page on github.com (https://github.com/(my_org)/(my_project)/releases) and create new release:
    - Select "Draft New Release"
    - Select tag created in previous step,
    - Leaving the Release Title blank will default to the tag name
    - Fill in release notes
    - and hit "Publish Release"

Publishing the release will cause the action defined in `_/.github/workflows/python-publish.yml` to start. This will (again) run through the make init-dev, check, docu, and build steps (assuring independent environment build success) before publishing the new version to PyPi using the supplied secret.

Documentation should be picked up and published to [readthedocs](http://readthedocs.org/).


## What version number to choose?

A comprehensive description on a sensible versioning structure is described [here](https://semver.org/).


## What other actions are running?

All yaml files stored in the ./.github/workflows/*.yml folder are github actions associated with the project. [Here](https://github.com/sdras/awesome-actions) is a curated list of possible actions that could be run.
