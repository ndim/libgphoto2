dnl Process this file with autoreconf to produce a configure script.
AC_PREREQ([2.69])

dnl NOTE: Be version style _higher_ than the last release.
dnl       So lastversion.X.trunk for instance. Bump X if necessary.

dnl ******* THE NEXT RELEASE VERSION MUST BE 2.5.31 at least or higher!
AC_INIT([libgphoto2 photo camera library],
        [2.5.31.1],
        [gphoto-devel@lists.sourceforge.net],
        [libgphoto2])

AC_CONFIG_SRCDIR([libgphoto2/gphoto2-version.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([auto-m4])
AC_CONFIG_AUX_DIR([auto-aux])
AM_INIT_AUTOMAKE([
  -Wall
  foreign
  1.14
  dist-bzip2
  dist-xz
  check-news
  subdir-objects
])


dnl Notable tool releases and why they are important for us:
dnl
dnl   autoconf 2012-04-25 2.69    (what libexif requires)
dnl   autoconf 2006-04-12 2.59c   (introduces localedir, docdir, htmldir)
dnl
dnl   automake 2013-12-24 1.14.1  (what libexif requires)
dnl   automake 2013-06-20 1.14    (introduces %reldir%, implies AM_PROG_CC_C_O)
dnl   automake 2013-05-15 1.13.2  (bugfix for handling multiple m4 macro dirs)
dnl   automake 2012-04-25 1.12    (introduces AM_PROG_AR)
dnl   automake 2009-05-17 1.11    (introduces AM_SILENT_RULES, pkglibexecdir)
dnl   automake 2005-07-10 1.9.6   (fixes filename-length-max=99)
dnl   automake 2004-07-28 1.9     (libgphoto2 requirement since 2.2.1.3 2006-09-28)
dnl
dnl   gettext  2014-06-10 0.19.1  (allows building without updating *.po)
dnl   gettext  2013-07-07 0.18.3  (what libexif requires)
dnl   gettext  2012-12-08 0.18.2
dnl   gettext  2004-01-30 0.14.1
dnl
dnl   libtool  2014-10-27 2.4.3
dnl   libtool  2011-10-18 2.4.2


AM_SILENT_RULES([no])


dnl Flag all GP_ strings in result as error unless specifically allowed.
m4_pattern_forbid([^_?GP_])dnl


GP_CHECK_SHELL_ENVIRONMENT
GP_CONFIG_MSG([Build])
GP_CONFIG_MSG([Source code location],[${srcdir}])

dnl ---------------------------------------------------------------------------
dnl Advanced information about versioning:
dnl   * "Writing shared libraries" by Mike Hearn
dnl         http://plan99.net/~mike/writing-shared-libraries.html
dnl         originally http://navi.cx/~mike/writing-shared-libraries.html
dnl   * libtool.info chapter "Versioning"
dnl   * libtool.info chapter "Updating library version information"
dnl ---------------------------------------------------------------------------
dnl Versioning:
dnl  - AGE (Micro):      Increment if any interfaces have been added; set to 0
dnl		         if any interfaces have been removed. Removal has
dnl                      precedence over adding, so set to 0 if both happened.
dnl                      It denotes upward compatibility.
dnl  - REVISION (Minor): Increment any time the source changes; set to
dnl			 0 if you incremented CURRENT.
dnl  - CURRENT (Major):  Increment if the interface has changes. AGE is always
dnl                      *changed* at the same time.
dnl
dnl  To summarize. Any interface *change* increment CURRENT. If that interface
dnl  change does not break upward compatibility (ie it is an addition),
dnl  increment AGE, Otherwise AGE is reset to 0. If CURRENT has changed,
dnl  REVISION is set to 0, otherwise REVISION is incremented.
dnl ---------------------------------------------------------------------------
dnl A:R:C=1:1:3  libgphoto2-2.2
dnl A:R:C=2:0:4  libgphoto2-2.3 (since libgphoto2-2.2.1.5.trunk)
dnl A:R:C=2:1:4  libgphoto2-2.3.1 (since libgphoto2-2.3.0.1.trunk)
dnl A:R:C=3:0:5  libgphoto2-2.3.0.3.trunk (new gp_file_new_from_fd() function)
dnl              libgphoto2-2.3.1.1.trunk (new gp_file_slurp() function)
dnl              libgphoto2-2.3.1.2.trunk (new gp_camera_get_storageinfo() function + enums + struct)
dnl A:R:C=0:0:6  libgphoto2-2.5.0	(fixed CameraList API, ... )
dnl A:R:C=1:0:7  libgphoto2-2.5.24	(added GP_EVENT_FILE_CHANGED ... )
dnl A:R:C=2:0:8  libgphoto2-2.5.28	(added gp_filesystem_set_info_dirty ... )
dnl A:R:C=3:0:9  libgphoto2-2.5.XXX	(added gp_init_localedir ... )
AC_SUBST([LIBGPHOTO2_AGE],      [3])
AC_SUBST([LIBGPHOTO2_REVISION], [0])
AC_SUBST([LIBGPHOTO2_CURRENT],  [9])
AC_SUBST([LIBGPHOTO2_CURRENT_MIN],
         [`expr $LIBGPHOTO2_CURRENT - $LIBGPHOTO2_AGE`])
AC_SUBST([LIBGPHOTO2_VERSION_INFO],
         [$LIBGPHOTO2_CURRENT:$LIBGPHOTO2_REVISION:$LIBGPHOTO2_AGE])

dnl ---------------------------------------------------------------------------
dnl A:R:C=6:1:6 libgphoto2_port-0.6.1 libgphoto2-2.2.1
dnl A:R:C=7:0:7 libgphoto2_port-0.7.0 libgphoto2-2.3
dnl A:R:C=7:1:7 libgphoto2_port-0.7.1 libgphoto2-2.3.x
dnl A:R:C=8:0:8 libgphoto2_port-0.8.0 libgphoto2-2.4.x
dnl A:R:C=9:1:9 libgphoto2_port-0.10.0 libgphoto2-2.5.x
dnl A:R:C=1:0:13  libgphoto2-2.5.30	(added gp_port_init_localedir ... )
dnl A:R:C=2:0:14  libgphoto2-2.5.31	(added gpi_libltdl_mutex ... )
AC_SUBST([LIBGPHOTO2_PORT_AGE],      [2])
AC_SUBST([LIBGPHOTO2_PORT_REVISION], [0])
AC_SUBST([LIBGPHOTO2_PORT_CURRENT],  [14])
AC_SUBST([LIBGPHOTO2_PORT_CURRENT_MIN],
         [`expr $LIBGPHOTO2_PORT_CURRENT - $LIBGPHOTO2_PORT_AGE`])
AC_SUBST([LIBGPHOTO2_PORT_VERSION_INFO],
         [$LIBGPHOTO2_PORT_CURRENT:$LIBGPHOTO2_PORT_REVISION:$LIBGPHOTO2_PORT_AGE])


dnl ---------------------------------------------------------------------------
dnl Checks for programs.
dnl ---------------------------------------------------------------------------

AC_MSG_CHECKING([original CC value])
AC_MSG_RESULT(["$CC"])
AC_MSG_CHECKING([original CXX value])
AC_MSG_RESULT(["$CXX"])

AC_PROG_CC
AC_PROG_CPP
AC_PROG_CXX
AC_PROG_INSTALL
AC_PROG_SED
AM_PROG_AR


dnl If CXX is neither unset nor empty nor "no", presume we can compile
dnl C++ sources. A C++ compiler is not required for libgphoto2 itself,
dnl but is useful to make sure that the libgphoto2 header files
dnl compile when included into C++ source files.
AM_CONDITIONAL([HAVE_CXX], [test "x$CXX" != "x" && test "x$CXX" != "xno"])


dnl Not strictly necessary, but helps pulling translations.
GP_CHECK_PROG([RSYNC], [rsync], [file copying command])
AM_CONDITIONAL([HAVE_RSYNC], [test "x$RSYNC" != xno])


dnl --------------------------------------------------------------------
dnl Determine the most pedantic compiler flags we can find for both
dnl C and C++, so that we can test that the libgphoto2 headers compile
dnl with those flags.
dnl --------------------------------------------------------------------
dnl
dnl
GP_WITH_EMPTY_CONFDEFS_H([dnl
dnl
GP_PEDANTIC_COMPILER_FLAGS([C90],   [C],   [-std=c90])
GP_PEDANTIC_COMPILER_FLAGS([C99],   [C],   [-std=c99])
GP_PEDANTIC_COMPILER_FLAGS([C11],   [C],   [-std=c11])
GP_PEDANTIC_COMPILER_FLAGS([C2X],   [C],   [-std=c2x])
dnl
GP_PEDANTIC_COMPILER_FLAGS([CXX98], [C++], [-std=c++98])
GP_PEDANTIC_COMPILER_FLAGS([CXX11], [C++], [-std=c++11])
GP_PEDANTIC_COMPILER_FLAGS([CXX14], [C++], [-std=c++14])
GP_PEDANTIC_COMPILER_FLAGS([CXX17], [C++], [-std=c++17])
GP_PEDANTIC_COMPILER_FLAGS([CXX20], [C++], [-std=c++20])
dnl

dnl --------------------------------------------------------------------
dnl The goals here are twofold:
dnl
dnl   * Produce as many compiler warnings as possible to find
dnl     potential problems in our own code.
dnl
dnl   * Make sure our API header files are as broadly compatible as
dnl     possible.
dnl
dnl We want our library and driver code to compile with the lowest
dnl possible number of warnings, and the pedantic compilation tests to
dnl compile with zero warnings (-Werror) so we do not limit the users
dnl of our API in their use of compiler warnings.
dnl
dnl If, for some reason, you need to build without all these compiler
dnl warnings, run the build while setting CFLAGS to an empty string:
dnl
dnl     $ make all check CFLAGS=
dnl --------------------------------------------------------------------

dnl * gcc exits non-zero when it encounters an unknown warning option
dnl * clang by default ignores unknown warning option
dnl * clang with -Werror=unknown-warning-option will exit non-zero
dnl   when it encounters an unknown warning option
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Werror=unknown-warning-option])

GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wall])
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wextra])
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wmost])
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Werror=incompatible-pointer-types])
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Werror=implicit])
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Werror=int-conversion])

dnl We used to have these two defined for GCC instead of the whole -Wextra
dnl GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wmissing-declarations])
dnl GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wmissing-prototypes])

dnl clang finds the underscores in all the "struct _Foo" definitions
dnl which means they fall into the reserved category. Before we can
dnl think about renaming those idenifiers, we need to verify they are
dnl not part of our public API.
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wno-error=reserved-identifier])

dnl clang finds "/** comments using \deprecated */" without a
dnl corresponding __attribute__(( deprecated )). We need a good header
dnl file defining such compiler and standard library specific
dnl attributes purely as C preprocessor macros without configure
dnl involvement before we can change anything about this in the public
dnl API's include files.
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wno-error=documentation-deprecated-sync])

dnl We used to have these four... no idea why, though. Stop reporting
dnl unused parameters for now, as those are VERY numerous and not much
dnl of a security risk, unlike the format and string warnings.
GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wno-unused-parameter])
dnl GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wno-format-overflow])
dnl GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wno-format-truncation])
dnl GP_CONDITIONAL_COMPILE_FLAGS([CFLAGS], [-Wno-stringop-truncation])

])dnl GP_WITH_EMPTY_CONFDEFS_H

dnl Every compile example after here will be using the C language
AC_LANG([C])


dnl ---------------------------------------------------------------------------
dnl Turn on (almost) all warnings when using gcc
dnl ---------------------------------------------------------------------------
if test "x$GCC" = "xyes"; then
	AC_SUBST([NO_UNUSED_CFLAGS], [-Wno-unused])
fi
AM_CONDITIONAL([HAVE_GCC], [test "x$GCC" = "xyes"])

# Activate internal code
AM_CPPFLAGS="$AM_CPPFLAGS -D_GPHOTO2_INTERNAL_CODE"

# CPPFLAGS: C PreProcessor flags
AC_SUBST([AM_CPPFLAGS])
# CFLAGS: C compiler flags
AC_SUBST([AM_CFLAGS])
# CXXFLAGS: C++ compiler flags
AC_SUBST([AM_CXXFLAGS])
# LDFLAGS: Linker flags
AC_SUBST([AM_LDFLAGS])

# Check for va_copy()
GP_VA_COPY

# Note: Do NOT add specific libraries and stuff to the generic _FLAGS.
#       Put these into LIBFOO_CFLAGS and LIBFOO_LIBS instead.


dnl check for/set up libtool and libltdl
m4_pattern_forbid([^LT_PREREQ])dnl
LT_PREREQ([2.4.2])
dnl Disable building static library, as no one uses it anyway.
m4_pattern_forbid([^LT_INIT])dnl
LT_INIT([
  disable-static
  dlopen
  win32-dll
])
dnl
dnl LTDL_INIT([external])
dnl
dnl We are using our own libltdl checks instead of LTDL_INIT because
dnl we do not want to ship our own two copies of libltdl (one for
dnl libgphoto2 and one for libgphoto2_port), and LTDL_INIT insists on
dnl that.
GP_LIBLTDL


# report on compiler/libtool setup
GP_CONFIG_MSG([Compiler],[${CC}])
GP_CONFIG_MSG([libltdl includes],[$LTDLINCL])
GP_CONFIG_MSG([libltdl library],[$LIBLTDL])

AC_DEFINE_UNQUOTED([HAVE_CC], ["$CC"],
                   [The C compiler we are using])


dnl ---------------------------------------------------------------------------
dnl Reference definitions
dnl    required before we do the Makevars hack!
dnl ---------------------------------------------------------------------------

GP_REFERENCES()dnl


GP_CONFIG_MSG([Features])

dnl ---------------------------------------------------------------------------
dnl i18n support (including some hacks)
dnl ---------------------------------------------------------------------------

GP_GETTEXT_SETUP([GETTEXT_PACKAGE_LIBGPHOTO2],
                 [${PACKAGE}-${LIBGPHOTO2_CURRENT_MIN}],
                 [po])
GP_GETTEXT_SETUP([GETTEXT_PACKAGE_LIBGPHOTO2_PORT],
                 [libgphoto2_port-${LIBGPHOTO2_PORT_CURRENT_MIN}],
                 [libgphoto2_port/po])
AM_PO_SUBDIRS()
AM_GNU_GETTEXT_VERSION([0.19.1])
AM_GNU_GETTEXT([external])
AM_ICONV()

GP_CONFIG_MSG([Use translations],
              [${USE_NLS}])

dnl XXX FIXME: BEGIN from libgphoto2
dnl FIXME: We have to make sure this works first
dnl AC_CHECK_FUNC(gettext, gettext_without_libintl=true)
# same trick as with libdl:
# if gettext() doesn't require linking against libintl,
# we don't have to check for gettext in libintl. Otherwise
# we may even require libintl.
dnl if test "x$gettext_without_libintl" != xtrue && test "x$USE_NLS" = xyes; then
dnl        AC_CHECK_LIB([intl], [gettext], [INTLLIBS="$INTLLIBS -lintl"])
dnl fi
dnl XXX FIXME: END from libgphoto2

dnl XXX FIXME: BEGIN from libgphoto2_port
AC_CHECK_FUNC([gettext], [gettext_without_libintl=true])
# same trick as with libdl in libgphoto2:
# if gettext() doesn't require linking against libintl,
# we don't have to check for gettext in libintl. Otherwise
# we may even require libintl.
dnl AC_CHECK_LIB(intl, gettext, [LIBS="$LIBS -lintl"])
if test "x$gettext_without_libintl" != xtrue && test "x$USE_NLS" = xyes; then
  AC_CHECK_LIB([intl], [gettext], [INTLLIBS="$INTLLIBS -lintl"])
fi
dnl XXX FIXME: END from libgphoto2_port


AC_SYS_LARGEFILE

GP_ASM_SYMVER_SUPPORT

dnl ---------------------------------------------------------------------------
dnl FIXME: What is this good for?
dnl Replace `main' with a function in -libs:
dnl ---------------------------------------------------------------------------
AC_CHECK_LIB([ibs], [main])

dnl we use some libm functions in some drivers, so just add -lm
AC_CHECK_LIB([m], [sqrt])


dnl ---------------------------------------------------------------------------
dnl test GP_SET_ macros from gp-set.m4
dnl ---------------------------------------------------------------------------
dnl GP_SET_TESTSUITE
dnl AC_MSG_ERROR([gp-set.m4 testsuite done.])


dnl ---------------------------------------------------------------------------
dnl libjpeg (from libjpeg-turbo or a number of other implementations)
dnl ---------------------------------------------------------------------------
GP_LIBJPEG


dnl ---------------------------------------------------------------------------
dnl check for ws2_32
dnl ---------------------------------------------------------------------------
LIBWS232_CFLAGS=""
LIBWS232_LIBS=""
libws232_msg="no"
AC_SUBST([LIBWS232_CFLAGS])
AC_SUBST([LIBWS232_LIBS])
AC_ARG_WITH([ws232],
            [AS_HELP_STRING([--without-ws232],
	                    [Build without ws2_32 library (default: no)])])
AS_IF([test "x$with_ws232" != "xno"], [dnl
	AC_CHECK_LIB([ws2_32], [WSAStartup], [dnl
		AC_CHECK_HEADER([winsock.h], [dnl
			AC_DEFINE([HAVE_LIBWS232], [1],
			          [define if we found LIBWS232 and its headers])
			LIBWS232_LIBS="-lws2_32"
			libws232_msg="yes"
		])
	])
])
GP_CONFIG_MSG([Winsocket support (for PTP/IP)],[${libws232_msg}])

dnl ---------------------------------------------------------------------------
dnl check for libxml2
dnl ---------------------------------------------------------------------------
GP_CHECK_LIBRARY([LIBXML2],[libxml-2.0],[>= 2.0],
                [libxml/parser.h],[xmlFirstElementChild],[],[],
                [default-on],
                [http://xmlsoft.org]
)
GP_CONFIG_MSG([XML support for Olympus E series],[${have_LIBXML2}])

GP_CHECK_LIBRARY([LIBCURL],[libcurl],[>= 7.1],
		[curl/curl.h],[curl_easy_init],[],[],
                [default-on],
		[https://www.curl.org]
)
GP_CONFIG_MSG([CURL support for Lumix Wifi],[${have_LIBCURL}])

dnl ---------------------------------------------------------------------------
dnl check for libgd
dnl they call it "gdlib" ... confusing.
dnl ---------------------------------------------------------------------------
GP_CHECK_LIBRARY([LIBGD],[gdlib],[>= 2.0],[gd.h],[gdImageCreateTrueColor],[
	# gdlib-config --libs upstream does not include -lgd, but only the dependencies
	LIBGD_LIBS="-lgd $LIBGD_LIBS"

],[],[default-on],[http://www.libgd.org/])
GP_CONFIG_MSG([libGD conversion support],[${have_LIBGD}])

dnl ---------------------------------------------------------------------------
dnl Checks for header files.
dnl ---------------------------------------------------------------------------
AC_HEADER_DIRENT
AC_HEADER_STDC
AC_CHECK_HEADERS([sys/param.h sys/mman.h sys/select.h locale.h memory.h getopt.h unistd.h mcheck.h limits.h sys/time.h langinfo.h])
AC_CHECK_HEADERS([stdlib.h unistd.h stdio.h fcntl.h errno.h sys/time.h	\
	sys/param.h sys/select.h termios.h sgetty.h ttold.h ioctl-types.h	\
	fcntl.h sgtty.h sys/ioctl.h sys/time.h termio.h unistd.h	\
	endian.h byteswap.h asm/io.h mntent.h sys/mntent.h sys/mnttab.h \
	scsi/sg.h limits.h sys/file.h])

dnl If sys/mman.h is present, check whether mmap requires the mman
dnl library (see camlibs/st2205/st2205.c st2205_malloc_page_aligned()).
MMAP_LIBS=""
AS_VAR_IF([ac_cv_header_sys_mman_h], [yes], [dnl
  gp_saved_LIBS="$LIBS"
  LIBS=""
  AC_SEARCH_LIBS([mmap], [mman])
  MMAP_LIBS="$LIBS"
  LIBS="$gp_saved_LIBS"
])dnl
AC_SUBST([MMAP_LIBS])

AC_C_INLINE([])
AC_C_CONST([])
dnl FIXME: AC_STRUCT_TIMEZONE

dnl FIXME: Provide regex.h with the corresponding object code for
dnl        platforms which do not have it, e.g. Windows.
AC_CHECK_HEADER([regex.h],
                [AC_DEFINE([HAVE_REGEX], [1],
		           [whether we have regex.h])],
		[])
AC_CHECK_LIB([regex], [regexec])

GP_ASM_SYMVER_SUPPORT

dnl Check for mnt_mountp in struct mnttab
AC_MSG_CHECKING([for mnt_mountp in struct mnttab])
AC_COMPILE_IFELSE([dnl
AC_LANG_PROGRAM([[
#if defined(HAVE_SYS_MNTENT_H) && defined(HAVE_SYS_MNTTAB_H)
# include <sys/mntent.h>
# include <sys/mnttab.h>
#endif
]], [[
struct mnttab mt;
mt.mnt_mountp;
]])dnl
], [dnl
  AC_DEFINE([HAVE_MNTTAB], [1],
            [whether struct mnttag has mnt_mountp field])
  AC_MSG_RESULT([yes])
], [dnl
  AC_MSG_RESULT([no])
])



dnl Checks for library functions.
AC_CHECK_FUNCS([setmntent endmntent strerror snprintf vsnprintf flock])

dnl Check if TIOCM_RTS is included in one of several possible files
AC_TRY_COMPILE([#include <termios.h>], [int foo = TIOCM_RTS;],
			AC_DEFINE([HAVE_RTS_IOCTL], [1], [Define if you have TIOCM_RTS.]))
AC_TRY_COMPILE([#include <termio.h>], [int foo = TIOCM_RTS;],
			AC_DEFINE([HAVE_RTS_IOCTL], [1], [Define if you have TIOCM_RTS.]))
AC_TRY_COMPILE([#include <ioctl-types.h>], [int foo = TIOCM_RTS;],
			AC_DEFINE([HAVE_RTS_IOCTL], [1], [Define if you have TIOCM_TRS.]))
AC_TRY_COMPILE([#include <sys/ioctl.h>], [int foo = TIOCM_RTS;],
			AC_DEFINE([HAVE_RTS_IOCTL], [1], [Define if you have TIOCM_TRS.]))



dnl ---------------------------------------------------------------------------
dnl more header/function/def checks
dnl ---------------------------------------------------------------------------

dnl Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_SIZE_T

dnl Checks for library functions.
AC_CHECK_FUNCS([getenv getopt getopt_long mkdir setenv strdup strncpy strcpy snprintf sprintf vsnprintf gmtime_r statvfs localtime_r lstat inet_aton rand_r])

dnl Find out how to get struct tm
AC_STRUCT_TM

dnl Check for tm_gmtoff in struct tm
AC_MSG_CHECKING([for tm_gmtoff in struct tm])
AC_COMPILE_IFELSE([dnl
AC_LANG_PROGRAM([[
#include <sys/types.h>
#include <$ac_cv_struct_tm>
]], [[
struct tm tm;
tm.tm_gmtoff;
]])dnl
], [dnl
  AC_DEFINE([HAVE_TM_GMTOFF], [1],
            [whether struct tm has tm_gmtoff field])
  AC_MSG_RESULT([yes])
], [dnl
  AC_MSG_RESULT([no])
])

AC_CHECK_HEADERS([sys/mount.h sys/statvfs.h sys/user.h sys/vfs.h], [], [], [
#include <sys/types.h>
#if HAVE_SYS_PARAM_H
# include <sys/param.h>
#endif
])

AC_CHECK_MEMBERS([struct statvfs.f_blocks], [], [], [
#ifdef HAVE_SYS_STATVFS_H
# include <sys/statvfs.h>
#endif
])

dnl Create a header file containing NetBSD-style byte swapping macros
AC_NEED_BYTEORDER_H([libgphoto2/gphoto2-endian.h])


dnl should be obsolete (we're not using grep and tr any more)
dnl dnl Solaris hack for grep and tr
dnl [
dnl if test -n "`echo $host_os | grep '[sS]olaris'`"; then
dnl   TR=/usr/xpg4/bin/tr
dnl   GREP=/usr/xpg4/bin/grep  
dnl else
dnl   TR=tr
dnl   GREP=grep
dnl fi
dnl ]


dnl ---------------------------------------------------------------------------
dnl utility installation directory
dnl
dnl If your system wants utilities installed into ${libexecdir} instead, then
dnl run configure with 'utilsdir=${libexecdir}/${PACKAGE_TARNAME}'.
dnl ---------------------------------------------------------------------------

AC_SUBST([PACKAGE_TARNAME])

if test "x${utilsdir}" = "x"; then utilsdir="\${libdir}/\${PACKAGE_TARNAME}"; fi
AC_ARG_VAR([utilsdir],[Directory where utilities like print-camera-list will be installed])
AC_SUBST([utilsdir])

GP_UDEV([true])


dnl ---------------------------------------------------------------------------
dnl camlib installation directory
dnl ---------------------------------------------------------------------------
GP_DRIVERDIR([camlibdir], [CAMLIBS], [camlibs])


dnl ---------------------------------------------------------------------------
dnl Camera drivers (camlibs)
dnl ---------------------------------------------------------------------------
dnl * See gp-camlibs.m4 for usage details, e.g. for marking camlibs as
dnl   unlisted.
dnl * Please add new camlibs in alphabetical order.
dnl * Selective build:
dnl   $ make -C camlibs canon.la ptp2.la
dnl   or
dnl   $ make -C camlibs GP_CAMLIB_SET="canon.la ptp2.la"
dnl * Selective install:
dnl   $ make GP_CAMLIB_SET="canon.la ptp2.la" install-camlibs
GP_CAMLIB([adc65],[outdated])dnl very old serial camera
GP_CAMLIB([agfa_cl20],[outdated])dnl
GP_CAMLIB([aox],[outdated])dnl
GP_CAMLIB([ax203])dnl
GP_CAMLIB([barbie],[outdated])dnl
GP_CAMLIB([canon])dnl
GP_CAMLIB([casio_qv],[outdated])dnl
GP_CAMLIB([clicksmart310],[outdated])dnl
GP_CAMLIB([digigr8])dnl
GP_CAMLIB([digita],[outdated])dnl
GP_CAMLIB([dimera3500],[outdated])dnl
GP_CAMLIB([directory])dnl
AM_COND_IF([HAVE_LIBGD], [dnl
GP_CAMLIB([docupen])dnl
])
GP_CAMLIB([enigma13],[outdated])dnl
GP_CAMLIB([fuji],[outdated])dnl
GP_CAMLIB([gsmart300],[outdated])dnl
GP_CAMLIB([hp215],[outdated])dnl
GP_CAMLIB([iclick],[outdated])dnl
GP_CAMLIB([jamcam],[outdated])dnl
GP_CAMLIB([jd11],[outdated])dnl
GP_CAMLIB([jl2005a])dnl
GP_CAMLIB([jl2005c])dnl
GP_CAMLIB([kodak_dc120],[outdated])dnl
GP_CAMLIB([kodak_dc210],[outdated])dnl
GP_CAMLIB([kodak_dc240])dnl
GP_CAMLIB([kodak_dc3200],[outdated])dnl
GP_CAMLIB([kodak_ez200],[outdated])dnl
GP_CAMLIB([konica],[outdated])dnl
GP_CAMLIB([konica_qm150],[outdated])dnl
GP_CAMLIB([largan],[outdated])dnl
GP_CAMLIB([lg_gsm],[outdated])dnl
AM_COND_IF([HAVE_LIBCURL], [dnl
AM_COND_IF([HAVE_LIBXML2], [dnl
GP_CAMLIB([lumix])dnl
])
])
GP_CAMLIB([mars])dnl
GP_CAMLIB([dimagev])dnl
GP_CAMLIB([mustek],[outdated])dnl
GP_CAMLIB([panasonic_coolshot],[outdated])dnl
GP_CAMLIB([panasonic_l859],[outdated])dnl
GP_CAMLIB([panasonic_dc1000],[outdated])dnl
GP_CAMLIB([panasonic_dc1580],[outdated])dnl
GP_CAMLIB([pccam300],[outdated])dnl
GP_CAMLIB([pccam600],[outdated])dnl
GP_CAMLIB([pentax])dnl
GP_CAMLIB([polaroid_pdc320],[outdated])dnl
GP_CAMLIB([polaroid_pdc640],[outdated])dnl
GP_CAMLIB([polaroid_pdc700],[outdated])dnl
GP_CAMLIB([ptp2])dnl
GP_CAMLIB([quicktake1x0])dnl
GP_CAMLIB([ricoh],[outdated])dnl
GP_CAMLIB([ricoh_g3])dnl
GP_CAMLIB([samsung],[outdated])dnl
GP_CAMLIB([sierra])dnl
GP_CAMLIB([sipix_blink], [unlisted])dnl did not find out the correct decompressor, unfinished
GP_CAMLIB([sipix_blink2],[outdated])dnl
GP_CAMLIB([sipix_web2],[outdated])dnl
GP_CAMLIB([smal],[outdated])dnl
GP_CAMLIB([sonix])dnl
GP_CAMLIB([sony_dscf1],[outdated])dnl
GP_CAMLIB([sony_dscf55],[outdated])dnl
GP_CAMLIB([soundvision],[outdated])dnl
GP_CAMLIB([spca50x],[outdated])dnl
GP_CAMLIB([sq905])dnl
GP_CAMLIB([st2205])dnl
GP_CAMLIB([stv0674],[outdated])dnl
GP_CAMLIB([stv0680],[outdated])dnl
GP_CAMLIB([sx330z],[outdated])dnl
GP_CAMLIB([template], [unlisted])dnl
GP_CAMLIB([topfield])dnl
GP_CAMLIB([toshiba_pdrm11],[outdated])dnl
GP_CAMLIB([tp6801])dnl
dnl
GP_CAMLIBS_DEFINE()dnl


dnl --------------------------------------------------------------------
dnl documentation
dnl --------------------------------------------------------------------
GP_CHECK_DOXYGEN()dnl
GP_INTERNAL_DOCS()dnl
GP_BUILD_GTK_DOCS()dnl
AC_SUBST([camlibdocdir], ['${docdir}/camlibs'])


dnl --------------------------------------------------------------------
dnl initialize convenience packaging
dnl --------------------------------------------------------------------
GPKG_CHECK_LINUX()dnl Check whether to package for a linux system


dnl --------------------------------------------------------------------
dnl guess directory to install *.pc into
dnl --------------------------------------------------------------------
pkgconfigdir='${libdir}/pkgconfig'
AC_SUBST([pkgconfigdir])


dnl ---------------------------------------------------------------------------
dnl libexif: The CameraFilesystem can use libexif for extracting thumbnails
dnl	     out of EXIF data. Similarly, it can extract the mtime of
dnl	     a file. 
dnl libexif: The virtual usb camera driver can use libexif for extracting thumbnails
dnl	     out of EXIF data. Similarly, it can extract the mtime of
dnl	     a file.
dnl	     libexif is available from
dnl	     http://www.sourceforge.net/projects/libexif
dnl ---------------------------------------------------------------------------
GP_CHECK_LIBRARY([LIBEXIF],[libexif],[>= 0.6.13],
		 [libexif/exif-data.h],[exif_data_new],[
AC_MSG_CHECKING([whether we use a version of libexif with ExifData.ifd[[]]])
# Check for libexif version
dnl FIXME: Use AC_CHECK_MEMBER?
CPPFLAGS_save="$CPPFLAGS"
CPPFLAGS="$LIBEXIF_CFLAGS"
AC_COMPILE_IFELSE([AC_LANG_SOURCE([[
/* CC=$CC */
/* CPPFLAGS=${CPPFLAGS} */
/* LDFLAGS=${LDFLAGS} */
#include <libexif/exif-data.h>
#include <libexif/exif-content.h>
]],[[
	ExifData ed;
	ExifContent *ec0, *ec1;
	ec0 = &ed.ifd[0];
	ec1 = &ed.ifd[1];
]])], [dnl
   AC_DEFINE([HAVE_LIBEXIF_IFD], [1],
	     [whether we use a version of libexif with ExifData.ifd[[]]])
   AC_MSG_RESULT([yes])
], [dnl
   AC_MSG_RESULT([no])
])
CPPFLAGS="$CPPFLAGS_save"
],[],[default-on],[http://www.sourceforge.net/projects/libexif])dnl

dnl ---------------------------------------------------------------------------
dnl serial
dnl ---------------------------------------------------------------------------
serial_msg=yes
have_serial=true
try_ttylock=true
try_lockdev=true
try_resmgr=true

if test "$ac_cv_header_sgtty_h" = "no"
then
  have_serial=false
  serial_msg=no
fi

AC_ARG_ENABLE([serial],
	[AS_HELP_STRING([--disable-serial],
			[do not compile in SERIAL support])],
[dnl
	if test x$enableval = xno; then
		have_serial=false
		serial_msg=no
		try_ttylock=false
		try_lockdev=false
		try_resmgr=false
	fi
])
if $have_serial; then
	IOLIB_LIST="$IOLIB_LIST serial"
	AC_DEFINE([HAVE_SERIAL], [1],
	          [Whether you have serial support enabled])
fi
GP_CONFIG_MSG([Serial ports])
GP_CONFIG_MSG([Serial support],[$serial_msg])

SERIAL_LIBS=""
if $have_serial; then

dnl -----------------------------------------
dnl Serial port locking: We try to use either
dnl  (1) ttylock.h
dnl  (2) lockdev.h
dnl -----------------------------------------
AC_DEFUN([GP_SERLOCK],[dnl
# $0([$1])
AC_ARG_ENABLE([$1],
[AS_HELP_STRING([--disable-][$1],
                [do not use ][$1][ library])dnl
], [dnl
	if test x$enableval = xno; then
		try_[$1]=false
	fi
])
])dnl
GP_SERLOCK([ttylock])dnl
GP_SERLOCK([lockdev])dnl

ttylock_msg=no
if $try_ttylock; then
	AC_CHECK_HEADER([lockdev.h])
	AC_CHECK_HEADER([ttylock.h], [dnl
		lockdev_result="no"
		AC_TRY_LINK([#include <ttylock.h>],[ttylocked ("/dev/foo");],[
			lockdev_result="no"
			AC_DEFINE([HAVE_TTYLOCK], [1],
			          [Define if you have ttylock based tty locking.])
			ttylock_msg=yes
			try_lockdev=false,
			save_LIBS="$LIBS"
			LIBS="$LIBS -llockdev"
			AC_TRY_LINK([#include <ttylock.h>],[ttylocked ("/dev/foo");],[
				lockdev_result="yes"
				AC_DEFINE([HAVE_TTYLOCK], [1],
				          [Define if you have ttylock based tty locking.])
				ttylock_msg=yes
				try_lockdev=false
				SERIAL_LIBS=-llockdev
			])
			LIBS="$save_LIBS"
		])
		AC_MSG_CHECKING([if ttylock needs lockdev])
		AC_MSG_RESULT([${lockdev_result}])
	], [], [#ifdef HAVE_LOCKDEV_H
# include <lockdev.h>
#endif
	])
fi
GP_CONFIG_MSG([ttylock locking],[${ttylock_msg}])

lockdev_msg=no
if $try_lockdev; then
	AC_CHECK_LIB([lockdev], [dev_lock], [dnl
		AC_CHECK_HEADER([lockdev.h], [dnl
			AC_DEFINE([HAVE_LOCKDEV], [1],
			          [Define if you have dev_lock/lockdev based locking.])
			lockdev_msg=yes
			SERIAL_LIBS=-llockdev
		])
	])
fi
GP_CONFIG_MSG([lockdev locking],[${lockdev_msg}])

fi # have_serial

AC_SUBST([SERIAL_LIBS])


dnl ---------------------------------------------------------------------------
dnl libusb
dnl ---------------------------------------------------------------------------

dnl libpthread is dynamically linked by libusb, which is dynamically loaded
dnl but newer Linux systems need it on startup, not later. So link libgphoto2_port
dnl against libpthread
AC_CHECK_LIB([pthread], [pthread_create])

dnl ---------------------------------------------------------------------------
dnl libusb1
dnl ---------------------------------------------------------------------------
GP_CONFIG_MSG([USB ports])
GP_CHECK_LIBRARY([LIBUSB1],[libusb-1.0],[>= 1.0.0],
		[libusb.h],[libusb_init],[
        case "$host" in
          *-linux*)
	  IOLIB_LIST="$IOLIB_LIST usb1 usbdiskdirect usbscsi"
          ;;
          *)
	  IOLIB_LIST="$IOLIB_LIST usb1"
          ;;
        esac

	# only in libusbx? but not in traditional libusb 1.0
	# note that the library is not always named libusb-1.0.so , e.g. on freebsd it is not.
	save_LIBS="$LIBS"
	LIBS="$LIBS $LIBUSB1_LIBS"
	AC_CHECK_FUNC([libusb_strerror], [dnl
		AC_DEFINE([HAVE_LIBUSB_STRERROR], [1],
		          [Define if libusb-1.0 has libusb_strerror])
	])
	AC_CHECK_FUNC([libusb_wrap_sys_device], [dnl
		AC_DEFINE([HAVE_LIBUSB_WRAP_SYS_DEVICE], [1],
		          [Define if libusb-1.0 has libusb_wrap_sys_device])
	])

	save_CFLAGS="$CFLAGS"
	CFLAGS="$CFLAGS $LIBUSB1_CFLAGS"

	AC_COMPILE_IFELSE([dnl
	AC_LANG_PROGRAM([[
	# include "libusb.h"
	]], [[
	enum libusb_option opt = LIBUSB_OPTION_NO_DEVICE_DISCOVERY;
	]])dnl
	], [dnl
	  AC_DEFINE([HAVE_LIBUSB_OPTION_NO_DEVICE_DISCOVERY], [1],
		    [whether we have LIBUSB_OPTION_NO_DEVICE_DISCOVERY])
	  AC_MSG_RESULT([yes])
	], [dnl
	  AC_MSG_RESULT([no])
	])

	LIBS="$save_LIBS"
	CFLAGS="$save_CFLAGS"
], [],
		[default-on],
		[http://libusb.sourceforge.net/]
)
# We select the old libusb 0 only if we are not doing libusb1
GP_CHECK_LIBRARY([LIBUSB],[libusb],[>= 0.1.5],
		[usb.h],[usb_open],[
	case "$host" in
	  *-*-mingw* | *-*-cygwin* | *-*-msvc* )
	  dnl Windows itself has usb.h we mis-detect, in that case remove access to the other usb.h
	  IOLIB_LIST="$IOLIB_LIST usb"
	  ;;
          *-linux*)
	  if test "x$have_LIBUSB1" != xyes; then
		IOLIB_LIST="$IOLIB_LIST usb usbdiskdirect usbscsi"
          else
		GP_CONFIG_MSG([libusb0 support],[detected, but disabled (libusb1 support is enabled)])
          fi
	  ;;
	  *)
	  if test "x$have_LIBUSB1" != xyes; then
		IOLIB_LIST="$IOLIB_LIST usb"
          else
		GP_CONFIG_MSG([libusb0 support],[detected, but disabled (libusb1 support is enabled)])
          fi
	  ;;
	esac
], [],
		[default-on],
		[http://libusb.sourceforge.net/]
)
dnl depends on libusb's availability
GP_UDEV([test "x$have_LIBUSB" = xyes || test "x$have_LIBUSB1" = xyes])


AC_ARG_ENABLE([disk],
	[AS_HELP_STRING([--disable-disk],
	                [disable the 'disk' port driver])],
	[],
	[enable_disk=yes])

dnl disk port also works everywhere, but it's not really necessary
if test "x$enable_disk" = "xyes"; then
	IOLIB_LIST="$IOLIB_LIST disk"
fi

AC_ARG_ENABLE([vusb],
	[AS_HELP_STRING([--enable-vusb],
	                [enable the 'vusb' virtual USB port driver])],
	[], [dnl
		enable_vusb=no
		GP_CONFIG_MSG([virtual USB support],[disabled, no virtual PTP test camera])
	]
)

dnl disk port also works everywhere, but it's not really necessary
if test "x$enable_vusb" = "xyes"; then
	IOLIB_LIST="$IOLIB_LIST vusb"
fi

AC_ARG_ENABLE([ptpip],
	[AS_HELP_STRING([--disable-ptpip],
	                [disable the 'ptpip' port driver for TCP/IP connected PTP cameras])],
	[], [dnl
		enable_ptpip=yes
])
dnl ptpip - works 'everywhere' with TCP/IP stack.
AS_VAR_IF([enable_ptpip], [yes], [dnl
	IOLIB_LIST="$IOLIB_LIST ptpip"
])

# ----------------------------------------------------------------------
# Define IOLIB stuff
# ----------------------------------------------------------------------


dnl ---------------------------------------------------------------------------
dnl iolib installation directory
dnl ---------------------------------------------------------------------------

GP_DRIVERDIR([iolibdir], [IOLIBS], [iolibs (port libraries)])


dnl ---------------------------------------------------------------------------
dnl List of iolibs (port drivers)
dnl ---------------------------------------------------------------------------
AC_SUBST([IOLIB_LIST])
for x in ${IOLIB_LIST}; do
    IOLIB_LTLIST="${IOLIB_LTLIST} ${x}.la"
done
AC_SUBST([IOLIB_LTLIST])

sorted_iolib_list="$(echo "${IOLIB_LIST}" | tr ' ' '\n' | sort | ${SED} '/^$/d' | tr '\n' ' ' | ${SED} 's/ $//')"
AC_DEFINE_UNQUOTED([IOLIB_LIST], ["${sorted_iolib_list}"],
                   [Define as string containing a list of the iolibs])
GP_CONFIG_MSG([General])
GP_CONFIG_MSG([IOLIBs], [${sorted_iolib_list}])


dnl ----------------------------------------------------------------------
dnl GNU regex?
dnl ----------------------------------------------------------------------
AC_CHECK_FUNC([re_compile_pattern],
              [AC_DEFINE([HAVE_GNU_REGEX], [1],
	                 [Define if you have GNU regex.])])


dnl ----------------------------------------------------------------------
dnl disable debugging if requested
dnl ----------------------------------------------------------------------
AC_ARG_ENABLE([debug],
  [AS_HELP_STRING([--disable-debug],
                  [do not include debugging code])],
  [dnl
    AS_VAR_IF([enableval], [no], [dnl
      AC_DEFINE([DISABLE_DEBUGGING], [1],
                [Define if you want to disabled debugging.])
    ])
])


# ---------------------------------------------------------------------------
# clean up
# ---------------------------------------------------------------------------
GP_SET_CLEAN_FILES


# ---------------------------------------------------------------------------
# Create output files
# ---------------------------------------------------------------------------
AC_CONFIG_FILES([
  Makefile
  gphoto2-config
  camlibs/Makefile
  camlibs/canon/doc/Makefile
  libgphoto2/Makefile
  libgphoto2.pc
  libgphoto2-uninstalled.pc
  examples/Makefile
  tests/Makefile
  packaging/Makefile
  packaging/generic/Makefile
  po/Makefile.in
  doc/Makefile
  doc/Doxyfile
  doc/Doxyfile-internals
  doc/api/Makefile
  libgphoto2_port/Makefile
  libgphoto2_port/po/Makefile.in
  libgphoto2_port/libgphoto2_port/Makefile
  libgphoto2_port/libgphoto2_port.pc
  libgphoto2_port/libgphoto2_port-uninstalled.pc
  libgphoto2_port/gphoto2-port-config
  libgphoto2_port/tests/Makefile
  libgphoto2_port/doc/Makefile
])
AC_OUTPUT

AS_IF([test "x$CDPATH" != "x"], [dnl
  AC_MSG_WARN([

    #=========================================================#
    # You have CDPATH set. You may have to run "unset CDPATH" #
    # before running "make dist".                             #
    #=========================================================#
])
])dnl

GP_CONFIG_OUTPUT

dnl Catch the Gentoo folks about to shoot themselves in the foot.
dnl Just enabling "foo" often does not make a camera made by
dnl manufacturer "Foo" work.
GP_CAMLIBS_CONDITIONAL_WARNING

cat<<EOF
Please check whether the configuration I have detected matches what
you would like to have. E.g. make sure that USB support is there if
you intend to use USB cameras with ${PACKAGE_NAME}.

Please also check that PKG_CONFIG_PATH contains
    ${pkgconfigdir}
before compiling any libgphoto2 frontend.
EOF
