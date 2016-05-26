# Markdown Publishing Guide v1.0.0-prerelease
A guide to publishing Markdown documents on GitHub and ReadTheDocs

## Introduction
This is a guide to writing and publishing Markdown documents on GitHub and ReadTheDocs.
It includes steb-by-step instructions for using GitHub, git, Markdown, and ReadTheDocs in order to
produce a well-formatted set of documents with a detailed table of contents.

This document itself was created using the instructions in this document.

## Status
This documentation is currently being written and should not be considered ready to use.

## Motivation
This document was created to help others write documents in Markdown and have them look good on both GitHub and ReadTheDocs.
By "good" I mean that on ReadTheDocs it has a table of contents page and there is a left navigation pane with topics
that expands hierarchically.

It took a while to figure out how to setup my files on GitHub in a way would produce good results so I 
decided to document the procedures I came up with. I also included a very basic git workflow to support multiple versions.

These instructions are published with Creative Commons Zero license which basically says
you can do what you want with this content and you don't have to add any attributions
or do anything really - just copy it.

## Scope
These instructions are intended for standalone documents, like this one, that do not require
a sophisticated git branching and collaboration workflow.
However, you can also ignore my suggested git workflow and subsitute your own in order to support collaboration.

## Preparing for Development
* Create GitHub Account
* Create ReadTheDocs Account
* Setup Connection to GitHub in ReadTheDocs

## Setting up a New Project

### Creating a GitHub Repo with Initial Content

#### Create a New Repo in the GitHub Web Interface
* Click "New repository" in plus (+) menu in upper right.
* Enter a short description of your project.
* Check "Initialize this repository with a README"
* For license, select "Creative Commons Zero v1.0 Universal"
* Click Create Repository

#### Create docs/user-guide.md with initial content
This document assumes your initial version is v0.0.0 but you can choose a different initial version.
If you pick an initial version other than v0.0.0 then replace v0.0.0 throughout
the rest of this document with your chosen version.

* Go to the repository main page.
* Click on "New file".
* Choose a name for your file, such as "user-guide.md"
* Type "docs/user-guide.md" (replacing with your chosen file name) in the file name text box.
* Click in the file content area.
* Add project description and status.
* If you already have content, add it now
```
# Project Name User Guide v0.0.0

## Introduction
Put an introduction here.

## Main Content
Put more content here.
```
* Change commit message.
    * "Create docs/user-guide.md with initial content"
* Click "Commit new file"


#### Add project info and links to README.md
* Go to the repository main page
* Click on README.md
* Click on pencil icon
* Add project description and status
* Add links to both local doc and read the docs. Change 'project-name' in the text below.
```
## Read the document here:
  * Click [here](http://project-name.readthedocs.io/) for the latest formatted release of the document at readthedocs.io.
  * Click [here](docs/README.md) for the local version of the document in Markdown format.
```
* Edit commit message
    * "Add project information to README.md"
* Click "Commit changes"

#### Create Document list for GitHub in docs/README.md
* Create a docs index in Markdown format for GitHub.
* Go to the repository main page
* Click on "New file".
* Type "docs/README.md" in the file name text box.
* Click in the file content area and add the content below.
* Be sure to change 'project-name' in content below to actual project name.
```
# project-name v0.0.0

Documents
--------
* [User Guide](user-guide.md)
```
* Change commit message.
    * "Create docs/README.md with document list"
* Click "Commit new file"

#### Create a Table of Contents for ReadTheDocs in docs/index.rst
* Create a docs index in Markdown format for GitHub.
* Go to the repository main page
* Click on "New file".
* Type "docs/index.rst" in the file name text box.
* Click in the file content area and add the content below.
* Be sure to change 'project-name' in content below to actual project name.
```
project-name
------------

Documents
=========
.. toctree::
   :maxdepth: 16

   user-guide
```
* Change commit message.
    * "Create docs/index.rst with table of contents"
* Click "Commit new file"


#### Create docs/conf.py
* Go to the repository main page
* Click on "New file".
* Type "docs/conf.py" in the file name text box.
* Click in the file content area and add the content below.
* Be sure to change 'project-name' in content below to actual project name.
```
from recommonmark.parser import CommonMarkParser

source_parsers = {
    '.md': CommonMarkParser,
}

source_suffix = ['.rst', '.md']

master_doc = 'index'
project = u'project-name'
```
* Edit commit message
    * "Add sphinx conf file for ReadTheDocs support"
* Click "Commit new file"

### Setup ReadTheDocs project

#### Import Project
* Go to My Projects by clicking on Account name in upper right
* Click Import a Project
* Click '+' next to project name
* Click Next

## Publish v0.0.0 Project Release

### Add CHANGELOG.md with v0.0.0 description
* Go to the repository main page.
* Click on "New file".
* Type "CHANGELOG.md" in the file name text box.
* Click in the file content area.
* Add content:
```
# v0.0.0
* Project description and status.
* Initial content
* ReadTheDocs support.
```
* Change commit message.
    * "Create CHANGELOG.md for v0.0.0 release"
* Click "Commit new file"

### Create release v0.0.0
* Go to the repository main page.
* Click on "0 releases"
* Click "Create a new release"
* Type "v0.0.0" in the text box
* Enter "v0.0.0 Document Started" in the title box
* Enter the contents of the CHANGELOG.md entry in the description box
* Click "This is a pre-release"
* Click "Publish release"

### Create branch "latest-release"
* Go to the repository main page
* Click on "Branch: master".
* In the text box, type "latest-release".
* Click "Create Branch: latest-release" "from master".

### Activate Version on ReadTheDocs
* Go to ReadTheDocs project
* Click Versions tab
* Click Edit next to v0.0.0
* Click Active
* Click Save

### Setup ReadTheDocs default version
* Go to ReadTheDocs project
* Click Admin tab
* Click Advanced settings
* Change Default version to 'stable'
* Click submit

### Test versions on ReadTheDocs
* Go to ReadTheDocs project
* Click Builds tab
* Wait until builds are finished
* Click Versions tab
* Click on version number to view

### Prepare to develop next version
* Update version at top of docs/index.md to indicate next anticipated version + "-prerelease".
* Update version at top of README.md to indicate next anticipated version + "-prerelease".

## Develop the Next Version

### Improve the content
* Improve the documents in docs/ on the 'master' branch.

## Release the Next Version

### Set the version number
Set version number (vX.Y.Z) decided upon for the new release in file headers.

* Update top of README.md
* Update docs/*.md

### Edit CHANGELOG.md to include vX.Y.Z description
* Go to the repository main page.
* Click on CHANGELOG.md.
* Click on pencil icon
* Click in the file content area.
* Add content:
```
# vX.Y.Z
* First improvement here.
* Next improvement here.
```
* Change commit message.
  * "Add vX.Y.Z release to CHANGELOG.md"
  * Click "Commit changes"

### Create GitHub release
* Go to the repository main page.
* Click on "<N> releases" (where <N> is the current number)
* Click "Create a new release"
* Type "vX.Y.Z" in the text box (replacing X, Y, and Z with the major, minor, and patch number.)
* Enter "vX.Y.Z Put Theme or CodeWord Here" in the title box (replacing with appropriate theme or code word)
* Enter the contents of the CHANGELOG.md entry in the description box
* If major version is zero, click "This is a pre-release"
* Click "Publish release"

### Merge release tag to 'latest-release' branch.
Change user-name, project-name in commands below.
```
$ git clone -b latest-release ssh://github.com/user-name/project-name
$ cd project-name
$ git merge --ff-only <release-tag>
$ git push
```
