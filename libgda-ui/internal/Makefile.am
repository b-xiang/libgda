noinst_LTLIBRARIES = libgda-ui-internal.la

AM_CPPFLAGS = \
	-I$(top_builddir) \
	-I$(top_srcdir) \
	-I$(top_srcdir)/libgda \
	$(COREDEPS_CFLAGS) \
	$(COREDEPS_WFLAGS) \
	$(GTK_CFLAGS)

libgda_ui_internal_la_SOURCES = \
	gdaui-dsn-selector.c \
	gdaui-dsn-selector.h \
	gdaui-provider-auth-editor.c \
	gdaui-provider-auth-editor.h \
	gdaui-provider-spec-editor.c \
	gdaui-provider-spec-editor.h \
	popup-container.h \
	popup-container.c \
	utility.h \
	utility.c
