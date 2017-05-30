Ruby's `defined?` method is useful, but the syntax is a little surprising at first glance!

{% highlight ruby %}
# These two are similar, but you call them different
defined? @whatever # call with the actual identifier
instance_variable_defined? :@whatever # call with a symbol of the identifier
{% endhighlight %}

`defined?` returns a string of what identifier is. In this case, `nil` or `"instance-variable"`.

`instance_variable_defined?` returns a bool.

When `nil` is an acceptable memoized value, I often reach for a pattern of.

{% highlight ruby %}
def whatever
  return @whatever if instance_variable_defined? :@whatever
  @whatever = some_expensive_computation
end
{% endhighlight %}

For tersness that communicates just as much, this could become

{% highlight ruby %}
def whatever
  return @whatever if defined? @whatever
  @whatever = some_expensive_computation
end
{% endhighlight %}

