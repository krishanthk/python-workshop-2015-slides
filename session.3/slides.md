% title: Python Workshop for Grad Students
% subtitle: 3 - Data Analysis & Visualisation
% author: Tim van Boxtel
% thankyou: Thanks everyone for attending!
% contact: <span>github</span> <a href="http://github.com/sunpowered">SunPowered</a>
% favicon: favicon.ico

---
title: Contents
subtitle: The Line Up

- Numpy
- Matplotlib
- Scipy

---
title: Numpy
subtitle: Numerical Python
class: segue dark nobackground

---
title: Numpy
subtitle: Lists Of Data
build_lists: true

- A single Python object is useful
- 1000 similar Python objects in a row is wasteful
- numpy leverages C code to create efficient data structures
- <pre class="prettyprint" data-lang="python">
      import numpy as np
      # An array
      my_arr = np.arange(100)</pre>

---
title: Numpy
subtitle: Enhanced Lists
build_lists: true

A numpy array is multidimensional:

- 50x1 -> 3x5x5x10
- <pre class="prettyprint" data-lang="python">
      >>> my_big_array = np.ones((3, 5, 5, 10))
      >>> my_big_array.shape
      (3, 5, 5, 10)
      >>> my_big_array.size
      750</pre>

---
title: Numpy
subtitle: Find me by my index
build_lists: true

- Arrays are nested, accessed via subsequent indexing
- <pre class="prettyprint" data-lang="python">
      >>> my_big_array[:, 2:4, :, 4].shape
      (3, 2, 5)</pre>

---
title: Numpy
subtitle: Quick Stats
build_lists: true

- Useful builtin statistics for numeric arrays
- <pre class="prettyprint" data-lang="python">
      >>> my_data.sum()
      546.3
      >>> my_data.mean()
      21.1
      >>> my_data.std()
      8.1</pre>

---
title: Numpy
subtitle: Optimized for speed not flexibility
build_lists: true

- Unlike Python lists, they cannot be extended or appended to
- Must be created with a given size first, then populated with data
- <pre class="prettyprint" data-lang="python">
      # From a list
      >>> a_list_arr = np.array([3, 4, 5, ...])
      >>> a_longer_list = np.array([[1, 2, 3],
                                    [4, 5, 6]])
     >>> a_longer_list.shape
     (2, 1)</pre>

---
title: Matplotlib
subtitle: Once blind, can now see
class: segue dark nobackground

---
title: Matplotlib
subtitle: Show Me the Things!
build_lists: true

- Originally intended to be used with ipython as a Matlab replacement
- Many different ways to interact with plots
- Native SVG support

---
title: Matplotlib
subtitle: Show Me the Things
build_lists: true

- Many different builtin plot types
- Works very well with numpy
- Allows for many customization paths

---
title: SciPy
subtitle: Blinded by Science
class: segue dark nobackground

---
title: SciPy
subtitle: Subroutines Galore
class: build_lists: true

- scipy, or Scientific Python fills in much of the blanks
- It has many numerical routines for data processing and analysis
- Many routines are optimized in C or Fortran

---
title: SciPy
subtitle: The Toolset
build_lists: true

Some of the many features of scipy:

- Integration
- Linear Algebra
- FFT
- Interpolation
- Signal Processing

