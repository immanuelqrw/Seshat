Memoized hash vs full comparison

How can you tell when two objects are equal? Simply just compare all
their values.

Wait, turns out this object has another object it owns. You have to
compare all its values.

But wait, turns out... you see where I'm going?

As objects start to have more layers the amount of time taken to compare
equivalence increases immensely. One solution to this is a memoized
hash.

Instead of comparing entire objects, you generate a hash based on any
particular object. And whenever an object has any value changed, the
hash is updated immediately. Java has this implemented through the
hashCode method.

This allows for quick comparisons and removes redundant value checks,
for the small price of a holding a hash value, and whatever it takes to
generate the hash value after each change.

The balance comes from whether your objects are nested enough to
consider trading the algorithm speed cost.
