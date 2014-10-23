Aggressively eliminate state. After working with ReactJS for a bit, I am
starting to see the merits of eliminating state. I'm even beginning to like
methods prefixed with `get` and `set`. Eliminating state means eliminating
side-effects.

Writing adolescent JS code seems to lead to better JS code. What I mean by
adolescent code, is that it refused to take responsibility. It let's somebody
else own the state of the world. All it does is ask for values, and do something
with them.
