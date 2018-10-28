PZhelp
======

**PZhelp** is what is left from an educational subset of the C
(and later C++) programming language that was intended for teaching
[Introduction to Computer Programming](https://courses.softlab.ntua.gr/progintro/)
to first-year students of the
[School of Electrical and Computer Engineering](https://www.ece.ntua.gr/)
at the
[National Technical University of Athens](https://www.ntua.gr/).
The original subset was called
[Pazcal](https://github.com/softlab-ntua/pazcal)
and came a set of notes, written by
[Stathis Zachos](http://www.corelab.ece.ntua.gr/~zachos/) and
[Nikos Papaspyrou](https://www.softlab.ntua.gr/~nickie/).
The notes (in Greek) now use PZhelp.

PZhelp is actually just a header file defining a set of C macros that
are meant to facilitate first-year students learning C++.
All these macros are written in `UPPERCASE` letters, so they can be
easily distinguished from things existing in regular C.


Usage
-----

```C++
#include "pzhelp"

PROGRAM {
  WRITELN("hello world!");
}
```

You can find the full documentation of the macros defined in PZhelp written in [English](Macros.md) and [Greek](Macros.el.md).


Installation
------------

To install PZhelp to your computer, assuming you are running
Linux or Mac OS, or that you know what to do with your Windows:

0. Make sure you have `g++` or `clang++` installed and working.
   Other C++ compilers may work; however some GNU extensions are required
   --- you have been warned!

1. Copy the file `pzhelp` either to a directory that is in
   your C++ compiler's include path, or to the same directory
   where you have your C++ source files.

This should be enough...


Maintainer
----------

The implementation of PZhelp is maintained by

* [Nikos Papaspyrou](https://www.softlab.ntua.gr/~nickie/)
   \<<nickie@softlab.ntua.gr>\>
