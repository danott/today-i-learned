I started making a `before_filter` that would redirect a request from a bot.
After returning to the code, I decided it would be better to `rescue_from
SomeCustomError, with: :what_was_previously_a_before_filter` so that the code
did not have to run on every single request. This probably amounts to minimal
performance gains in terms of actual execution time, but I think it brought
clarity to the code by having the happy path occur first.

Taking the time to organize your folders/files into something predictable needs
to be done quickly when you're working with branches of code. Every divergent
branch means a delay in making it happen.
