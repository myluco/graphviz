# $Id: Makefile.am,v 1.5 2007/03/12 22:48:20 erg Exp $ $Revision: 1.5 $
## Process this file with automake to produce Makefile.in

pdfdir = $(pkgdatadir)/doc/pdf

man = lneato.1
pdf = lneato.pdf

man_MANS = $(man)
pdf_DATA = $(pdf)
if WITH_WIN32
bin_PROGRAMS = lneato
else
bin_SCRIPTS = lneato
endif

AM_CFLAGS = -DLNEATO
if WITH_WIN32
lneato_SOURCES = ${top_srcdir}/cmd/dotty/mswin32/dotty.c
lneato_LDADD = -luser32 -lgdi32 -lwinspool -lcomdlg32 -ladvapi32 -lshell32
else
lneato: ${top_srcdir}/cmd/lneato/lneato.sh
	cp ${top_srcdir}/cmd/lneato/lneato.sh lneato
	chmod +x lneato
endif

.1.pdf:
	-groff -Tps -man $< | ps2pdf - - >$@

EXTRA_DIST = $(man) $(pdf) lneato.bsh lneato.ksh lneato.sh \
	Makefile.old mswin32 

DISTCLEANFILES = lneato $(pdf)
