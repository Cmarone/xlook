AC_INIT(main.c)

SVN_REVISION=`svnversion -n .`
VERSION="WAC-r$SVN_REVISION"
AM_INIT_AUTOMAKE(xlook,$VERSION)
AM_CONFIG_HEADER(config.h)

# Check for programs.
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_MAKE_SET
AC_CHECK_PROG(DOXYGEN,doxygen,doxygen,[@echo 'You must have doxygen installed to generate the developer documentation.'])

AC_LANG_C

CFLAGS="$CFLAGS -Wall -I/usr/openwin/include -DOWTOOLKIT_WARNING_DISABLED"
CPPFLAGS="$CPPFLAGS -I/usr/openwin/include"
LDFLAGS="$LDFLAGS -L/usr/openwin/lib -L/usr/X11R6/lib"

# Check for libraries.
AC_CHECK_LIB(X11,XDrawLine,,[AC_MSG_ERROR([couldn't find X11 libraries.])])
AC_CHECK_LIB(olgx,olgx_draw_box,,[AC_MSG_ERROR([couldn't find xview libraries. Make sure xview development package is installed from http://physionet.org/physiotools/xview/])],[-lX11])
AC_CHECK_LIB(xview,xv_init,,[AC_MSG_ERROR([couldn't find xview libraries. Make sure xview development package is installed from http://physionet.org/physiotools/xview/])],[-lX11 -lolgx])
AC_CHECK_LIB(m,floor,,[AC_MSG_ERROR([couldn't find m library.])])

# Check for headers.
AC_CHECK_HEADERS(xview/xview.h,,
                [AC_MSG_ERROR([couldn't find xview header files. Make sure xview development package is installed from http://physionet.org/physiotools/xview/])])
AC_CHECK_HEADERS(arpa/inet.h)
AC_CHECK_HEADERS(netinet/in.h)

AC_OUTPUT(Makefile)
