# Reproducible Zola Example

This is a reproducible zola example failing with the "openssl.so.1.1 error"

## Steps to reproduce

- `git clone` the repo
- `now`
- Now, `now` will ask you some information like scope, project linking, project name and directory of the code. Fill it as requested.
- Then, will assume some information like build command and output directory.
This time, `now` will ask if you want to override the settings it just assumed.
Answer yes, build command and put `zola build` as the new build command.

If followed properly, this steps will lead to a build failed with the next error:

```
zola: error while loading shared libraries: libssl.so.1.1: cannot open shared object file: No such file or directory
```

## My temporary solution

This repo also comes with a temporary solution, as it might lead to a better solution.

- Rename `now.json` to `_now.json`, just to keep it as a backup.
- Rename `now.json.bak` to `now.json` and `build.sh.bak` to `build.sh`.
- Run `now`

This should results in a successful build.

This configuration retrieves, builds and installs OpenSSL 1.1.0 using the release from the OpenSSL's GitHub.

This solution is marked as temporary since it takes ~2 minutes to build (compared to the ~18 seconds it took before the error appeared).

I hope this helps.