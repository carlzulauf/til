I often use `arel_table` in my ActiveRecord models to build up relational algebra and pass the result to something like `where` to execute more complex queries.

```ruby
# I prefer class methods for scopes
def self.old_timers
  where(arel_table[:hire_date].lteq(10.years.ago))
end
```

This is all well and good, but sometimes you want to get back to that low level arel after it's already been passed to `where`. That's where `where_values` (and other related ActiveRecord relation methods) come in.

```ruby
def self.loyalists
  where old_timers.where_values.reduce(:and).or(arel_table[:loyalty_score].gt(1_000))
end
```
