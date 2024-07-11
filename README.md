# {{ My new project }}

> A boilerplate template for new repostories in the DexMach organization

This repository serves as a template to setup new repositories within DexMach.

## Installation and usage

More info per topic can be found below. 
Refer to the checklist to make sure you have all items covered.

### Checklist

Go through this checklist after creating your repository. If there is a more efficient way or you hit a blocker, open an issue and let's talk!

#### Readme

- [ ] rename this file to instructions.md
- [ ] rename _readme.md to readme.md
- [ ] remove the installation and usage instructions
- [ ] rename all {{ placeholder }} elements
- [ ] complete all empty headings (example; description, ...)

#### Chancelog

- [ ] install nodejs and npm if not already done
- [ ] restore the npm packages (standard-version)
- [ ] initiate an first release (npm run release -- --first-release)

#### dotfiles

- [ ] update the .gitignore file (refer to the [gitignore](#gitignire) section for more info)
- [ ] do you need additional ignore files (docker, terraform, ..)

#### Metadata

- [ ] have you added a short description to the repo in Github or Azure Devops?

### Instructions

Within the following sections you can find detailed instructions per topic

#### Repo cloning

Using this repo as a template is quite straightforward, but the instructions depend on the VCS. At DexMach we currently use Github or Azure Devops.

##### Github

When creating a repository from the GH CLI, append the --template parameter to create a new repository.

``` bash

 gh repo create <REPO-NAME> --template <USER|ORG/repo-template>

```

##### Azure Devops

The Azure Devops CLI does not support creating new repositories based on a 'template repo'. A few additional steps are needed to mimick the same behaviour.

``` bash

# create the repo in Azure Devops
az devops repo create --name '<REPO-NAME>' --project '<PROJECT-NAME>' --org 'DexMach'

# create an empty folder
mkdir new-project/
cd new-project/
git archive --remote="<REPO-TEMPLATE-URL>" HEAD | tar -x
git init
git add -A
git commit -m "Staring off with revision ${rev} of repository ${repo}."

## add the remote

git remote add origin 'https://dev.azure.com/DexMach/<PROJECT-NAME>/_git/<REPO-NAME>'
git push -u origin --all

```

#### Changelog

The changelog is autogenerated using [standard-version](https://github.com/conventional-changelog/standard-version).
Please adhare to the  [conventional commit naming standard](https://www.conventionalcommits.org/en/v1.0.0/) to help generate the changelog whenever a new version is released.

Refer to the [versionrc](./.versionrc) file to validate what gets tracked.

To generate a new changelog just run the following snippet after got commit:

``` nodejs

    nmp run release

```
#### gitignore

The .gitignore is created using the excellent [gitignore.io](https://gitignore.io) website.
Currently we take the following items into consideration:

- windows,
- macos,
- linux,
- powershell,
- python,
- dotnetcore,
- aspnetcore,
- terraform,
- ssh,
- dotenv,
- helm,
- node

Whenever a new technology needs to be included, please inform the [Innovation Cirle](https://app.glassfrog.com/organizations/24145/orgnav/roles/13209873/overview) to raise a ['technology basket']() tension.