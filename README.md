English | [日本語](README.ja.md)

# Global Configurations

This repository is the shared source for development and CI configuration used across projects and the user's development environment. It is designed to be included as a Git submodule so that projects and user-level configuration can refer to one maintained set of files.

## What is included

The repository currently contains configurations for:

- EditorConfig and Git ignore rules
- Markdownlint and textlint, including textlint dictionaries and allowlists
- Commitlint
- GitHub Actions workflow and security checks
- GitHub Actions linting and secret scanning tools

See the repository files for the current set of configurations.

## Use as a submodule

Add this repository to the host repository at a path that fits your setup:

```sh
git submodule add https://github.com/aglabo/global-configs.git path/to/global-configs
git submodule update --init --recursive
```

For a project, the submodule can live under a project configuration directory. For user-level settings, add it to the Git repository that manages your home-directory configuration, at a path such as `.config/global-configs`.

A submodule makes these files available in the host repository; it does not automatically make tools or GitHub Actions discover them. Configure each tool, runner, or workflow to read the relevant file from the submodule path. GitHub Actions workflows that should run in a consuming repository must be wired into that repository's `.github/workflows` directory.

## Updating

To fetch the latest version recorded by the remote repository:

```sh
git submodule update --remote path/to/global-configs
git add path/to/global-configs
git commit -m "chore: update global configs"
```

Review the changes before committing so that the host repository records the intended configuration revision.

## License

This repository is licensed under the MIT License. See [LICENSE](./LICENSE) for details.
