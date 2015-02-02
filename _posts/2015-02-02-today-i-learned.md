There is no magic for Rails' `enum` in fixtures. If you want to use the string value (which is the entire point of using the enum), you need to ERB it up. Something like

{% highlight yaml %}
michael:
  name: Michael Bluth
  occupation: <%= Person.occupations[:actor] %> # because 'actor' won't do it
{% endhighlight %}
