providerdir=$(libdir)/libgda-$(GDA_ABI_MAJOR_VERSION).$(GDA_ABI_MINOR_VERSION)/providers
provider_LTLIBRARIES = libgda-bdbsql.la

AM_CPPFLAGS = \
	-I$(top_srcdir) \
	-I$(top_srcdir)/libgda \
	-I$(top_srcdir)/libgda/sqlite \
	-I$(top_builddir) \
	$(COREDEPS_CFLAGS) \
	$(COREDEPS_WFLAGS) \
	$(BDBSQL_CFLAGS) -DWITH_BDBSQLITE \
	$(sqliteinc) 


libgda_bdbsql_la_SOURCES = \
	bdbsql.gresources.c \
	libmain.c

libgda_bdbsql_la_LDFLAGS = -export-dynamic -module -avoid-version $(NO_UNDEFINED) $(LIBTOOL_PROV_EXPORT_OPTIONS)
libgda_bdbsql_la_LIBADD = \
	$(top_builddir)/libgda/sqlite/libgda-bdbsqlite.la \
	$(top_builddir)/libgda/libgda-6.0.la \
	$(COREDEPS_LIBS)

xmldir   = $(datadir)/libgda-6.0
xml_in_files = \
	bdbsql_specs_dsn.xml.in \
	bdbsql_specs_create_db.xml.in \
	bdbsql_specs_drop_db.xml.in \
	bdbsql_specs_create_table.xml.in \
	bdbsql_specs_drop_table.xml.in \
	bdbsql_specs_create_index.xml.in \
	bdbsql_specs_drop_index.xml.in \
	bdbsql_specs_rename_table.xml.in \
	bdbsql_specs_add_column.xml.in \
	bdbsql_specs_create_view.xml.in \
	bdbsql_specs_drop_view.xml.in

@INTLTOOL_XML_RULE@

xml_DATA = $(xml_in_files:.xml.in=.xml)

# resources
RESOURCES=$(xml_in_files:.xml.in=.raw.xml)
bdbsql.gresources.c: bdbsql.gresource.xml $(RESOURCES)
	$(AM_V_GEN) $(GLIB_COMPILE_RESOURCES) --target=$@ --generate-source $(srcdir)/bdbsql.gresource.xml

%.raw.xml:%.xml.in
	@echo "  GEN      $@"
	@cat $< | sed -e 's/_\([a-zA-Z0-9]*\)=/\1=/g' -e 's/<_\([a-zA-Z0-9_]*\)>/<\1>/g' -e 's/<\/_\([a-zA-Z0-9_]*\)>/<\/\1>/g' -e 's/<!-- .* -->//'> $@

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = libgda-bdbsql-6.0.pc

EXTRA_DIST = $(xml_in_files) libgda-bdbsql-6.0.pc.in bdbsql.gresource.xml
DISTCLEANFILES = $(xml_DATA)

CLEANFILES = \
	bdbsql.gresources.c \
	$(RESOURCES)
