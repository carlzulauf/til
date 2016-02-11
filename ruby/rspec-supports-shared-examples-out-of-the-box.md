I found [this](https://github.com/rspec/rspec-core#shared-examples-and-contexts) while reading through some rspec docs. You can create shared examples, then include them into your individual specs, passing different objects.

```ruby
RSpec.shared_examples "collections" do |collection_class|
  it "is empty when first created" do
    expect(collection_class.new).to be_empty
  end
end

RSpec.describe Array do
  include_examples "collections", Array
end

RSpec.describe Hash do
  include_examples "collections", Hash
end
```
