# Global git-hooks

Integrate secretlint with global git hooks.

Prevent credentials on any Git project by [secretlint](https://github.com/secretlint/secretlint).

## Features

- Global Git Hooks using [`core.hooksPath`](https://git-scm.com/docs/githooks) on Git 2.9+
- If project has setup local git hook, call local hooks too
    - Order: local hooks -> global hooks 
- Define ignoring project paths by `IGNORE_GLOBAL_HOOKS` file

## Hooks

- `pre-commit`
    - [secretlint](https://github.com/secretlint/secretlint) prevent to commit credentials

## Installation

**Requirement:**

- Docker
- Git 2.9+

Check if you already have any global git hooks:

    git config --global core.hooksPath

If output is not empty, run following steps:

```shell script
# clone this repository
git clone https://github.com/secretlint/git-hooks git-hooks
cd git-hooks
# setup git config
git config --global core.hooksPath $(pwd)/hooks
```

## Options

You can create `IGNORE_GLOBAL_HOOKS` file in git-hooks project dir.
It is collection of absolute path to ignore global hooks.

`IGNORE_GLOBAL_HOOKS`:
```
/path/to/my-project-a
/path/to/my-project-b
```

If the project path is included in `IGNORE_GLOBAL_HOOKS`, global git hook does not run. 

## FAQ

### Ignore `pre-commit` hook when commit example

Use [`--no-verify`](https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---no-verify) options.

```
git commit --no-verify
```

## Related

- [azu/git-hooks: @azu's global git hooks](https://github.com/azu/git-hooks)

## Contributing

Pull requests and stars are always welcome.

For bugs and feature requests, [please create an issue](https://github.com/secretlint/git-hooks/issues).

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## Author

- [github/azu](https://github.com/azu)
- [twitter/azu_re](https://twitter.com/azu_re)

## License

MIT © azu