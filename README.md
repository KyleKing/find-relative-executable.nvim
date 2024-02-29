# Where is my executable?

> WARN
>
> This plugin should be considered pre-alpha (and doesn't actually exist yet! See "Tasks" below)

Efficiently find executables (such as eslint or flake8) in mono-repos for other nvim plugins (like conform and nvim-lint).

Correctly supports `poetry` (`.venv`) and JavaScript/TypeScript/etc. (`node_modules`). Please submnit an issue if you have additional use cases.

## Example

In the below example `eslint (A)` would be found for `file-A.ts` while `eslint (B)` would be found for `file-B.js`. The benefit is that any locally-installed `eslint` plugins and the specific `eslint` version are scoped to the files within that directory. In the same fashion, `flake8` is found for `file.py`; however any files in `Git Root/*.*` would use the system-wide `flake8` or `eslint` binary (if it is installed).

```txt
- Git Root
    - ProjectA
        - node_modules/.bin/eslint (A)
        - src/file-A.ts
    - ProjectB
        - node_modules/.bin/eslint (B)
        - src/file-B.js
    - Project C
        - .venv/bin/flake8
        - src/file.py
```

## Usage

```lua
local where_is_my_executable = require("where_is_my_executable")
where_is_my_executable.find("eslint") -- Uses the currently visible buffer

-- Or probide your own path
where_is_my_executable.find("flake8", vim.fn.getcwd() .. "some/path/file.py")
```

## Tasks

- [ ] Initialize plugin based on template and document local testing with LazyVim
- [ ] Document integration with conform and nvim-lint using LazyVim
- [ ] Implement test framework
- [ ] Generate Vim Documentation
- [ ] Link related plugins
