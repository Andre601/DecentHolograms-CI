# DecentHolograms CI

This repository acts as an unofficial CI System, that builds jar files from [DecentHolograms](https://github.com/DecentSoftware-eu/DecentHolograms) whenever there has been a change.

## How to get a Dev build

Each dev build is a new release in this repository. To get the latest dev build, simply check the [releases](https://github.com/Andre601/DecentHolograms-CI/releases) of this repository. The release will have the commits since the last build as a changelog and a jar file will be attached to it under its assets.

## How it works

The CI runs through a [GitHub Actions Workflow](https://github.com/Andre601/DecentHolograms-CI/blob/main/.github/workflows/ci.yml) which activates every 30 minutes.

When running will it check the DecentHolograms Repository for the latest Commit SHA on its main branch. This SHA will then be compared with the one it currently has stored in the `.last_upstream_sha` file.  
Should the SHA's be the same will nothing happen. But if they are different will the Action continue to download the repository, setup Gradle and build a jar file. It will also pull the commits since the last build and convert it into a changelog list before also pulling the previous build number from the `.last_build_number` file, increase it and use it as the new release's tag.  
Finally does it create the release with the changelog, attach the Jar file to it and update the `.last_upstream_sha` and `.last_build_number` files with the new values.

## Why?

This was honestly just a proof of concept, to see how easy or hard it would be to make a CI system using GitHub and GitHub Actions alone.  
It was also honestly made for me to get jar files of dev builds without having to compile it all by myself.
