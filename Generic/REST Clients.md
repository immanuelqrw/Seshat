You've finally finished your REST API. Looks pretty good. Has all the
correct endpoints. Passed QA with only a few security issues. But. Now
you want to start using it to build applications, and you find yourself
hard coding requests as strings sent to your specified endpoint.
Wait\...did you miss a step?

Here comes API wrappers, an object oriented package to use instead of
dealing with JSON in your new projects. Built in many different ways,
the most common style is creating a class for each endpoint, with
connections to other classes as needed.
