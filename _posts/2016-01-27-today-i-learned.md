I'm almost always wanting to add configuration hooks to Rails engines when I build them.
Up to this point I've never taken the time to figure out the most succinct way to provide configuration hooks.
It turns out that it's much simpler than I even imagined.

{% highlight ruby %}
module MyGem
  class Engine < ::Rails::Engine
    isolate_namespace MyGem

    config.my_gem = ActiveSupport::OrderedOptions.new
    config.my_gem.some_setting = true
  end
end
{% endhighlight %}

That's it!
Setting `config` directly in the class definition will expose the configuration in the consuming Rails application.
