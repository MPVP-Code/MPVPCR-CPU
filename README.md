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

## Git workflow

When starting to work on a particular task, move the task in **Board** from the **Open** to **Doing**. Then there is a need to make sure that the local `master` branch is most up to date. To check this make sure that you are using the `master` branch. Before performing any checkout make sure that ISSIE is closed to prevent some conflicts that could be caused by ISSIE's autosaving feature. To checkout, the `master` open Git bash in the project folder and enter `git checkout master`. After checking out `master` download the latest version from the origin using `git pull`. The next step is to create a new branch satisfying the naming convention described in [Branch naming](#branch-naming). Then implement the task as described in the task assignment. When committing new changes make sure that you follow the commit message convention described in [Commit message](#commit-message). After finishing the task, there is a need to push your changes to the origin. This can be done using the command `git push --set-upstream origin [name of the branch]`. The next step is to merge your changes to the `master` on GitLab. To merge the new branch into the `master` create a new merge request in **Merge request** section by clicking on the button **Create merge request** in the notification message with your branch name. Assign the merge request to yourself, remove the **Doing** label from the task, and if there are no conflicts, you will be able to merge your branch into the `master`. Wait until the **Merge** button turns to green and merge your changes to `master`.

### Merge-conflicts

It may happen that someone else has already pushed some changes to `master` after you have created your branch and maybe they changed the same file as you did. This causes a conflict that will prevent you from merging your branch into `master`. To prevent data loss there is a need to accept changes from another person and once again apply your changes because you know what you have changed. You will have to merge `master` from `origin` to your local branch and apply your changes. Before merging make sure that there are no unversioned changes on your current local branch. If there are, remove them or commit them. Then enter the following commands to the Git bash:

- `git checkout master` - checks out the local `master` branch
- `git pull` - pulls the latest version from the origin to master
- `git checkout [your-feature-branch-that-you-want-to-merge]` - checkout your local feature branch
- `git merge --strategy-option theirs master` - merges up to date changes from master. This means that your conflicting changes will be overwritten with changes from `master`. Now you have to implement your changes to the conflicting files once again and make sure that your newly implemented functionality works. Then commit new changes and push them to origin. In case there were no changes in master you should be able to merge your merge request.

## Git pre-commit hook

Git pre-commit hook was setup using the [husky](https://github.com/typicode/husky) library with [lint-staged](https://github.com/okonet/lint-staged) and the [Prettier](https://prettier.io/). The Prettier is configured to format `.dgm` files as pure `JSON` files. Only the files that are in the root directory of the project are formatted. `.dgm` files in the `backup` directory are not formatted.

There is a known issue that prevents from pre-commit hook to run. This issue occurs when some files are staged and then changed on the file system once again without adding them to the stage. This causes the `lint-staged` library to run into problems because it takes files into the stage back on the file system which causes a conflict with edited files. Therefore before committing there is a need to always stage all `.dgm` files.

## Git conventions

### Commit message

Commit messages should follow [Convetional commits](https://www.conventionalcommits.org) specification:

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

## CPU documentation

### Instruction set

| Instruction     | Op code |
| --------------- | ------- |
| Load/Store      | 0000    |
| FPU             | 0001    |
| JLO             | 0010    |
| JLS             | 0011    |
| JMP N           | 0100    |
| JMI N           | 0101    |
| JEQ N           | 0110    |
| STP             | 0111    |
| Data processing | 1000    |
| Data processing | 1001    |
| Data processing | 1010    |
| Data processing | 1011    |
| Data processing | 1100    |
| Data processing | 1101    |
| Data processing | 1110    |
| Data processing | 1111    |

## Authors

- Michal Palič ([michal.palic20@imperial.ac.uk](mailto:michal.palic20@imperial.ac.uk))
- Chenghong Ren ([chenghong.ren20@imperial.ac.uk](mailto:chenghong.ren20@imperial.ac.uk))
- Václav Pavlíček ([vaclav.pavlicek20@imperial.ac.uk](mailto:vaclav.pavlicek20@imperial.ac.uk))
