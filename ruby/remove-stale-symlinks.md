`File.file?` will return false if you give it a symlink that points to a missing file. Therefore, to clear symlinks, the following code works.

```ruby
`ls`.split("\n").each{ |path| File.unlink(path) unless File.file?(path) }
```
This will remove any stale links in the current directory.
