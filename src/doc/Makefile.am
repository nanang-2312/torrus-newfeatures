
#  Copyright (C) 2002  Stanislav Sinyagin
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program; if not, write to the Free Software
#  Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307, USA.

# Stanislav Sinyagin <ssinyagin@k-open.com>
#

SUBDIRS = . manpages

SUBST = @abs_top_builddir@/setup_tools/substvars.sh

CLEANFILES = $(POD_FILES) $(nodist_pkgdoc_DATA)
EXTRA_DIST = $(SRCPOD)

SRCPOD = \
		install.pod.in \
		nodeid_usage.pod.in \
		reporting_setup.pod.in \
		rpnexpr.pod.in \
		scalability.pod.in \
		snmpdiscovery.pod.in \
		stylingprofile.pod.in \
		userguide.pod.in \
		vendorsupport.pod.in \
		webintf.pod.in \
		xmlconfig.pod.in

POD_FILES = \
		install.pod \
		nodeid_usage.pod \
		reporting_setup.pod \
		rpnexpr.pod \
		scalability.pod \
		snmpdiscovery.pod \
		stylingprofile.pod \
		userguide.pod \
		vendorsupport.pod \
		webintf.pod \
		xmlconfig.pod


pkgdocdir  = @pkgdocdir@

if POD2TEXT_PRESENT
nodist_pkgdoc_DATA = \
		install.txt \
		nodeid_usage.txt \
		reporting_setup.txt \
		rpnexpr.txt \
		scalability.txt \
		snmpdiscovery.txt \
		stylingprofile.txt \
		userguide.txt \
		vendorsupport.txt \
		webintf.txt \
		xmlconfig.txt
endif

devdocdir  = $(pkgdocdir)/devdoc

dist_devdoc_DATA = \
		devdoc/architecture.pod \
		devdoc/devdiscover.pod \
		devdoc/progstyle.pod

SUFFIXES = .pod.in .pod .txt

.PRECIOUS: $(POD_FILES)

.pod.in.pod:
	$(SUBST) $<  > $@

if POD2TEXT_PRESENT
.pod.txt:
	$(POD2TEXT) $< > $@ 
endif

htdocs: $(POD_FILES)
	cd manpages; make pods
	HTMLDIR=@abs_top_builddir@/../htdocs $(SHELL) mkhtdocs.sh

