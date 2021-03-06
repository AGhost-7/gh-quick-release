# `gh-quick-release`
This tool updates your package.json file's version number, merges develop into master and pushes the changes, and creates a new release on Github.

## Installation
```bash
pip install --user gh-quick-release
```

## Installing from source
```bash
git clone https://github.com/AGhost-7/gh-quick-release.git
cd gh-quick-release
python setup.py install --user
```

For development, use the following to install from source:
```
git clone https://github.com/AGhost-7/gh-quick-release.git
cd gh-quick-release
sudo pip install --editable .
```

## Usage
Just run the utility from your project directory. It requires you to have
two environment variables of set; `GH_USER` and `GH_PASSWORD` (used for
authentication with Github).

```
usage: gh-quick-release [-h] [--commit-msg COMMIT] [--version VERSION]
                        [--from-branch FROM_BRANCH]
                        [--into-branch INTO_BRANCH]
                        [--release-title RELEASE_TITLE]
                        [--release-description RELEASE_DESCRIPTION]
                        [--pre-release PRE_RELEASE] [--indent INDENT]
                        [--remote REMOTE] [--verbose VERBOSE]
                        [--cmd-redirect CMD_REDIRECT]

optional arguments:
  -h, --help            show this help message and exit
  --commit-msg COMMIT, -c COMMIT
                        The commit message that will be used when pushing the
                        changes to the package.json
  --version VERSION, -v VERSION
                        The version you want to bump this to (by default it
                        will increment the patch number)
  --from-branch FROM_BRANCH, -f FROM_BRANCH
                        The branch you want to merge from
  --into-branch INTO_BRANCH, -i INTO_BRANCH
                        The branch you will merge into
  --release-title RELEASE_TITLE, -t RELEASE_TITLE
                        The release title! (defaults to "Release version
                        $version")
  --release-description RELEASE_DESCRIPTION, -d RELEASE_DESCRIPTION
                        The release description (defaults to blank)
  --pre-release PRE_RELEASE, -p PRE_RELEASE
                        Should be release be flagged as pre-release on Github?
  --indent INDENT, -n INDENT
                        The indentation style to use when outputing the
                        package.json file
  --remote REMOTE, -r REMOTE
                        The remote to push the changes to (defaults to origin)
  --verbose VERBOSE, -b VERBOSE
                        Spits out information about what is going on (defaults
                        to true)
  --cmd-redirect CMD_REDIRECT, -e CMD_REDIRECT
                        Tells the utility to redirect the git messages to
                        /dev/null
```

## Removing the TLS Certificate Warning
Just certifi, a package which update's the Python certificates automatically.

```
pip install --user certifi
```

## Why is this a Python project?
Well, mainly just for fun. At the same time, I wanted to just write sync code.
The problem is that this would've required some extension modules, which
make it hard to support all nodejs versions. This project is able to support
nodejs 0.6 to 6!
( ͡° ͜ʖ ͡° )


## TODO
- Rollback or resume (to the point where it failed). Tbh this isn't really
important since it does a lot of sanity checks at the begining.
- Add customizable release body:
	- Template for the body.
	- Commit logs are generated and accessible through the template variables.
	- Should be able to modify the commit log output through the `--format='%s'`
	of git.
- Check if branches exist and create if not. Esp the master branch. Devel is
usually there.
- Better error logging...
