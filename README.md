```
/*
Copyright (c) by respective owners including Yahoo!, Microsoft, and
individual contributors. All rights reserved.  Released under a BSD (revised)
license as described in the file LICENSE.
 */
```

[![Build Status](https://travis-ci.org/JohnLangford/vowpal_wabbit.png)](https://travis-ci.org/JohnLangford/vowpal_wabbit)

This is the vowpal wabbit fast online learning code.  For Windows, look at README.windows.txt

You can download the latest version from here:
https://github.com/JohnLangford/vowpal_wabbit/wiki/Download

Alternatively, the very latest version is available here:

```
git clone git://github.com/JohnLangford/vowpal_wabbit.git
```
11/11/20 -- update
- Need to make the vw_jni.lib.
- Go to vowpal_wabbit/java/ and run the makefile
- Requires that libboost-program-options.so.1.54.0 be installed:
- To install it: apt-get install libboost1.54-all-dev
- If the dependency is not met, vw_jni will complain

You should be able to build it on most systems with:
make
(make test)

If that fails, try:
```
./autogen.sh
make
(make test)
make install
```

Note that ``./autogen.sh`` requires automake.On OSX, this implies installing
'glibtools'.

For OSX: if make fails with errors then try:
```
brew install libtool
brew install boost --with-python
```
This will install appropriate versions of 'glibtools' and 'boost' on OSX.

Options that were passed to `./configure` in 7.6 and earlier may now be passed
to `./autogen.sh`.

Be sure to read the wiki: https://github.com/JohnLangford/vowpal_wabbit/wiki
for the tutorial, command line options, etc.  

The 'cluster' directory has it's own documentation for cluster
parallel use, and the examples at the end of test/Runtests give some
example flags.
