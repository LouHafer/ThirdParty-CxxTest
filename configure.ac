# Copyright (C) 2007-2010 Stefan Vigerske and others.
# All Rights Reserved.
# This file is distributed under the Eclipse Public License.

#############################################################################
#                       Names and other basic things                        #
#############################################################################

AC_INIT([ThirdPartyCxxTest],[4.4],
	[https://github.com/coin-or-tools/ThirdParty-CxxTest/issues/new],
	[thirdpartycxxtest],
	[https://github.com/coin-or-tools/ThirdParty-CxxTest/])

AC_COPYRIGHT([
Copyright 2007-2010 Stefan Vigerske and others.
All Rights Reserved.
This file is part of the open source package Coin which is distributed
under the Eclipse Public License.])

# List one file in the package so that the configure script can test
# whether the package is actually there.
AC_CONFIG_SRCDIR(cxxtest/bin/cxxtestgen)

# Do some project-level initialization work (version numbers, change prefix
# default, ...)

AC_COIN_INITIALIZE

#############################################################################
#                         Standard build tool stuff                         #
#############################################################################

# CxxTest is a bit of an odd duck. It's source code, which might well
# benefit from some configuration, but it's never compiled on its own. All
# of the various bits of source here are used to compose custom test code
# for the unit under test. I'm going to leave these checks in place during
# development. It may be possible to remove some of them at a later date.
# -- lh, 130216 --

# Get the name of the C++ compiler and appropriate compiler options.
AC_COIN_PROG_CXX

###########################################################################
#                            check CxxTest version                        #
###########################################################################

# Get the version. Remember that m4 eats square brackets
AC_MSG_CHECKING([CxxTest version])
CXXTESTVER=`$srcdir/cxxtest/bin/cxxtestgen --version`
CXXTESTVER=`echo $CXXTESTVER | sed -n -e ['s/.*\([0-9]\.[0-9]\)\./\1/p']`
AC_MSG_RESULT([$CXXTESTVER])
AC_SUBST(CXXTESTVER)

# Generate a list of the header and code files that cxxtest uses when it
# generates the driver program for tests.

files=`ls $srcdir/cxxtest/cxxtest`
for file in $files ; do
  CXXTESTHDRS="$CXXTESTHDRS $srcdir/cxxtest/cxxtest/$file"
done
AC_SUBST(CXXTESTHDRS)

AC_CONFIG_FILES([Makefile coincxxtest.pc coincxxtest-uninstalled.pc])

AC_COIN_FINALIZE
