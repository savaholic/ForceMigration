# ForceMigration
Salesforce force.com migration tools

## Configs

This build.xml requires two build.properties files.

#### /Program Files/Force Migration/sample/build.properties

This file contains usernames and passwords and must be filled out and placed at /Program Files/Force Migration/sample/build.properties

#### build.properties.local

This file must be in every build folder. It does not need any changes, but can be manipulated to control some functions

**sf.sourceRoot** = This is the root directory for your builds. It is set to the current working directory by default.

**sf.sourceHome** = This is the what the build script calls. (Can probably be collapsed into sourceRoot)

**sf.source.manifest** = This is the location of the package.xml that is used for all retrieval

**sf.checkOnlyBool** = This controls whether pushes are validation only or actual pushes. This is always true for prod.

**sf.runTests** = This controls what level of tests are run. Ensure the level you want is uncommented. Tests are always run in prod.

## Usage

You must create a new folder with a copy of the build.xml, build.properties.local and package.xml for each build that you want to do. The package.xml must contain the items that you want to pull/push in the proper metadata format.

Metadata Reference: https://developer.salesforce.com/docs/atlas.en-us.204.0.api_meta.meta/api_meta/meta_types_list.htm

#### The following build commands can be issued:

**rus** = Retrieve Unpackaged Selector => This will prompt for an env selection (badger,turkey,panther,qa5,qa6,qa7,prod,new). A folder with the name of the selection will be created with the items specified in the package.xml as well as a copy of said package.xml.

**dus** = Deploy Unpackaged Selector => This will prompt for an env selection (badger,turkey,panther,qa5,qa6,qa7,prod,new). A folder with the name of the selection must be present containing a package.xml file listing the contents of the directory.

* You can bypass the selection on either command by passing -Dsf.source.env=${org} where ${org} is the selection.
