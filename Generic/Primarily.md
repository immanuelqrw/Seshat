Primary Keys: BIGINT vs UUID

Primary keys come in two flavors: a uniquely incrementing value, or a
randomly generated value that needs to be unique. The benefits are
pretty clear: the former being generated quickly and matched quickly,
the latter making it unclear on the amount of entries that have been
generated at all \-- allowing for us more publicly without compromising
this information if desired.

My preference is BIGINT for RDBMS with a UUID field if desired. Allowing
fast retrieval by integer ID, but also UUID if desired, trading quick
generation and some space.

In most situations either would be suitable for a table so it comes down
to preference.
