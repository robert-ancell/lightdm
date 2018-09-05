libcommon = static_library ('common',
                            [ 'configuration.c', 'configuration.h',
                              'dmrc.c', 'dmrc.h',
                              'privileges.c', 'privileges.h',
                              'user-list.c', 'user-list.h' ],
                            dependencies: [ glib_dep ],
                            c_args: [ '-DCONFIG_DIR="@0@"'.format (configdir) ] )

libcommon_dep = declare_dependency (include_directories: include_directories ('.'),
                                    link_with: libcommon)
