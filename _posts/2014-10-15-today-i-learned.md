You have to mull through a lot of terrible names, and iterate on terrible code
to arrive at a consistent, reasonable API. Today I was building an
`ActiveSupport::Concern` whose purpose will be to cache attributes that are
expensive to compute. The names of the methods changed a handful of times. And
even now they may not be finalized.

I left the code for a few hours, and returned to it with a fresh set of eyes.
The names were terrible. Their implied meaning was confusing. But because of
this gap, I was able to see some of of the consistent shortcomings. I also saw
patterns emerging, that lead to a more consistent API for the final iteration
(of the day).
