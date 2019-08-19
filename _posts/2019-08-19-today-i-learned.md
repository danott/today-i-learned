[React's Developer Tools][] are accessible from Safari!

For the last three years I've been developing day-to-day in Safari.
Whenver this practice comes up in conversation the first question is "what about React Developer Tools?"
Until now my answer was to drop into Chrome to use the developer toos.

Today I discovered that `react-devtools` can be launched as a standalone application that can be connected to.

I wired this up in my Rails app with some development only logic.

{% highlight erb %}
<% # app/views/application.html.erb %>
<% if Rails.env.development? && ENV["CONNECT_TO_REACT_DEVTOOLS"] == "yep" %>
  <%= javascript_include_tag "http://localhost:8097" %>
<% end %>
{% endhighlight %}

With this in place, starting a Rails server with the appropriate environment flag does the trick. `bin/rails server CONNECT_TO_REACT_DEVTOOLS=yep`

[React's Developer Tools]: https://github.com/facebook/react-devtools/blob/master/packages/react-devtools/README.md#usage-with-react-dom

