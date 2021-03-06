At some point in time Rails added a nicety to ActionMailer that I've really appreciated.
The nicety I mention is that an html formatted email will be automatically translated into a plaintext email counterpart that is not perfect, but passable when iterating on a blossoming application.

As our applications mature we're upping our efforts on accessibilty.
Within that effort, the automatically generated plaintext emails are being replaced by artisinal plaintext emails.

We're good about writing tests, but our tests broke when we moved from providing the single part to providing multiple parts.

Today I rel-learned how to get to the different parts of the email when they're being provided explicitly.

{% highlight diff %}
-assert_includes email.body.encoded, "some expected text"
+assert_includes email.html_part.body, "some expected text"
+assert_includes email.text_part.body, "some expected text"
{% endhighlight %}

Thanks again [Stackoverflow](https://stackoverflow.com/questions/4868205/rails-mail-getting-the-body-as-plain-text).
