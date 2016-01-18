# apex-doc-node
This project is a node.js implementation of the [ApexDoc](https://github.com/SalesforceFoundation/ApexDoc) project. The project aims to provide a documentation frame work for development on the force.com platform.

## Project Status
[![Build Status](https://travis-ci.org/dsharrison/apex-doc-node.svg?branch=master)](https://travis-ci.org/dsharrison/apex-doc-node)

This project is currently in early alpha so bugs may be encountered. A test suite has not yet been implemented and major changes may be made to the project structure prior to the 1.0.0 release. Additionally, this project does not yet have feature parity with the Java ApexDoc and is missing the following notable features:

  - Command-line arguments
  - Including `webservice` scope in `global`
  - Class groups
  - Class group content

## To Do
The next steps for this project will be to support the following:

  - Command-line arguments to override config.json settings
  - A grunt wrapper to allow for inclusion in build tasks
  - Support for template overrides
  - SASS compilation to allow for easier styling

## Usage
### Setup
After cloning or downloading the project, run `npm install` in the project root to install all dependencies.

### Basic Configuration
Edit the `config.json` file to set the following properties:

  - `source`: The location of your class files. This should point to the _"src/classes/"_ directory of a force.com project. **This must end with a forward slash.**
  - `target`: Where your documentation files will be placed. I suggest placing them in a directory like _"docs/"_ of the force.com project. **This must end with a forward slash.**
  - `company`: The name of your company.
  - `email`: Your company's contact email.
  - `scopes`: An array of scopes you would like to generate documentation for.
  - `report`: Whether to run the documentation coverage analysis or not (true/false). 
### Execution
To run the documentation, simply run `node main.js` from the project root.

**IMPORTANT NOTE**

The directory specified in the `target` param is emptied before the new files are generated to account for a difference in scope or deleted classes. **Do not specify a directory containing other files as a target directory!** As a safeguard, the directory will not be emptied if an _index.html_ file is not found, but this is not bulletproof.

### Customization
All HTML is generated by [mustache](https://mustache.github.io/) using the templates contained in the `_templates` directory. These templates can be customized however you want. Default styles are provided by Bootstrap.

## Contribution
Before creating a pull request please update the tests or create new tests in "/\_test/" to cover your changes. New commits and pull requests will be tested by TravisCI but you should run the tests yourself first using `npm test`.