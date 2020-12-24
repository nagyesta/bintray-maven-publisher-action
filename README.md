# Bintray Maven Publisher Action

[![GitHub license](https://img.shields.io/github/license/nagyesta/bintray-maven-publisher-action?color=informational)](https://raw.githubusercontent.com/nagyesta/bintray-maven-publisher-action/main/LICENSE)
[![Version](https://img.shields.io/github/v/tag/nagyesta/bintray-maven-publisher-action?color=blue&label=Latest%20version&logo=docker&logoColor=white&sort=semver)](https://img.shields.io/github/v/tag/nagyesta/bintray-maven-publisher-action?color=blue&label=Latest%20version&logo=docker&logoColor=white&sort=semver)

Bintray Maven Publisher Action aims to upload simple maven artifacts to a Bintray repository.

## Input files

The following input files can be defined:

- POM
- Jar
- Source Jar
- Javadoc Jar

## Goal

Once the artifacts are generated by your build tool (and maybe even published to Github Packages),
this action can quickly and easily upload them to your Bintray repository as well. No need to define
multiple repositories or configure some external tool to sync from Github Packages.

### Features

- Identifies version name from the tag pointing at the current commit (HEAD). Tag format must match Bintray version format.
- Verifies whether the version exists for the package in your Bintray repository
- Creates a new version if needed 
- Uploads the specified artifacts (and leaves them unpublished so that you can verify everything is as expected)

### Configuration

```yml
  - name: Publish to Bintray
    uses: nagyesta/bintray-maven-publisher-action@v1.0.1
    with:
      DEBUG_LOG: "true"
      INFO_LOG: "true"
      WARN_LOG: "true"
      ERROR_LOG: "true"
      DRY_RUN: "true"
      POM_FILE_NAME: "build/publications/mavenJava/pom-default.xml"
      JAR_FILE_NAME: "build/libs/build.jar"
      SOURCE_JAR_FILE_NAME: "build/libs/build-sources.jar"
      JAVADOC_JAR_FILE_NAME: "build/libs/build-javadoc.jar"
      ARTIFACT_GROUP_ID: "com.github.nagyesta.example"
      ARTIFACT_ARTIFACT_ID: "action-artifact"
      ARTIFACT_VERSION: "1.0.0"
      API_USER: "nagyesta"
      API_KEY: "${{ secrets.BINTRAY_TOKEN }}"
      SUBJECT: "nagyesta"
      REPO: "sandbox"
      PACKAGE_NAME: "action-artifact"
      BINTRAY_VERSION_PREFIX: "v"
      BASE_URL: "https://api.bintray.com/"
```
