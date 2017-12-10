liblightdm_qt_sources = [ 'greeter.cpp',
                          'power.cpp',
                          'sessionsmodel.cpp',
                          'usersmodel.cpp' ]
liblightdm_qt_headers = [ 'QLightDM/greeter.h',
                          'QLightDM/power.h',
                          'QLightDM/sessionsmodel.h',
                          'QLightDM/usersmodel.h' ]
liblightdm_qt_header_aliases = [ 'QLightDM/Greeter',
                                 'QLightDM/Power',
                                 'QLightDM/SessionsModel',
                                 'QLightDM/UsersModel' ]

if get_option ('with_liblightdm_qt')
    qt = import ('qt4')

    qt_dep = dependency ('qt4', modules: [ 'Core', 'DBus', 'Gui'])
    moc_files = qt.preprocess (moc_headers: liblightdm_qt_headers)
    liblightdm_qt = shared_library ('lightdm-qt-3',
                                    liblightdm_qt_sources, moc_files,
                                    dependencies: [ qt_dep, liblightdm_gobject_dep, gobject_dep ],
                                    cpp_args: '-DQT_NO_KEYWORDS',
                                    soversion: '0',
                                    install: true)

    install_headers (liblightdm_qt_headers, liblightdm_qt_header_aliases,
                     subdir: 'lightdm-qt-3/QLightDM')

    pkgconfig.generate (libraries: liblightdm_qt,
                        subdirs: 'lightdm-qt-3',
                        filebase: 'liblightdm-qt-3',
                        version: meson.project_version (),
                        name: 'liblightdm-qt',
                        description: 'LightDM Qt4 client library',
                        requires: [ 'Qt5Core', 'Qt5Gui' ])
endif

if get_option ('with_liblightdm_qt5')
    qt = import ('qt5')

    qt_dep = dependency ('qt5', modules: [ 'Core', 'DBus', 'Gui'])
    moc_files = qt.preprocess (moc_headers: liblightdm_qt_headers)
    liblightdm_qt5 = shared_library ('lightdm-qt5-3',
                                     liblightdm_qt_sources, moc_files,
                                     dependencies: [ qt_dep, liblightdm_gobject_dep, gobject_dep ],
                                     cpp_args: [ '-DQT_NO_KEYWORDS', '-DQT_DISABLE_DEPRECATED_BEFORE=QT_VERSION_CHECK(4, 0, 0)' ],
                                     soversion: '0',
                                     install: true)

    install_headers (liblightdm_qt_headers, liblightdm_qt_header_aliases,
                     subdir: 'lightdm-qt5-3/QLightDM')

    pkgconfig.generate (libraries: liblightdm_qt5,
                        subdirs: 'lightdm-qt5-3',
                        filebase: 'liblightdm-qt5-3',
                        version: meson.project_version (),
                        name: 'liblightdm-qt5',
                        description: 'LightDM Qt5 client library',
                        requires: [ 'Qt5Core', 'Qt5Gui' ])

endif
