% title: Python Workshop for Grad Students
% subtitle: 2 - Advanced Topics
% author: Tim van Boxtel
% thankyou: Thanks everyone for attending!
% contact: <span>github</span> <a href="http://github.com/sunpowered">SunPowered</a>
% favicon: favicon.ico

---
title: Contents
subtitle: The Lineup

- Classes and Exceptions
- The `os` module
- Times and Dates
- Working with files
- Scripts and Argument Parsing

---
title: Classes
subtitle: The objects have become oriented
class: segue dark nobackground

---
title: Classes
subtitle: So much <i>self</i>
build_lists: true

Remember the class?

- <pre class="prettyprint" data-lang="python">
    class Car(object):
        """ All of the Cars """
        def __init__(self, manufacturer=None, colour=None, 
                     num_doors=None, horsepower=None):
            self.manufacturer = manufacturer or 'unknown manufacturer'
            self.colour = colour or 'unknown colour'
            self.horsepower = horsepower or 'unknown'
            self.num_doors = num_doors or 4
        def is_sedan(self):
            " Is this car a sedan? "
            return self.num_doors == 4
  </pre>

---
title: Classes
subtitle: On your feet!
build_lists: true

Think fast! What object type does the method `is_sedan()` return?

- It's a `bool`  :-)

---
title: Classes
subtitle: Waiting for the inheritance
build_lists: true

- Classes can be *parents* of other classes
- <pre class="prettyprint" data-lang="python">
    class Volkswagon(Car):
    """ The people's car"""
    def __init__(self, **kwargs):
        kwargs['manufacturer'] = 'VW'
        super(Volkswagon, self).__init__(**kwargs)
  </pre>
- <pre class="prettyprint" data-lang="python">
    >>> my_vw = Volkswagon(colour="red", num_doors=2)
    >>> my_vw.is_sedan()
    False
  </pre>

---
title: Classes
subtitle: All the Types
build_lists: true

- It is something helpful to check what type your variables are
- Use `type`
- <pre class="prettyprint" data-lang="python">
    >>> myint = 5
    >>> type(myint)
    <type 'int'>
  </pre>

---
title: Classes
subtitle: Are you instantiated?
build_lists: true

- Instantiated classes are unique versions of that class
- Does it have a serial number?  Instantiate it!
- Check parent/child heierarchy with `isinstance` and `issubclass`
- <pre class="prettyprint" data-lang="python">
    >>> issubclass(Volkswagon, Car)
    True
    >>> isinstance(my_vw, Car):
    True
  </pre>

---
title: Exceptions
subtitle: Shut it all down
build_lists: true

- Occasionally, reality interferes
- Code doesn't always run as you expect, `Exceptions` are thrown
- <pre class="prettyprint" data-lang="python">
    >>> 3[5]
    Traceback (most recent call last):
    File "stdin", line 1, in module
    TypeError: 'int' object has no attribute '\__getitem__'  
  </pre>

---
title: Exceptions
subtitle: Go with the flow
build_lists: true

We can inherit from `Exception` for our own purposes:

- <pre class="prettyprint" data-lang="python">class BaseException(Exception):
    """A project wide Exception class"""
    pass

    class ConnectionError(BaseException):
        """Connections were broken"""
        pass  

    class DatabaseError(BaseException):
        """Database is whack"""
        pass</pre>

---
title: Useful Builtins
subtitle: import os
build_lists: true

- Lots of great platform specific info and functions
- `os.path` - Maybe most useful part?
- Helps write code to be cross platform
- `getcwd()` gets the current working directory
- <pre class="prettyprint" data-lang="python">
    >>> import os
    >>> print os.getcwd()
    '/path/to/where/im/at'</pre>

---
title: Useful Builtins
subtitle: os.path
build_lists: true

- Patches the annoying problem of system paths across all platforms
  + Ahem, <sm>Windows</sm>
  + <pre class="prettyprint" data-lang="python">
      >>> print os.path.join('dir1', 'dir2', 'file.txt')
      'dir/dir2/file.txt'</pre>
- Also has handy functions for splitting and manipulating the path

---
title: Scripts and Arguments
subtitle: Go Python Go
class: segue dark nobackground

---
title: Scripts and Arguments
subtitle: Run It
build_lists: true

- Modules can be imported in other code, or run explicitly from the command line (or IDE)
- <pre class="prettyprint" data-lang="cmd">
    $> python my_script.py
    Doing all your things ... Done.
    $> </pre>
- When invoked like this, we call these *scripts*

---
title: Scripts and Arguments
subtitle: What in the __main__?
build_lists: true

- How do we tell that the file is being run as a script?
- A somewhat ugly yet ubiquitous solution
- <pre class="prettyprint" data-lang="python">
    def analyze_the_data(data):
        ... Analyze all the data ...
    if \_\_name\_\_ == \_\_main\_\_:
        # This condition is met only when the file is being run explicitly
        print "You called?"
        # Do the things
        data = get_the_data()
        analyze_the_data(data)</pre>

---
title: Scripts and Arguments
subtitle: Flexible scripts with arguments
build_list: true

- Often, scripts are written to automate some tedious task, and might be used in any number of ways
- We need a way to handle these variations.  Let's use arguments
- <pre class="prettyprint" data-lang="cmd">
    $> python my_script.py -v --file='/path/to/file'
    I am reading the file '/path/to/file'
    Done!
    $></pre>

---
title: Scripts and Arguments
subtitle: sys.argv
build_lists: true

- The script arguments are available in `sys.argv`, and you can roll your own argument parser if you wish
- <pre class="prettyprint" data-lang="python">
    ...
    if \_\_name\_\_ == \_\_main\_\_:
        import sys
        print sys.argv
        options = parse_the_args(sys.argv)
        do_the_things(options)</pre>

---
title: Scripts and Arguments
subtitle: argparse
build_lists: true

- I prefer to use the one that is given, `argparse.ArgumentParser`
- <pre class="prettyprint" data-lang="python">
    def main(options):
        #  do all the things with the options
        ... 
    if \_\_name\_\_ == \_\_main\_\_:
        import argparse
        parser = argparse.ArgumentParser("my_script_name")
        parser.add_argument('--file', help="Use a file for the things")
        parser.add_argument('-v', action="store_true", 
                            dest='verbose', help='Tell me more things')
        options = parser.parse_args()
        main(options)</pre>

---
title: Working With Files
subtitle: From the I to the O
class: segue dark nobackground

---
title: Working With Files
subtitle: The file object
build_lists: true

- We interact with most filetypes in the same way
- <pre class="prettyprint" data-lang="python">
    with open('/my/data/file.csv', 'r') as f:
        # Do your things with f
        for line in f:
            process_line(line)</pre>

---
title: Working With Files
subtitle: Writing looks similar
build_lists: true

- A file is opened writable with a write flag, `w`
- <pre class="prettyprint" data-lang="python">
    with open('/my/data/analysis.txt', 'w') as f:
        # Write your things to f
        for line in data:
            f.writeline(str(line))</pre>
- e.g. Append a log file, `a`
- <pre class="prettyprint" data-lang="python">
    with open('/my/error/logs.txt', 'a') as f:
        log_the_error()</pre>

