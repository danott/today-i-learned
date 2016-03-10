Rails will save associations by default.
If you build an in-memory representation of a record that's not intended to be saved with a call to `update` you need to do one of two things.

1. Don't associate the built record with the object you're saving
2. Set autosave to false. Example: `has_one :other_thing autosave: false`.

This manifested itself because I was doing something of the form:

{% highlight ruby %}
class Thing
  has_one :other_thing # 1. Use autosave: false
  def optimistic_version_of_other_thing
    OtherThing.new(thing: self) # 2. don't associate the record with self
  end
end
end
{% endhighlight %}
