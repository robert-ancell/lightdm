sbin_PROGRAMS = lightdm
bin_PROGRAMS = dm-tool

lightdm_CFLAGS = \
	$(WARN_CFLAGS) \
	$(LIGHTDM_CFLAGS) \
	-I"$(top_srcdir)/common" \
	-DSBIN_DIR=\"$(sbindir)\" \
	-DUSERS_DIR=\"$(localstatedir)/lib/lightdm-data\" \
	-DLOG_DIR=\"$(localstatedir)/log/lightdm\" \
	-DRUN_DIR=\"$(localstatedir)/run/lightdm\" \
	-DCACHE_DIR=\"$(localstatedir)/cache/lightdm\" \
	-DSESSIONS_DIR=\"$(pkgdatadir)/sessions:$(datadir)/xsessions:$(datadir)/wayland-sessions\" \
	-DWAYLAND_SESSIONS_DIR=\"$(datadir)/wayland-sessions\" \
	-DREMOTE_SESSIONS_DIR=\"$(pkgdatadir)/remote-sessions\"

lightdm_LDADD = \
	$(LIGHTDM_LIBS) \
	$(top_builddir)/common/libcommon.la \
	-lgcrypt \
	-lpam

dm_tool_SOURCES = \
	dm-tool.c

dm_tool_CFLAGS = \
	$(WARN_CFLAGS) \
	$(LIGHTDM_CFLAGS) \
	-DLOCALE_DIR=\"$(datadir)/locale\"

dm_tool_LDADD = \
	$(LIGHTDM_LIBS)

libexec_PROGRAMS = lightdm-guest-session

lightdm_guest_session_SOURCES = lightdm-guest-session.c

lightdm_guest_session_CFLAGS = \
	$(WARN_CFLAGS) \
	$(LIGHTDM_CFLAGS)

EXTRA_DIST = \
	display-manager.xml
