# ABCs are best class

Don't Repeat Yourself. One of the first lessons you learn in CS.

Standard libraries are designed to provide both an implementation that
can be commonly used and a reference for other libraries to design
themselves after. A similar effect occurs in many languages with
abstract classes and interfaces. A template from which to create other objects.

Python, like other languages, has inheritance as a built-in feature to
their classes. However, sometimes you might desire to create a simple
template rather than a creatable class. Python's strength in being
dynamic becomes a major weakness when strictness is desired. However
Python 3 has added a new standard library to alleviate some of the
issues.

---

Abstract Base Classes (ABCs) are Python's solution to their dynamic to strict
problem. They are effectively both abstract classes and interfaces.

Let's first define the difference:

- Interfaces define the structure of an object. An interface is a scaffold, to be filled with implementation that matches defined methods.
- Abstract classes are the next step up: a scaffold, with an option to add implementation.

So how do Python ABCs differ from standard Abstract classes? In a word: dynamic. Python being dynamic means it doesn't check for typing before execution, a fantastic benefit for scripting, a huge detriment when building complex projects which rely on specific implementations. ABCs still manage to allow the rest of the use cases for interfaces.

Consider the following example class inheriting from an ABC:

```python
# run_abc_example.py
from abc import ABC

class ExampleAbstractBaseClass(ABC):

    def run(self):
      raise NotImplementedError("This will throw an exception.")

class ImplementedClass(ExampleAbstractBaseClass):
    pass

if __name__ == "__main__":
    implemented_class = ImplementedClass()
    implemented_class.run()
```

The `run` method is not intended to be implemented, so we raise a `NotImplementedError` when attempting to execute without overriding the method.

```bash
$ python3 run_abc_example.py
Traceback (most recent call last):
  File "run_abc_example.py", line 14, in <module>
    implemented_class.run()
  File "run_abc_example.py", line 7, in run
    raise NotImplementedError("This will throw an exception.")
NotImplementedError: This will throw an exception.
```

As expected, the `NotImplementedError` is raised. However, if we implement the `run` method:

```python
...

class ImplementedClass(ExampleAbstractBaseClass):

    def run(self):
        print("This will work successfully")

...
```

Then we get a valid output:

```bash
$ python3 run_abc_example.py
This will work successfully
```


Similarly, if we only implemented `run` inside the ABC, we would receive the same valid output; just as a regular class inheritance would return.
