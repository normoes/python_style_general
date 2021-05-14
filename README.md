# python_style_general
Python code style configuration.

Contains configuration files for:
* `black`
* `flake8`
* `pylint`
* `pre-commit`

This is a repository I use to manage tool versions and coding style agreements throughout my projects.

Let's define someterms I will be using in the next couple of sentences:
* **source repository** is this very repository containing the configruation files.
* **project repository** is some project you might want to configure the way defined in the source repository, including updates.

In my projects I use [`copier`](https://github.com/copier-org/copier) to get the latest version of those files.
* By default `copier` considers the latest tag of the source repository.
    - The option ` --vcs-ref=HEAD` makes `copier` consider the most recent commit.
* Answers to questions (from templates) will be stored in `.copier-answers.yml`.
    - These answers will be used as defaults with later updates.

```
# In the python project repository.
# Initial command, sets some values for the project.
copier --vcs-ref=HEAD copy  'git@github.com:normoes/python_style_general.git'  ./

# Update the files
copier --vcs-ref=HEAD update
```

*_Note_*:
* Local changes (in the project repository) need to be committed to make `copier` work.

This way it is possible to (assuming `copier` was already used before):
* First update versions in `.pre-commit-config.yaml` or change something in `tox.ini` for example in the source repository.
* Then commit the changes (optionally create a tag) in the source repository.
* Then use the above `copier` update command to update the files locally in the project repository.

Every project can now be updated to the most recent configuration.
