# $Id: Makefile.am,v 1.15 2008/05/21 20:37:40 ellson Exp $ $Revision: 1.15 $
## Process this file with automake to produce Makefile.in

AM_CPPFLAGS = \
	-I$(top_srcdir) \
	-I$(top_srcdir)/lib/common \
	-I$(top_srcdir)/lib/pathplan \
	-I$(top_srcdir)/lib/gvc \
	-I$(top_srcdir)/lib/graph \
	-I$(top_srcdir)/lib/cdt \
	$(LIBGVC_CFLAGS)

noinst_LTLIBRARIES = libgvplugin_neato_layout_C.la

if WITH_WIN32
lib_LTLIBRARIES = libgvplugin_neato_layout.la
else
pkglib_LTLIBRARIES = libgvplugin_neato_layout.la
endif

libgvplugin_neato_layout_C_la_SOURCES = \
	gvplugin_neato_layout.c \
	gvlayout_neato_layout.c
libgvplugin_neato_layout_C_la_LIBADD = \
	$(top_builddir)/lib/neatogen/libneatogen_C.la \
	$(top_builddir)/lib/twopigen/libtwopigen_C.la \
	$(top_builddir)/lib/fdpgen/libfdpgen_C.la \
	$(top_builddir)/lib/circogen/libcircogen_C.la

libgvplugin_neato_layout_la_LDFLAGS = -version-info @GVPLUGIN_VERSION_INFO@
libgvplugin_neato_layout_la_SOURCES = $(libgvplugin_neato_layout_C_la_SOURCES)
libgvplugin_neato_layout_la_LIBADD = $(libgvplugin_neato_layout_C_la_LIBADD) \
	$(top_builddir)/lib/gvc/libgvc.la \
	$(top_builddir)/lib/graph/libgraph.la \
	$(top_builddir)/lib/cdt/libcdt.la \
	$(top_builddir)/lib/pathplan/libpathplan.la \
	$(GTS_LIBS) @IPSEPCOLA_LIBS@ @MATH_LIBS@
	
if WITH_SFDP
libgvplugin_neato_layout_C_la_LIBADD += $(top_builddir)/lib/sfdpgen/libsfdpgen_C.la
endif

if WITH_WIN32
libgvplugin_neato_layout_la_LDFLAGS += -no-undefined
libgvplugin_neato_layout_la_LIBADD += $(top_builddir)/lib/graph/libgraph.la $(top_builddir)/lib/cdt/libcdt.la
endif

if WITH_DARWIN9
libgvplugin_neato_layout_la_LDFLAGS += -Wl,-exported_symbol,_gvplugin_neato_layout_LTX_library -Wl,-exported_symbol,_neato_init_node -Wl,-exported_symbol,_init_nop -Wl,-exported_symbol,_user_pos
endif

EXTRA_DIST = Makefile.old
