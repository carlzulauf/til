You can put pretty much anything you want into the class-level enclosure in CoffeeScript.
This should maybe be obvious since its just javascript, but it can be very useful.

Maybe you have `jQuery` in safe mode so you only have access through the `jQuery` object, not `$`.

```coffee
jQuery(".some-selector").hide()
```

In individual classes you could use class scope to give you `$` just within that class:

```coffee
class MyClass
  $ = jQuery
  
  constructor: ->
    @$el = $("div.i-care-about")
  
  # ...
```
