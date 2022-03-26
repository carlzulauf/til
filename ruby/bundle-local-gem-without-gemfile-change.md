Point bundler to a local copy of a gem, temporarily, without changing a project's `Gemfile`. **NOTE:** This only works with `git` sourced gems.

https://bundler.io/v2.3/guides/git.html#local

Point a local gem:

```
$ bundle config set local.opt_struct ~/projects/opt_struct
```

Return to non-local gem usage:

```
$ bundle config --delete local.opt_struct
```
