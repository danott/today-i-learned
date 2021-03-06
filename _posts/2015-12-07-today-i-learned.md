Multiple calls to `ReactDOM.render` can be a super powerful tool. Given a
state-ful component `Counter`

{% highlight javascript %}
// Initial render into document.body
React.render(<Counter count=0 />, document.body)
// => { state: { count: 0 }, props: { count: 0 } }

// Something internal happens that changes state to 50
// => { state: { count: 50 }, props: { count: 0 } }

// Re-render without unmounting into document.body
React.render(<Counter count=100 />, document.body)
// => { state: { count: 50 }, props: { count: 100 } }
{% endhighlight %}

In many use-cases, `flux` is introduced to distinguish between props and state.
If props are changing on the server, this is a nice light-weight way re-render
everything, while maintaining some client-side state. (Super helpful in rails in
my usage)
