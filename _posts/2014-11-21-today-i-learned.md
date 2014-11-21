Let the database do all of the heavy lifting for counting your ActiveRecord
objects.

{% highlight ruby %}
Record.pluck(:owner_id).each_with_object(Hash.new(0)) { |id, counts|
  counts[id] += 1
}
{% endhighlight %}

Sums up the number of records for a `owner` in Ruby. The same can be achieved
via ActiveRecord.

{% highlight ruby %}
Record.group(:owner_id).count
{% endhighlight %}

