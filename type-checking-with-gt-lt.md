You can use comparison operators like `<`, `>`, `<=`, `>=` when checking types to determine if one class is in the inheritence chain somehwere.

```ruby
# Numeric is greater than Fixnum because it is an ancestor of Fixnum
Numeric > Fixnum # => true
Numeric < Fixnum # => false

# Any comparison with with a constant in another hierarchy will return nil
Numeric <  String # => nil
Numeric >= String # => nil

# works for modules too
class MyClass
  include MyModule
end

MyClass < MyModule # => true
```
