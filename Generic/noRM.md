# No to ORMs

ORMs are a saving grace to Software Engineers. They bridge the gap
between one's proglang of choice and the RDBMS they've implemented (or
had to use). 'No more using SQL directly!' one would think. But Database
Administrators might have other opinions.

ORMs do something necessary for Software Engineers: they abstract away
the details for a specific RDBMS \-- which seem to implement their own
flavor of SQL. However this comes with drawbacks: mainly lack of
optimization.

ORMs abstract away the need for indexed for particular fields. Query
generation for more than simplistic selects tend to be jumbled by less
advanced SQL generation tools.

Overall they are still a great tool, but ORMs can cause major pains when
complex reporting is needed.
