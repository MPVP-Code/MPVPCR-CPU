# Central Processing Unit

This repository is the enhanced implementation of the MU0-ARM CPU that is optimised to solve commonly occurring computing problems. It has been built on MU0-ARM architecture from the DECA labs which was improved by adding the serial communication, floating point arithmetic and dual core CPU.

## Requirements

- [ISSIE](https://github.com/tomcl/issie) - an application for digital circuit design and simulation.
- [Node.JS](https://nodejs.org/en/) - a JavaScript runtime built on Chrome's V8 JavaScript engine.
- [Yarn](https://yarnpkg.com/) - package manager for JavaScript libraries.

## Setup

To setup the project just clone in from the GitLab and then run the following command:

```
yarn install
```

This command installs all required dependencies. These dependecies are stored in the `package.json` file. They are used to setup the Git pre-commit hook that formats `.dgm` files before each commit.

## Git pre-commit hook

Git pre-commit hook was setup using the [husky](https://github.com/typicode/husky) library with [lint-staged](https://github.com/okonet/lint-staged) and the [Prettier](https://prettier.io/). The Prettier is configured to format `.dgm` files as pure `JSON` files. Only the files that are in the root directory of the project are formatted. `.dgm` files in the `backup` directory are not formatted.

There is a known issue that prevents from pre-commit hook to run. This issue occurs when some files are staged and then changed on the file system once again without adding them to the stage. This causes the `lint-staged` library to run into problems because it takes files into the stage back on the file system which causes a conflict with edited files. Therefore before committing there is a need to always stage all `.dgm` files.

## Git conventions

### Commit message

Commit messages should follow [Convetional commits](www.conventionalcommits.org) specification:

```
<type>[optional scope]: <description> #<task-id>
```

Example:

```
feat(fpu): implement the add operation #3
```

### Branch naming

Branche names should follow the following namimg convetion:

```
{task-id}-{short-task-description}
```

Example:

```
3-prettier
```

## Authors
- Michal Palič ([michal.palic20@imperial.ac.uk](mailto:michal.palic20@imperial.ac.uk))
- Chenghong Ren ([chenghong.ren20@imperial.ac.uk](mailto:chenghong.ren20@imperial.ac.uk))
- Václav Pavlíček ([vaclav.pavlicek20@imperial.ac.uk](mailto:vaclav.pavlicek20@imperial.ac.uk))