liblightdm_sources = [ 'greeter.c',
                       'system.c',
                       'language.c',
                       'layout.c',
                       'power.c',
                       'session.c',
                       'user.c' ]
liblightdm_headers = [ 'lightdm.h',
                       'lightdm/greeter.h',
                       'lightdm/system.h',
                       'lightdm/language.h',
                       'lightdm/layout.h',
                       'lightdm/power.h',
                       'lightdm/session.h',
                       'lightdm/user.h']

liblightdm_gobject = shared_library ('lightdm-gobject-1',
                                     liblightdm_sources + liblightdm_headers,
                                     dependencies: [ libcommon_dep, glib_dep, gio_unix_dep, libxklavier_dep, x11_dep ],
                                     include_directories: [ config_inc ],
                                     soversion: '0',
                                     link_depends: 'liblightdm-gobject-1.map',
                                     install: true)

liblightdm_gobject_inc = include_directories ('.')
liblightdm_gobject_dep = declare_dependency (link_with: liblightdm_gobject,
                                             include_directories: liblightdm_gobject_inc)

install_headers (liblightdm_headers,
                 subdir: 'lightdm-gobject-1')

pkgconfig.generate (libraries: liblightdm_gobject,
                    subdirs: 'lightdm-gobject-1',
                    filebase: 'liblightdm-gobject-1',
                    version: meson.project_version (),
                    name: 'liblightdm-gobject',
                    description: 'LightDM client library',
                    requires_private: [ 'glib-2.0', 'gio-2.0', 'gio-unix-2.0', 'gobject-2.0', 'libxklavier', 'x11' ])

if get_option ('with_introspection')
    gnome.generate_gir (liblightdm_gobject,
                        namespace: 'LightDM',
                        nsversion: '1',
                        sources: liblightdm_sources + liblightdm_headers,
                        symbol_prefix: 'lightdm',
                        includes: [ 'GObject-2.0', 'Gio-2.0' ],
                        install: true,
                        extra_args: ['--c-include', 'lightdm.h' ])

    if get_option ('with_vapi')
        gnome.generate_vapi ('liblightdm-gobject-1',
                             sources: [ 'LightDM-1.gir', 'LightDM-1-custom.vala' ],
                             packages: [ 'gio-2.0', 'posix' ],
                             install: true)
    endif
endif
