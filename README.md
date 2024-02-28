# `mvndelta`

Build only modified Maven modules. Useful on very large projects. Uses the `git` commit
log to determine which Maven modules have changed, and builds only those.

## Usage
```sh
mvndelta <mvn args>
```

## Limitations
The script writes a cache of all discovered modules in the root of the project, using
the file name `.mvndelta`. This is used to speed up executions, however, it will not
detect when new modules or added. Therefore it is necessary to remove the `.mvndelta`
file whenever you add new modules.
