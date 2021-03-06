It's important to know how to revert a commit, because sometimes you
accidentally commit strait to master.

If you caught yourself before pushing upstream, you're good. Just

{% highlight bash %}
git checkout -b temporary
git branch -D master
git checkout master
{% endhighlight %}

This assuming it automatically pulls master back down from upstream, which is my
default setup.

If you did push upstream, you'll basically want to create a commit that reverts
the latest commit. Hopefully it's only one commit.

{% highlight bash %}
git format-patch -1 HEAD
git apply [newly_created_patch_name] -R
{% endhighlight %}

