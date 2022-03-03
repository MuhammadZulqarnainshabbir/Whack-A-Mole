# `sphinx-book-theme`-based Template for Scientific Text

You can write your content in Markdown or reStructuredtext. I recommend Markdown.

# Getting started

## Install `sphinx-book-theme`

Create a Python virtual environment to not influence your standard Python development environment:

```
virtualenv venv
. ./venv/bin/activate
pip install sphinx-book-theme myst-parser
```
Sphinx uses reStructuredtext as default. Using `myst_parser` we can also use Markdown.

## Cloning the template

First fork this project using the fork button on the top right. Then clone your project.

# Creating html

```
cd sphinx-book-template
SPHINXBUILD=~/venv/bin/sphinx-build make html
```

You can view the output using your browser, e.g.:

```
xdg-open _build/html
```

# Deployment on World Wide Web (WWW)

## Manually

You can copy the folder `html` on a web server.

If you are using a server which serves the `$HOME/public_html` to the web, then make sure that the web server has access to this folder. In the following example we are using a server called `joan.th-deg.de`:

```
ssh joan.th-deg.de
mkdir public_html  # This folder will be shared

# Give others the permission to enter your home directory (listing is forbidden, because `r` is missing)
chmod o+x ~

# Now other users could read the files by guessing their filename, so remove the read permission for others
chmod o-r --recursive ~

# ... with exception of public_html
chmod o+rx public_html
```

If you already have other files and folders in public_html
```
# Give others the permission to read all the files
find -type f -exec chmod o+r {} +
# Give others the permission to enter the directories
find -type d -exec chmod o+x {} +
```

## Automatic

This template includes a continuous integration and deployment (CI/CD) configuration (`.gitlab-ci.yml`) for Gitlab which copies the html files to a server whenever you push a new commit. To use it, you need to have an SSH access to a web server.

Three steps:

1. Setting up the values for the variables in `.gitlab-ci.yml`
1. Modifying `.gitlab-ci.yml` according to your username and the deployment folder on the web server
1. Activating a runner in `Settings - CI/CD - Runners`. A shared runner may be available. 

The explanation for the first steps follows:

### Setting up the values for the variables in `.gitlab-ci.yml`

First store your SSH private key (`$SSH_PRIVATE_KEY`) and the SSH public key of the SSH server (`$SSH_KNOWN_HOSTS`) in the CI/CD variables. You find a tutorial here: [Add a CI/CD variable to a project](https://docs.gitlab.com/ee/ci/variables/#add-a-cicd-variable-to-a-project). You do not have to activate `Protected` nor `Masked`.

#### What do I store in `SSH_PRIVATE_KEY`?

You find your private key in `$HOME/.ssh`. You can create new keys using `ssh-keygen`. The public keys have the extension `*.pub`. The extensionless files contain your private keys, e.g., `$HOME/.ssh/id_rsa`:

```
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
NhAAAAAwEAAQAAAYEAlLAHB1jr+muOFMbAtJWcPQJZOJtiAdtSNauyYU9i5/geckOuKHP9
...
K4oavZecZ5XW8AAAASYXJjaEBheWRvcy1yb3MtbWwyAQ==
-----END OPENSSH PRIVATE KEY-----
```

#### What do I store in `SSH_KNOWN_HOSTS`?

This is the key that you accept when you first connect to an SSH server. You can find the public keys of the SSH servers that you have connected to under `$HOME/.ssh/known_hosts`. Alternatively use `ssh-keyscan SERVER_ADDRESS`.

For example a SSH public key of `joan.th-deg.de` is:

```
joan.th-deg.de ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIPYxtnUvjyLdIDkzs4GEzv6KnSN88uPQCC3H/IcuEToe
```

# Further docs

- [Sphinx-book theme – Get Started](https://sphinx-book-theme.readthedocs.io). 

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
