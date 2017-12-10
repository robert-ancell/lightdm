AC_CHECK_FUNCS(setresgid setresuid clearenv)

AC_ARG_ENABLE([libaudit],
    AS_HELP_STRING([--enable-libaudit],
                   [Enable libaudit logging of login and logout events [[default=auto]]]),
    [enable_libaudit=$enableval],
    [enable_libaudit=auto])
use_libaudit=no    
if test x"$enable_libaudit" != "xno"; then
    AC_CHECK_LIB([audit], [audit_log_user_message],
                 [use_libaudit=yes
                  AC_DEFINE(HAVE_LIBAUDIT, 1, [libaudit support])
                  LIGHTDM_LIBS="${LIGHTDM_LIBS} -laudit"
                 ],
                 [if test "x$enable_libaudit" != xauto; then
                    AC_MSG_FAILURE(
                      [--enable-libaudit was given, but test for libaudit failed])
                  fi
                 ])
fi

AC_MSG_CHECKING(whether to build tests)
AC_ARG_ENABLE(tests,
        AS_HELP_STRING([--disable-tests], [Disable tests building]),
        [], [enable_tests="yes"])
AM_CONDITIONAL(COMPILE_TESTS, test x"$enable_tests" != "xno")

dnl ###########################################################################
dnl Configurable values
dnl ###########################################################################

DEFAULT_USER_SESSION=default
AC_ARG_WITH(user-session,
            AS_HELP_STRING(--with-user-session=<name>,
                           Session to use for user accounts),
    if test x$withval != x; then
        DEFAULT_USER_SESSION="$withval"
    fi
)
AC_SUBST(DEFAULT_USER_SESSION)
AC_DEFINE_UNQUOTED(DEFAULT_USER_SESSION, "$DEFAULT_USER_SESSION", User session)

DEFAULT_GREETER_SESSION=default
AC_ARG_WITH(greeter-session,
            AS_HELP_STRING(--with-greeter-session=<session>,
                           Greeter session),
    if test x$withval != x; then
        DEFAULT_GREETER_SESSION="$withval"
    fi
)
AC_SUBST(DEFAULT_GREETER_SESSION)
AC_DEFINE_UNQUOTED(DEFAULT_GREETER_SESSION, "$DEFAULT_GREETER_SESSION", Greeter session)

GREETER_USER=lightdm
AC_ARG_WITH(greeter-user,
            AS_HELP_STRING(--with-greeter-user=<username>,
                           User to run greeter as),
    if test x$withval != x; then
        GREETER_USER="$withval"
    fi
)
AC_SUBST(GREETER_USER)
AC_DEFINE_UNQUOTED(GREETER_USER, "$GREETER_USER", User to run greeter as)

dnl ###########################################################################
dnl Documentation
dnl ###########################################################################

GTK_DOC_CHECK
YELP_HELP_INIT

dnl ###########################################################################
dnl Summary
dnl ###########################################################################

echo "
                    Light Display Manager $VERSION
                    ===========================

        prefix:                   $prefix
        Greeter session:          $DEFAULT_GREETER_SESSION
        Greeter user:             $GREETER_USER
        User session:             $DEFAULT_USER_SESSION
        GObject introspection:    $found_introspection
        Vala bindings:            $enable_vala
        liblightdm-qt:            $compile_liblightdm_qt4
        liblightdm-qt5:           $compile_liblightdm_qt5
        libaudit support:         $use_libaudit
        Enable tests:             $enable_tests
"
