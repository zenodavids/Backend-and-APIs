# Backend Challenges boilerplate - package.json

[![Run on Repl.it](https://repl.it/badge/github/freeCodeCamp/boilerplate-npm)](https://repl.it/github/freeCodeCamp/boilerplate-npm)

<!-- task 1 -->

## Add your name as the author of the project in the package.json file.

```JSON
"author": "Chidozie Zeno Ezeanekwe",
```

<!-- task 2 -->

## Add a Description to Your package.json

```JSON
"description": "A project for learning Backend",
```

<!-- task 3 -->

## Add Keywords to Your package.json

The keywords field is where you can describe your project using related keywords.

```JSON
"keywords": [ "descriptive", "related", "words" ],
```

<!-- task 4 -->

## Add a License to Your package.json

common licenses for open source projects include MIT and BSD.
License information is not required,

```JSON
"license": "MIT",
```

<!-- task 5 -->

## Add a Version to Your package.json

A version is one of the required fields of your package.json file.
This field describes the current version of your project.

```JSON
"version": "1.0.0",
```

<!-- task 6 -->

## Expand Your Project with External Packages from npm

```JSON
"dependencies": {
  "package-name": "version",
  "express": "4.14.0",
  "@freecodecamp/example": "1.1.0"
}
```

<!-- task 7 -->

## Manage npm Dependencies By Understanding Semantic Versioning

Semantic Versioning (SemVer) is an industry standard for software versioning.

```JSON
"dependencies": {
  "package-name": "version",
  "package": "MAJOR.MINOR.PATCH",
  "@freecodecamp/example": "1.2.13"
// where '1' is the major version, '2' is the minor and '13' is the patch.
}
```

- The MAJOR version should _increment_ when you make incompatible API changes.
  - MAJORs add changes that won’t work with earlier versions.
- The MINOR version should _increment_ when you add functionality in a backwards-compatible manner.
  - MINORs add new features.
- The PATCH version should _increment_ when you make backwards-compatible bug fixes.
  - PATCHes are bug fixes.

<!-- task 8 -->

## Use the Tilde-Character to Always Use the Latest Patch Version of a Dependency

allows npm to install the latest PATCH for a dependency(1.2.PATCH version.).
To allow an npm dependency to update to the latest PATCH version, you can prefix the dependency’s version with the tilde (~) since you don’t want to miss bug fixes and (hopefully) don’t break things in doing so

```JSON
"dependencies": {
  "package-name": "version",
  "package": "MAJOR.MINOR.PATCH",
  "express": "4.14.0",
  "@freecodecamp/example": "~1.1.0"
}
```

<!-- task 9 -->

## Use the Caret-Character to Always Use the Latest Patch Version of a Dependency

allows npm to install both the latest MINOR and PATCH for a dependency(1.MINOR version.PATCH version).

```JSON
"dependencies": {
  "package-name": "version",
  "express": "4.14.0",
  "@freecodecamp/example": "^1.1.0"
}
```

<!-- task 10 -->

## Remove a Package from Your Dependencies

remove the corresponding key-value pair for that package from your dependencies.
