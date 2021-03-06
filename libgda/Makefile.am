QUIET_GEN = $(Q:@=@echo ' GEN '$@;)

lib_LTLIBRARIES = libgda-6.0.la

TESTS_ENVIRONMENT = GDA_TOP_SRC_DIR="$(abs_top_srcdir)" GDA_TOP_BUILD_DIR="$(abs_top_builddir)"
check_PROGRAMS = test-cnc-open test-cnc-exec test-cnc-meta
TESTS = test-cnc-open test-cnc-exec test-cnc-meta

SUBDIRS = sqlite handlers binreloc sql-parser providers-support thread-wrapper $(VALA_EXTENSIONS)

DEF_FLAGS=
if BDB 
GDA_BDB_H=gda-data-model-bdb.h
GDA_BDB_S=gda-data-model-bdb.c
DEF_FLAGS+=-DHAVE_BDB
endif

if LDAP 
GDA_LDAP_H=gda-data-model-ldap.h gda-tree-mgr-ldap.h
GDA_LDAP_S=gda-data-model-ldap.c gda-tree-mgr-ldap.c
DEF_FLAGS+=-DHAVE_LDAP
endif

GLOBAL_CFLAGS = \
	-I$(top_srcdir) \
	-I$(top_builddir) \
	-I$(top_srcdir)/libgda/sqlite \
	-I$(top_srcdir)/libgda \
	-I$(top_builddir)/libgda/sqlite \
	-I$(top_builddir)/libgda \
	-DABI_VERSION=\""$(GDA_ABI_VERSION)"\" \
	$(COREDEPS_CFLAGS) \
	$(BDB_CFLAGS) \
	-DBDB_LIB=\""$(BDB_LIB)"\" \
	$(GIO_CFLAGS) $(LIBSECRET_CFLAGS) $(GNOME_KEYRING_CFLAGS)

AM_CPPFLAGS = \
	$(GLOBAL_CFLAGS) \
	$(COREDEPS_WFLAGS)

_gda_marshal_built_files = gda-marshal.h gda-marshal.c

gda-marshal.h: gda-marshal.list $(GLIB_GENMARSHAL)
	$(GLIB_GENMARSHAL) $< --header --prefix=_gda_marshal > $@
gda-marshal.c: gda-marshal.list $(GLIB_GENMARSHAL)
	$(GLIB_GENMARSHAL) $< --body --prefix=_gda_marshal > $@

mkkeywordhash$(EXEEXT_FOR_BUILD): $(top_srcdir)/libgda/sqlite/mkkeywordhash.c
	$(CC_FOR_BUILD) -g -o mkkeywordhash$(EXEEXT_FOR_BUILD) $(GDA_DEBUG_FLAGS) $<

keywords_hash.code: mkkeywordhash$(EXEEXT_FOR_BUILD) $(top_srcdir)/libgda/keywords.list
	./mkkeywordhash$(EXEEXT_FOR_BUILD) $(top_srcdir)/libgda/keywords.list > keywords_hash.code

gda_headers = \
	gda-attributes-manager.h \
	gda-batch.h \
	gda-blob-op.h \
	gda-column.h \
	gda-config.h \
	gda-connection-event.h \
	gda-connection.h \
	gda-connection-private.h \
	gda-data-comparator.h \
	gda-data-handler.h \
	gda-data-model-array.h \
	gda-data-model.h \
	$(GDA_BDB_H) \
	$(GDA_LDAP_H) \
	gda-data-model-dir.h \
	gda-data-model-extra.h \
	gda-data-model-import.h \
	gda-data-model-iter.h \
	gda-data-model-iter-extra.h \
	gda-data-model-private.h \
	gda-data-access-wrapper.h \
	gda-data-proxy.h \
	gda-data-select.h \
	gda-decl.h \
	gda-enums.h \
	gda-holder.h \
	gda-lockable.h \
	gda-log.h \
	gda-meta-store.h \
	gda-meta-struct.h \
	gda-provider.h \
	gda-provider-meta.h \
	gda-quark-list.h \
	gda-repetitive-statement.h \
	gda-row.h \
	gda-set.h \
	gda-server-operation.h \
	gda-server-provider.h \
	gda-server-provider-extra.h \
	gda-server-provider-private.h \
	gda-server-provider-impl.h \
	gda-statement.h \
	gda-statement-extra.h \
	gda-sql-builder.h \
	gda-transaction-status.h \
	gda-transaction-status-private.h \
	gda-tree.h \
	gda-tree-mgr-columns.h \
	gda-tree-mgr-schemas.h \
	gda-tree-mgr-tables.h \
	gda-tree-node.h \
	gda-tree-manager.h \
	gda-tree-mgr-label.h \
	gda-tree-mgr-select.h \
	gda-util.h \
	gda-value.h \
	gda-xa-transaction.h \
	libgda-global-variables.h \
	gda-data-pivot.h \
	gda-ddl-base.h \
	gda-ddl-fkey.h \
	gda-ddl-column.h \
	gda-ddl-table.h \
	gda-ddl-buildable.h \
	gda-ddl-view.h \
	gda-ddl-creator.h

gda_built_sources= \
	$(builddir)/libgda.h

gda_sources= \
	gda-batch.c \
	gda-blob-op.c \
	gda-blob-op-impl.h \
	gda-column.c \
	gda-config.c \
	gda-connection.c \
	gda-connection-event.c \
	gda-data-comparator.c \
	gda-data-handler.c \
	gda-data-model-array.c \
	$(GDA_BDB_S) \
	$(GDA_LDAP_S) \
	gda-data-model.c \
	gda-data-model-dir.c \
	gda-data-model-import.c \
	gda-data-model-iter.c \
	gda-data-access-wrapper.c \
	gda-data-proxy.c \
	gda-data-select.c \
	gda-holder.c \
	gda-init.c \
	gda-lockable.c \
	gda-log.c \
	gda-meta-store.c \
	gda-meta-struct.c \
	gda-meta-struct-io.c \
	gda-provider.c \
	gda-provider-meta.c \
	gda-quark-list.c \
	gda-repetitive-statement.c \
	gda-row.c \
	gda-set.c \
	gda-server-operation.c \
	gda-server-provider.c \
	gda-server-provider-extra.c \
	gda-statement.c \
	gda-sql-builder.c \
	gda-transaction-status.c \
	gda-tree.c \
	gda-tree-mgr-columns.c \
	gda-tree-mgr-schemas.c \
	gda-tree-mgr-tables.c \
	gda-tree-node.c \
	gda-tree-manager.c \
	gda-tree-mgr-label.c \
	gda-tree-mgr-select.c \
	gda-util.c \
	gda-value.c \
	gda-xa-transaction.c \
	gda-data-pivot.c \
	gda-ddl-base.c \
	gda-ddl-fkey.c \
	gda-ddl-column.c \
	gda-ddl-table.c \
	gda-ddl-buildable.c \
	gda-ddl-view.c \
	gda-ddl-creator.c

libgda_sources =  \
	csv.h \
	libcsv.c \
	dir-blob-op.h \
	dir-blob-op.c \
	gda-attributes-manager.c \
	$(gda_headers) \
	gda-debug-macros.h \
	gda-connection-internal.h \
	gda-connection-sqlite.h \
	gda-custom-marshal.c \
	gda-custom-marshal.h \
	gda-data-meta-wrapper.c \
	gda-data-meta-wrapper.h \
	gda-data-model-dsn-list.c \
	gda-data-model-dsn-list.h \
	gda-data-select-extra.h \
	gda-meta-store-extra.h \
	gda-meta-struct-private.h \
	gda-marshal.c \
	gda-enum-types.c \
	gda-server-operation-private.h \
	gda-statement-priv.h \
	$(gda_built_sources) \
	$(gda_sources)

gda_enum_header_files = gda-connection.h gda-enums.h

gda-enum-types.h: s-enum-types-h
	@true

s-enum-types-h: @REBUILD@ $(gda_enum_header_files) Makefile
	( cd $(srcdir) && $(GLIB_MKENUMS) \
	                --fhead "#ifndef __LIBGDA_ENUM_TYPES_H__\n#define __LIBGDA_ENUM_TYPES_H__\n\n#include <glib-object.h>\n\nG_BEGIN_DECLS\n" \
			--vhead "GType @enum_name@_get_type (void);\n#define GDA_TYPE_@ENUMSHORT@ (@enum_name@_get_type())\n" 	\
			--ftail "G_END_DECLS\n\n#endif /* __LIBGDA_ENUM_TYPES_H__ */" \
		$(gda_enum_header_files)) > tmp-gda-enum-types.h \
	&& (cmp -s tmp-gda-enum-types.h gda-enum-types.h || cp tmp-gda-enum-types.h gda-enum-types.h ) \
	&& rm -f tmp-gda-enum-types.h	\
	&& echo timestamp > $(@F)

gda-enum-types.c: s-enum-types-c
	@true

s-enum-types-c: @REBUILD@ $(gda_enum_header_files) Makefile
	( cd $(srcdir) && $(GLIB_MKENUMS) \
	                --fhead "#include <libgda/libgda.h>\n" \
	                --fhead "#include <glib-object.h>" \
			--vhead "GType\n@enum_name@_get_type (void)\n{\n  static GType etype = 0;\n  if (etype == 0) {\n    static const G@Type@Value values[] = {" 	\
			--vprod "      { @VALUENAME@, \"@VALUENAME@\", \"@valuenick@\" }," \
			--vtail "      { 0, NULL, NULL }\n    };\n    etype = g_@type@_register_static (\"@EnumName@\", values);\n  }\n  return etype;\n}\n" \
		$(gda_enum_header_files)) > tmp-gda-enum-types.c \
	&& (cmp -s tmp-gda-enum-types.c gda-enum-types.c || cp tmp-gda-enum-types.c gda-enum-types.c ) \
	&& rm -f tmp-gda-enum-types.c \
	&& echo timestamp > $(@F)


# Generate the enums source code, with glib-mkenums:
# This is based on the same Makefile.am stuff in pango:
libgda_built_headers = gda-marshal.h gda-enum-types.h

# Don't build the library until we have built the headers that it needs:
$(OBJECTS) $(libgda_6_0_la_OBJECTS): gda-marshal.c gda-marshal.h gda-enum-types.h gda-enum-types.c keywords_hash.code

libgda_6_0_la_SOURCES = \
	$(libgda_sources)

libgda_6_0_la_LDFLAGS = \
	-version-info $(GDA_CURRENT):$(GDA_REVISION):$(GDA_AGE) \
	-export-dynamic $(NO_UNDEFINED) $(LIBTOOL_EXPORT_OPTIONS) \
	$(GDA_DEBUG_LDFLAGS)

libgda_6_0_la_LIBADD = \
	sql-parser/libgda_sql_parser-6.0.la \
	providers-support/libgda-psupport.la \
	handlers/libgda_handlers-6.0.la \
	binreloc/libgda_binreloc-6.0.la \
	sqlite/libgda-sqlite.la \
	thread-wrapper/libgda_threadwrapper-6.0.la \
	$(COREDEPS_LIBS) \
	$(GIO_LIBS) $(LIBSECRET_LIBS) $(GNOME_KEYRING_LIBS)

if PLATFORM_WIN32
libgda_6_0_la_LDFLAGS += -export-symbols $(builddir)/libgda.def
libgda_6_0_la_DEPENDENCIES = libgda.def

libgda.def: libgda.symbols
	(echo -e EXPORTS; $(CPP) -P $(DEF_FLAGS) - <$(srcdir)/libgda.symbols | sed -e '/^$$/d' -e 's/^/ /' -e 's/G_GNUC_[^ ]*//g' | sort) > libgda.def.tmp && mv libgda.def.tmp libgda.def

libgda-$(GDA_ABI_VERSION).lib: libgda.def
	$(DLLTOOL) --dllname libgda-$(GDA_ABI_VERSION)-$(GDA_ABI_MAJOR_VERSION).dll --def libgda.def --output-lib libgda-$(GDA_ABI_VERSION).lib

install-data-local: install-def-files
uninstall-local: uninstall-def-files

install-def-files: libgda.def libgda-$(GDA_ABI_VERSION).lib
	$(INSTALL) $(builddir)/libgda.def $(DESTDIR)$(libdir)/libgda-$(GDA_ABI_VERSION).def
	$(INSTALL) $(builddir)/libgda-$(GDA_ABI_VERSION).lib $(DESTDIR)$(libdir)/

uninstall-def-files:
	-rm $(DESTDIR)$(libdir)/libgda-$(GDA_ABI_VERSION).def
	-rm $(DESTDIR)$(libdir)/libgda-$(GDA_ABI_VERSION).lib
endif

gdaincludedir=$(includedir)/libgda-$(GDA_ABI_MAJOR_VERSION).$(GDA_ABI_MINOR_VERSION)/libgda
gdainclude_HEADERS=$(libgda_built_headers) $(gda_headers) libgda.h

CLEANFILES = $(libgda_built_headers) \
	gda-marshal.c \
	gda-enum-types.h \
	s-enum-types-h \
	gda-enum-types.c \
	s-enum-types-c \
	libgda.def \
	libgda-$(GDA_ABI_VERSION).lib \
	mkkeywordhash$(EXEEXT_FOR_BUILD) keywords_hash.code

dist-hook:
	cd $(distdir); rm -f $(libgda_built_headers)

xmldir   = $(datadir)/libgda-6.0
xml_DATA = $(srcdir)/information_schema.xml

DTD_FILES = libgda-array.dtd \
	    libgda-paramlist.dtd  \
	    libgda-server-operation.dtd \
	    libgda-ddl-creator.dtd

dtddir=$(LIBGDA_DTDDIR)
dtd_DATA=$(DTD_FILES)
EXTRA_DIST = \
	$(DTD_FILES) \
	$(xml_DATA) \
	gda-marshal.list \
	libgda.symbols \
	keywords.list

DISTCLEANFILES  = .deps/*.P
if ENABLE_GDA_GI
-include $(INTROSPECTION_MAKEFILE)
INTROSPECTION_GIRS =
INTROSPECTION_SCANNER_ARGS = --add-include-path=$(srcdir) \
			     --namespace Gda \
			     --warn-all \
			     --c-include=libgda/libgda.h
INTROSPECTION_COMPILER_ARGS = --includedir=$(srcdir)

psupport = \
	providers-support/gda-pstmt.h \
	providers-support/gda-pstmt.c

threadwrapper = \
	thread-wrapper/gda-worker.h \
	thread-wrapper/gda-worker.c

sqlparser = \
	sql-parser/gda-sql-parser.h \
	sql-parser/gda-sql-parser.c \
	sql-parser/gda-statement-struct-decl.h \
	sql-parser/gda-statement-struct-parts.h \
	sql-parser/gda-statement-struct-compound.h

handlers = \
	handlers/gda-handler-bin.h \
	handlers/gda-handler-boolean.h \
	handlers/gda-handler-numerical.h \
	handlers/gda-handler-string.h \
	handlers/gda-handler-time.h \
	handlers/gda-handler-type.h \
	handlers/gda-handler-bin.c \
	handlers/gda-handler-boolean.c \
	handlers/gda-handler-numerical.c \
	handlers/gda-handler-string.c \
	handlers/gda-handler-time.c \
	handlers/gda-handler-type.c

introspection_sources = $(gda_sources) \
	$(gda_headers) \
	$(psupport) \
	$(threadwrapper) \
	$(sqlparser) \
	$(handlers)
Gda-6.0.gir: $(lib_LTLIBRARIES)
Gda-6.0.typelib: $(lib_LTLIBRARIES)
Gda_6_0_gir_INCLUDES = GObject-2.0 libxml2-2.0
Gda_6_0_gir_CFLAGS = $(GLOBAL_CFLAGS)

Gda_6_0_gir_LIBS = $(lib_LTLIBRARIES)
Gda_6_0_gir_FILES = $(addprefix $(srcdir)/,$(introspection_sources)) $(gda_built_sources)
INTROSPECTION_GIRS += Gda-6.0.gir

girdir = $(datadir)/gir-1.0
typelibsdir = $(libdir)/girepository-1.0

gir_DATA = $(INTROSPECTION_GIRS)
typelibs_DATA = $(INTROSPECTION_GIRS:.gir=.typelib)

CLEANFILES += $(typelibs_DATA)
endif

if ENABLE_VALA_BINDINGS

vapi: libgda-6.0.vapi


libgda-6.0.vapi: Gda-6.0.gir
	$(VAPIGEN) --metadatadir=$(top_srcdir)/libgda --library libgda-6.0 --pkg libxml-2.0 Gda-6.0.gir

vapidir = $(datadir)/vala/vapi
vapi_DATA=libgda-6.0.vapi libgda-6.0.deps

EXTRA_DIST += \
	Gda-6.0.metadata \
        $(vapi_DATA)
endif

clean-local:
	@if ! test -d "$(top_srcdir)/.git"; \
	then \
		rm -f $(gir_DATA) $(vapi_DATA); \
	fi


test_cnc_open_SOURCES = test-cnc-open.c
test_cnc_open_LDADD = \
	$(top_builddir)/libgda/libgda-6.0.la \
        $(COREDEPS_LIBS)

test_cnc_exec_SOURCES = test-cnc-exec.c
test_cnc_exec_CFLAGS = \
	-DROOT_DIR=\""$(top_srcdir)"\"
test_cnc_exec_LDADD = \
	$(top_builddir)/libgda/libgda-6.0.la \
        $(COREDEPS_LIBS)

test_cnc_meta_SOURCES = test-cnc-meta.c
test_cnc_meta_CFLAGS = \
	-DROOT_DIR=\""$(top_srcdir)"\"
test_cnc_meta_LDADD = \
	$(top_builddir)/libgda/libgda-6.0.la \
        $(COREDEPS_LIBS)
