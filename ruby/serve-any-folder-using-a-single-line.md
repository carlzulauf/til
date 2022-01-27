I found a [list of one-line HTTP servers](https://gist.github.com/willurd/5720255) for several languages. Ruby has a great option available that requires no dependencies and is really short.

    $ ruby -run -ehttpd . -p8000

### Addendum

As of ruby 3, `webrick` is no longer included in the stdlib. So, this does actually have a single dependency: `gem install webrick`.
