# Contributing to Voice Metadata Standard

# Contributor License Agreement (CLA)
A CLA is a document that specifies how a project is allowed to use your
contribution; they are commonly used in many open source projects.

**_All_ contributions to _all_ projects hosted by [FINOS](https://www.finos.org/)
must be made with a
[Foundation CLA](https://finosfoundation.atlassian.net/wiki/spaces/FINOS/pages/83034172/Contribute)
in place, and there are [additional legal requirements](https://finosfoundation.atlassian.net/wiki/spaces/FINOS/pages/75530375/Legal+Requirements)
that must also be met.**

Commits and pull requests to FINOS repositories will only be accepted from those contributors with an active, executed Individual Contributor License Agreement (ICLA) with FINOS OR who are covered under an existing and active Corporate Contribution License Agreement (CCLA) executed with FINOS. Commits from individuals not covered under an ICLA or CCLA will be flagged and blocked by the FINOS Clabot tool. Please note that some CCLAs require individuals/employees to be explicitly named on the CCLA.

As a result, PRs submitted to the Voice Metadata Standard project cannot be accepted until you have a CLA in place with the Foundation.

Need an ICLA? Unsure if you are covered under an existing CCLA? Email [help@finos.org](mailto:help@finos.org?subject=CLA)

# Before Pull Request

# Contributing Issues

## Prerequisites

* [ ] Have you [searched for duplicates](https://github.com/finos/voice-metadata-standard/issues)?  A simple search for exception error messages or a summary of the unexpected behaviour should suffice.
* [ ] Are you running the latest version?
* [ ] Are you sure this is a bug or missing capability?

## Raising an Issue

* Create your issue [here](https://github.com/finos/voice-metadata-standard/issues/new).
* New issues contain two templates in the description: bug report and enhancement request. Please pick the most appropriate for your issue, **then delete the other**.
  * Please also tag the new issue with either "Bug" or "Enhancement".
* Please use [Markdown formatting](https://help.github.com/categories/writing-on-github/)
liberally to assist in readability.
  * [Code fences](https://help.github.com/articles/creating-and-highlighting-code-blocks/) for exception stack traces and log entries, for example, massively improve readability.

# Contributing Pull Requests (Code & Docs)

To make review of PRs easier, please:

* Validate your contribututions to the standard schema against JSON Schema draft version defined in `$schema` field. See [Tools](#schema-validation) section if you need help to validate your contribution.
* Format the standard schema following guidelines described in [Style guidelines](#style-guidelines). See [Tools](#schema-formatting) section if you need help to format your contribution.
* Please make sure your PRs will merge cleanly - PRs that don't are unlikely to be accepted.
* For documentation contributions, follow the general structure, language, and tone of the [existing docs](https://github.com/finos/voice-metadata-standard/wiki).
* Keep commits small and cohesive - if you have multiple contributions, please submit them as independent commits (and ideally as independent PRs too).
* Reference issue #s if your PR has anything to do with an issue (even if it doesn't address it).
* Minimise non-functional changes (e.g. whitespace).
* If necessary (e.g. due to 3rd party dependency licensing requirements), update the [NOTICE file](https://github.com/finos/voice-metadata-standard/blob/master/NOTICE) with any new attribution or other notices

## Commit and PR Messages

* **Reference issues, wiki pages, and pull requests liberally!**
* Use the present tense ("Add feature" not "Added feature")
* Use the imperative mood ("Move button left..." not "Moves button left...")
* Limit the first line to 72 characters or less when possible

# Style guidelines

## JSON Schema

### Definitions

For the purposes of this style guide, we define the following terms:

* **property** - a name: value pair inside a JSON object.
* **property name** - the name (or key) portion of the property.
* **property value** - the value portion of the property.

```
{
  // The name: value pair together is a "property".
  "propertyName": "propertyValue"
}
```

### General

#### Identation

Use 4 spaces to indent. Never use tabs.

#### Newlines

Use UNIX-style newlines (\n), and a newline character as the last character of a file. Windows-style newlines (\r\n) are forbidden on the repository.

#### No trailing whitespace

Clean up any trailing space in the JSON Schema files before commiting.

#### Comments

JSON Schema does not allow comments, all documentation must be in the `description` property of the object.

### Properties

#### Naming conventions

Use `lowerCamelCase` for property names. They should also be descriptive. Uncommon abbreviations should be avoided.

`array` types should have plural property names. All other property names should be singular.

#### Values

##### Complex types

Opening braces should go on the same line as property name.

Closing braces should be in a separate line with same identation level as the property name.

```
"properties": {
    "propertyName": {
        "type": "string",
        "description": "Some property description",
        "example": "johnsmith"
    },
}
```

##### Simple types

Property value must be placed in the same line as the property name.

```
{
    "property1": "property1 value",
    "property2": "property2 value"
}
```

##### Enums

Opening brackets should go on the same line as property name.

One line per option.

Closing brackets should be in a separate line with same identation level as the property name.

```
"properties": {
    "propertyName": {
        "type": "string",
        "enum": [
            "option1",
            "option2"
        ]
    }
}
```

# Tools

## Schema validation

We use [AJV](https://ajv.js.org) and [ajv-cli](https://github.com/jessedc/ajv-cli) to validate the standard schema in this project.

With ajv-cli installed you can execute the following command to validate your changes:

```
ajv compile -s callmetadata.schema.json
```

As alternative, you can use [JSON Schema Lint](https://jsonschemalint.com/#/version/draft-07/markup/json) online tool or any other tools available in the [JSON Schema Implementations](https://json-schema.org/implementations.html#validators) page.

## Schema formatting

Please configure your editor or run a formatter tool against your modified standard schema before creating your Pull Request.

We use [Prettier](https://prettier.io/) to check if the contributions to the standard schema are following the project guidelines. A Prettier config file(`.prettierrc`) is provided in the repository.
To format using prettier just run:

```
prettier callmetadata.schema.json
```
