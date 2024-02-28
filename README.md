# `mvndelta`

Build only modified Maven modules. Useful on very large projects. Uses the `git` commit
log to determine which Maven modules have changed, and builds only those.

## Prerequisites

Install 

- [Ripgrep](https://github.com/BurntSushi/ripgrep)
- [Fd](https://github.com/sharkdp/fd)
- [Yq](https://github.com/mikefarah/yq)

## Usage
```sh
mvndelta <mvn args>
```

If finding the delta takes longer, then caching mode can be enabled by 

```sh
WITHCACHE=1 mvndelta ...
```

This will cache the current baseline and only do delta checks against that. 

## Limitations
The script writes a cache of all discovered modules in the root of the project, using
the file name `.mvndelta`. This is used to speed up executions, however, it will not
detect when new modules or added. Therefore it is necessary to remove the `.mvndelta`
file whenever you add new modules.
