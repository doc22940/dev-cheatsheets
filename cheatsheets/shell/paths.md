# Path cheatsheet

## Current script

Get path to the current script.

### Option A

```sh
SCRIPT_PATH="$(
  cd "$(dirname "$0")" >/dev/null 2>&1
  pwd -P
)"
```

For script `~/foo/bar.sh`, printing that variable:

```
/Users/my-user/foo/bar.sh
```

From top answer on [SO](https://stackoverflow.com/questions/4774054/reliable-way-for-a-bash-script-to-get-the-full-path-to-itself/4774063). See also [page](http://mywiki.wooledge.org/BashFAQ/028).

### Option B

Alternatively, using `realpath`. Works on macOS or Debian - requires coreutils.

```sh
SCRIPT=$(realpath $0)
SCRIPT_PATH=$(dirname $SCRIPT)

# Oneline:
SCRIPT_PATH=$(dirname $(realpath $0))
```


For script `~/foo/bar.sh`, printing those variables:

```
/Users/my-user/foo/bar.sh
/Users/my-user/foo
```


To leave symlinks unresolved: 

```sh
realpath -s $0`
```

## Current directory
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNTE5NjA2NTksLTE2OTQ2NjM3MzVdfQ
==
-->