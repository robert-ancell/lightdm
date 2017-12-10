# FIXME: Check noinstall
# -DCONFIG_DIR=\"$(sysconfdir)/lightdm\"
libcommon = static_library ('libcommon',
                            [ 'configuration.c', 'configuration.h',
                              'dmrc.c', 'dmrc.h',
                              'privileges.c', 'privileges.h',
                              'user-list.c', 'user-list.h' ],
                            dependencies: [ glib_dep ],
                            include_directories: [ config_inc ])

libcommon_inc = include_directories ('.')
libcommon_dep = declare_dependency (link_with: libcommon,
                                    include_directories: libcommon_inc)
