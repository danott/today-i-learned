Study the docs. As an example, there are so many methods on [Enumerable][] that
you can leverage to eliminate temporary variables. Don't spend all your time
reading the docs, but every once and a while it's good to review what's already
built in the standard library that you don't need to re-invent.

If you're looking up a record by anything other than the `primary_key`, don't
accept arbitrary arguments. Lazily looking up a record is great, but if you're
using something like

{% highlight ruby %}
def destroy_do_dad(expecting_an_id_but_an_object_was_passed_in)
  DoDad.where(foreign_system_id: expecting_an_id_but_an_object_was_passed_in).destroy
end
{% endhighlight %}

you have a huge vulnerability.  `#to_param`, will come into play, and you're now
potentially finding a completely arbitrary record and destroying it.

[Enumerable]: http://ruby-doc.org/core-2.1.5/Enumerable.html
