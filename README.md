Python Module template
======================

A template for setting up a Python module project with support for unittests, command line argument parsing
and generation of api documentation through sphinx. This template uses
[cookiecutter](https://github.com/audreyr/cookiecutter), a Python templating
tool, to setup a directory structure.

Requirements
------------

Install `cookiecutter` using `pip`:

```
pip install cookiecutter
```

OR

`homebrew`:

```
brew install cookiecutter
```

OR

`conda`:

```
conda install -c conda-forge cookiecutter
```

Usage
-----

You will be asked to provide:
* `module_name` :: this is to become the main folder name to contain the python code
* `base_name` :: this will become the name of the first (base) python file to be added (.py extension will be added)

Generate a new py module project folder using:

```
cookiecutter git@github.com:vliz-be-opsci/cookiecutter-py-module.git
```

**Tip**: prepare your [github](https://github.com/vliz-be-opsci) repository for the new project up front, and have its remote-url at hand when running this:
it will automatically add your project to gitlab and add some basis ci/cd setting


You will then be asked some questions to set up your project. Leaving answers
blank will select the default (shown in [brackets]).

Seasoned users of cookiecutter customize their 'personal defaults' through a local ``~/.cookiecutter.rc``

```yaml
default_context:
    full_name: "Your Name"
    email: "your.name@example.com"
    github_username: "your-name"
    version: "0.0.0"
```

Happy coding!

Structure
----------

The resulting analysis project will have the following structure.

* **tests** - Unit tests
* **data/tests** - Data for testing
* **docs** - sphinx api doc setup
* **{{module_name}}** - where your actual py code goes

After generating your new project you should be able to:

```bash
$ cd your_project_name       # change to the generated folder
# source ./venv/bin/activate # enter the virtual environment
# git status                 # check up on the source management
# make init-dev              # get dependencies
# make test                  # run the tests
# make docu                  # generate the docs
```

Template Developers
-------------------

When extending on this cookiecuuter-template it is best to locally test before you commit any changes.

You can do that by referring to the temnplate-project locally

```bash
$ cd ..
$ cookiecutter ./cookiecutter-py-module
$ cd «project_name»
$ source ./venv/bin/activate                    # slightly different command for windows
$ make init-dev                                 # check install of dependencies
$ make test                                     # check run tests
$ cp dotenv.example .env                        # add local .env from example
$ python tests/test_demo.py                     # check logging statements for specific test
$ make check                                    # check flake8
$ make docs                                     # check generating docs
$ make build                                    # check generating a package
$ make release                                  # check tagging a release -- one can ignore the fail on git push if no git-remote was given
$ git tag                                       # check the release tag
$ python -m «project_name» -l debug-logconf.yml # check the __main__
$ cat «project_name».log                        # it should have produced some log output
$ cd .. && rm -rf «project_name»/               # clean up the test-project
```
