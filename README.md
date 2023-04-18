# Git Clang-Format Pre-commit Framework Hook

This repository contains a pre-commit hook for the [pre-commit](https://pre-commit.com) framework that automatically formats your code using `git-clang-format`. This ensures that only the changes made in the current commit are formatted, maintaining a consistent style throughout the project.

## Table of Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Updating the Hook](#updating-the-hook)
- [Troubleshooting](#troubleshooting)
- [Acknowledgements](#acknowledgements)
- [License](#license)

## Requirements

- Python (>= 3.7)
- Pre-commit framework (>= 2.9.2)

## Installation

1. Install the pre-commit framework:

```bash
pip install pre-commit
```

2. Add the following lines to your project's `.pre-commit-config.yaml` file:

```yaml
- repo: https://github.com/vmudrykPersonal/pre-commit-git-clang-format
  rev: master
  hooks:
  - id: git-clang-format
```

3. Install the pre-commit hook:

```bash
pre-commit install
```

## Usage

Once the pre-commit hook is installed, it will automatically run `git-clang-format` whenever you execute a `git commit` command. If any code changes are detected, they will be formatted according to your project's clang-format configuration.

To manually format your code without committing, run:

```bash
pre-commit run git-clang-format --all-files
```

## Configuration

To customize the behavior of the git-clang-format hook, add the following options to the hook configuration in your .pre-commit-config.yaml file:

```yaml
- repo: https://github.com/username/git-clang-format-precommit-hook
  rev: master
  hooks:
  - id: git-clang-format
    args: [--style=file, --diff]
```

There is the list of supported args by git-clang-format:

```bash
usage: git clang-format [OPTIONS] [<commit>] [<commit>|--staged] [--] [<file>...]

If zero or one commits are given, run clang-format on all lines that differ
between the working directory and <commit>, which defaults to HEAD.  Changes are
only applied to the working directory, or in the stage/index.

Examples:
  To format staged changes, i.e everything that's been `git add`ed:
    git clang-format

  To also format everything touched in the most recent commit:
    git clang-format HEAD~1

  If you're on a branch off main, to format everything touched on your branch:
    git clang-format main

If two commits are given (requires --diff), run clang-format on all lines in the
second <commit> that differ from the first <commit>.

The following git-config settings set the default of the corresponding option:
  clangFormat.binary
  clangFormat.commit
  clangFormat.extensions
  clangFormat.style

positional arguments:
  <commit>              revision from which to compute the diff
  <file>...             if specified, only consider differences in these files

options:
  -h, --help            show this help message and exit
  --binary BINARY       path to clang-format
  --commit COMMIT       default commit to use if none is specified
  --diff                print a diff instead of applying the changes
  --diffstat            print a diffstat instead of applying the changes
  --extensions EXTENSIONS
                        comma-separated list of file extensions to format, excluding the period and case-insensitive
  -f, --force           allow changes to unstaged files
  -p, --patch           select hunks interactively
  -q, --quiet           print less information
  --staged, --cached    format lines in the stage instead of the working dir
  --style STYLE         passed to clang-format
  -v, --verbose         print extra information
```

## Updating the Hook

To update the `git-clang-format` pre-commit hook to the latest version, run:

```bash
pre-commit autoupdate
```

This command will update the `rev` field in your `.pre-commit-config.yaml` file to the latest version of the hook.

## Troubleshooting

If you encounter any issues while using the `git-clang-format` pre-commit hook, please check the following:

- Ensure that you have the required dependencies installed (Python, pre-commit framework).
- Make sure your `.pre-commit-config.yaml` file is correctly configured.
- Check the [pre-commit framework documentation](https://pre-commit.com/#usage) for additional help.

If you still encounter issues, please submit a [new issue](https://github.com/username/git-clang-format-precommit-hook/issues) in the repository, providing a detailed description of the problem, any error messages, and your system configuration.

## Acknowledgements

This project is made possible by the [pre-commit framework](https://pre-commit.com) and the [clang-format](https://clang.llvm.org/docs/ClangFormat.html) tool.

## License

This project is licensed under the [MIT License](LICENSE).

## Additional Resources

* [Official Docs](https://clang.llvm.org/docs/ClangFormatStyleOptions.html)
* [clang-format Guide](https://embeddedartistry.com/blog/2017/10/23/creating-and-enforcing-a-coding-standard-with-clang-format) - a good overview and a great place to get started
* [clang-format Options Explorer](https://zed0.co.uk/clang-format-configurator/) - Website to interactively understand various options
* [Source Code](https://github.com/llvm-mirror/clang/blob/master/tools/clang-format/git-clang-format)