project ('lightdm', ['c', 'cpp'],
         version: '1.25.0',
         license: 'GPLv3+',
         default_options: [
             'warning_level=1',
             'buildtype=debugoptimized',
         ],
         meson_version: '>= 0.37.1')

gnome = import ('gnome')
i18n = import ('i18n')
pkgconfig = import ('pkgconfig')

# Paths
mandir = join_paths (get_option ('prefix'), get_option ('mandir'))
localedir = join_paths (get_option ('prefix'), get_option ('localedir'))
datadir = join_paths (get_option ('prefix'), get_option ('datadir'))
icondir = join_paths (datadir, 'simple-scan', 'icons')
sysconfdir = join_paths (get_option ('prefix'), get_option ('sysconfdir'))
libexecdir = join_paths (get_option ('prefix'), get_option ('libexecdir'))

# Dependencies
glib_dep = dependency ('glib-2.0', version: '>= 2.44')
gobject_dep = dependency ('gobject-2.0')
gio_dep = dependency ('gio-2.0', version: '>= 2.26')
gio_unix_dep = dependency ('gio-unix-2.0')
xdmcp_dep = dependency ('xdmcp')
xcb_dep = dependency ('xcb')
libxklavier_dep = dependency ('libxklavier')
x11_dep = dependency ('x11')
sane_dep = dependency ('sane-backends')
msgfmt = find_program  ('msgfmt')
itstool = find_program  ('itstool')

cc = meson.get_compiler ('c')
gcrypt_dep = cc.find_library ('gcrypt')
pam_dep = cc.find_library ('pam')

#	-DCONFIG_DIR=\"$(sysconfdir)/lightdm\" \
#	-DSESSIONS_DIR=\"$(pkgdatadir)/sessions:$(datadir)/xsessions:$(datadir)/wayland-sessions\" \
#	-DWAYLAND_SESSIONS_DIR=\"$(datadir)/wayland-sessions\" \
#	-DREMOTE_SESSIONS_DIR=\"$(pkgdatadir)/remote-sessions\"
#	-DSBIN_DIR=\"$(sbindir)\" \
#	-DUSERS_DIR=\"$(localstatedir)/lib/lightdm-data\" \
#	-DLOG_DIR=\"$(localstatedir)/log/lightdm\" \
#	-DRUN_DIR=\"$(localstatedir)/run/lightdm\" \
#	-DCACHE_DIR=\"$(localstatedir)/cache/lightdm\" \
conf_data = configuration_data ()
configure_file (input: 'config.h.in',
                output: 'config.h',
                configuration: conf_data)
config_inc = include_directories ('.')

subdir ('common')
subdir ('po')
subdir ('data')
#subdir ('doc')
subdir ('help')
subdir ('liblightdm-gobject')
subdir ('liblightdm-qt')
subdir ('src')
#subdir ('tests')
