[CORS](http://www.html5rocks.com/en/tutorials/cors/) is real. The part that really tripped me up, is the preflight OPTIONS request.

You can handle this options request in Rails with a nice routing constraint.

```ruby
match '*', to: 'cors#handle', via: %i(options)
```

Then set your `Access-Control-[Whatever]` headers accordingly, and you're in business.
