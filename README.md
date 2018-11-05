### Cutest
---
https://github.com/djanowski/cutest

```
cutest test/*.rb
cutest -r ./test/helper.rb ./test/*_test.rb
gem install cutest

```

```ruby
task :test do
  exec "cutest test/*.rb"
end
task :default => :test

setup do
  @foo = true
end
@bar = true
scope do
  test "should not share instance variables" do |foo|
    assert !defined?(@foo)
    assert !defined?(@bar)
    assert foo == true
  end
end

def assert_empty(string)
  assert(string.empty?, "not empty")
end
test "failed custom assertion" do
  assert_empty "foo"
end

setup do
  {:a => 23, :b => 43}
end
test "should receive the result of the setup block as a parameter" do |params|
  assert params == {:a => 23, :b => 43}
end
test "should evaluate the setup block before each test" do |params|
  params[:a] = nil
end
test "should preserve the original values from the setup" do |params|
  assert 23 == params[:a]
end

prepare do
  Ohm.flush
end
setup do
  Ohm.redis.get("foo")
end
test do |foo|
  assert foo.nil?
end


```

```
.PHONY: test
test:
  cutest test/*.rb
  
```
