Today I was attempting to validate that three variables all held the same value.
My clever approach was:

{% highlight ruby %}
a = 1
b = 1
c = nil

[a, b, c].uniq.one?
{% endhighlight %}

I expected that to return `false`.
It was returning `true`.

🤔

Showing my reasoning, elementary math style:

{% highlight ruby %}
[a, b, c].uniq.one?

# becomes =>

[1, 1, nil].uniq.one?

# becomes =>

[1, nil].one?
{% endhighlight %}

There are two values, right?
Here's my mistake.
In my quest for object-oriented-message-sending-purity I interpreted `one?` to be about the size of the array.
But reading [the docs][], I'm reminded it's not a message about the size of the array.
It's a message that passes each item in the array to a block, and returns true if exactly one of those return values is truthy.
Without an explicit block, the implicit block is the element itself.
`1` is truty. `nil` is not, so yes, there is one truthy value.

What I really wanted is `[1, nil].count == 1`.
In the end, I reverted to some obvious as day boolean logic of `a == b && b == c`

I'm glad I wrote a test for something so small, because this particular error in this particular place would have led to a substantial security hole.

Lesson learned: just because there's a nicely named message that _sounds_ right doesn't mean it's the message I want to send.
Also, quit trying to be clever.

[the docs]: https://ruby-doc.org/core-2.5.0/Enumerable.html#method-i-one-3F
