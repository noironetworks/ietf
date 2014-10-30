#
# libopflex: a framework for developing opflex-based policy agents
# Copyright (c) 2014 Cisco Systems, Inc. and others.  All rights reserved.
#
# This program and the accompanying materials are made available under the
# terms of the Eclipse Public License v1.0 which accompanies this distribution,
# and is available at http://www.eclipse.org/legal/epl-v10.html
#
###########
#
# Process this file with autoconf to produce a configure script
#
# If you just want to start a build from source control, run
# autogen.sh first.
#

# ---------------------------------------------------------------
# Version information

# Before doing a release, edit:
# 1. the version in AC_INIT
# 2. the libtool version in VERSION_INFO

m4_define([sdk_pversion], 0)
m4_define([sdk_sversion], 1)
m4_define([sdk_iversion], 0)
AC_INIT([libopflex], [sdk_pversion.sdk_sversion.sdk_iversion])
AC_SUBST(SDK_MARKETNAME, ["OpFlex Framework"])
AC_DEFINE(SDK_MARKETNAME, ["OpFlex Framework"], [Marketing name for SDK])

# For more information on libtool versioning, see:
# http://www.gnu.org/software/libtool/manual.html#Versioning
# 
# The version string is [current:revision:age] or [c:r:a].  Here are a
# set of rules to help you update your library version information:
#  1. Start with version information of 0:0:0 for each libtool
#     library.
#  2. Update the version information only immediately before a public
#     release of your software. More frequent updates are unnecessary,
#     and only guarantee that the current interface number gets larger
#     faster.
#  3. If the library source code has changed at all since the last
#     update, then increment revision (c:r:a becomes c:r+1:a).
#  4. If any interfaces have been added, removed, or changed since the
#     last update, increment current, and set revision to 0.
#  5. If any interfaces have been added since the last public release,
#     then increment age.
#  6. If any interfaces have been removed since the last public
#     release, then set age to 0.

AC_SUBST(VERSION_INFO, [0:0:0])

# ---------------------------------------------------------------
# Initialization

# initialize automake and libtool
AM_INIT_AUTOMAKE([subdir-objects silent-rules foreign])
AM_CONFIG_HEADER(config.h)
AC_CONFIG_MACRO_DIR([m4])
LT_INIT()
AC_PROG_LIBTOOL

m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES])

# ---------------------------------------------------------------
# Environment introspection
AC_PROG_INSTALL

# check for ietf tools
AC_PATH_PROG([XML2RFC], [xml2rfc], "no")
AC_PATH_PROG([XSLTPROC], [xsltproc], "no")
AM_CONDITIONAL([BUILD_SPECIFICATIONS],
               [test "x$XML2RFC" != "xno" -a "x$XSLTPROC" != "xno"])

AC_PATH_PROG([XMLLINT], [xmllint], "no")
AM_CONDITIONAL([LINT_SPECIFICATIONS],
               [test "x$XMLLINT" != "xno"])
if test x"$XML2RFC" == x"no" ; then
    AC_MSG_ERROR([Please install xml2rfc before installing.])
fi
if test x"$XSLTPROC" == x"no" ; then
    AC_MSG_ERROR([Please install xsltproc before installing.])
fi
if test x"$XMLLINT" == x"no" ; then
    AC_MSG_ERROR([Please install xmllint before installing.])
fi

# ---------------------------------------------------------------
# Dependency checks

# Checks for header files



# Older versions of autoconf don't define docdir
if test x$docdir = x; then
   AC_SUBST(docdir, ['${prefix}/share/doc/'$PACKAGE])
fi

# ---------------------------------------------------------------
# Build constants

# ---------------------------------------------------------------
# Output

AC_CONFIG_FILES([\
        Makefile \
        rfcs/Makefile \
])
AC_OUTPUT

AC_MSG_NOTICE([
======================================================================
Configuration complete

You may now compile the software by running 'make'
======================================================================])
