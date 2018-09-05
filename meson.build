project ('lightdm', ['c'],
         version: '1.28.0',
         license: 'GPLv3+',
         default_options: [
             'warning_level=1',
             'buildtype=debugoptimized',
         ],
         meson_version: '>= 0.37.1')

i18n = import ('i18n')

# Paths
mandir = join_paths (get_option ('prefix'), get_option ('mandir'))
localedir = join_paths (get_option ('prefix'), get_option ('localedir'))
datadir = join_paths (get_option ('prefix'), get_option ('datadir'))
configdir = join_paths (get_option ('prefix'), get_option ('sysconfdir'), 'lightdm')

# Dependencies
glib_dep = dependency ('glib-2.0', version: '>= 2.44')
gobject_dep = dependency ('gobject-2.0')
gio_dep = dependency ('gio-2.0', version: '>= 2.26')
gio_unix_dep = dependency ('gio-unix-2.0')
xdmcp_dep = dependency ('xdmcp')
xcb_dep = dependency ('xcb')
libxklavier_dep = dependency ('libxklavier')
x11_dep = dependency ('x11')
qt4core_dep = dependency ('QtCore')
qt4dbus_dep = dependency ('QtDBus')
qt4gui_dep = dependency ('QtGui')
qt5core_dep = dependency ('Qt5Core')
qt5dbus_dep = dependency ('Qt5DBus')
qt5gui_dep = dependency ('Qt5Gui')

subdir ('common')
subdir ('data')
subdir ('help')
subdir ('liblightdm-gobject')
subdir ('liblightdm-qt')
subdir ('po')
subdir ('src')
subdir ('tests')
