# Makefile for program source directory in GNU NLS utilities package.
# Copyright (C) 1995, 1996, 1997 by Ulrich Drepper <drepper@gnu.ai.mit.edu>
#
# This file file be copied and used freely without restrictions.  It can
# be used in projects which are not available under the GNU Public License
# but which still want to provide support for the GNU gettext functionality.
# Please note that the actual code is *not* freely available.
#
# - Modified by Owen Taylor <otaylor@redhat.com> to use GETTEXT_PACKAGE
#   instead of PACKAGE and to look for po2tbl in ./ not in intl/
#
# - Modified by jacob berkman <jacob@ximian.com> to install
#   Makefile.in.in and po2tbl.sed.in for use with glib-gettextize

GETTEXT_PACKAGE = scim
PACKAGE = scim
VERSION = 1.4.7

SHELL = /bin/sh


srcdir = .
top_srcdir = ..
top_builddir = ..


prefix = /usr
exec_prefix = ${prefix}
datadir = ${prefix}/share
libdir = ${exec_prefix}/lib
localedir = $(libdir)/locale
gnulocaledir = $(datadir)/locale
gettextsrcdir = $(datadir)/glib-2.0/gettext/po
subdir = po
install_sh = /home/cambell/scim-1.4.7/scim-1.4.7/install-sh
mkdir_p = mkdir -p -- .
mkinstalldirs = $(SHELL) $(top_srcdir)/mkinstalldirs

INSTALL = /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644

CC = gcc
GENCAT = gencat
GMSGFMT = /usr/bin/msgfmt
MSGFMT = /usr/bin/msgfmt
XGETTEXT = /usr/bin/xgettext
INTLTOOL_UPDATE = $(top_builddir)/intltool-update
INTLTOOL_EXTRACT = $(top_builddir)/intltool-extract
MSGMERGE = INTLTOOL_EXTRACT=$(INTLTOOL_EXTRACT) srcdir=$(srcdir) $(INTLTOOL_UPDATE) --gettext-package $(GETTEXT_PACKAGE) --dist
GENPOT   = INTLTOOL_EXTRACT=$(INTLTOOL_EXTRACT) srcdir=$(srcdir) $(INTLTOOL_UPDATE) --gettext-package $(GETTEXT_PACKAGE) --pot

DEFS = -DHAVE_CONFIG_H
CFLAGS =  -g
CPPFLAGS = 

INCLUDES = -I.. -I$(top_srcdir)/intl

COMPILE = $(CC) -c $(DEFS) $(INCLUDES) $(CPPFLAGS) $(CFLAGS) $(XCFLAGS)

SOURCES = 
POFILES =  zh_CN.po zh_TW.po ja.po ko.po de.po fr.po it.po cs.po pa.po fi.po sv.po nl.po
GMOFILES =  zh_CN.gmo zh_TW.gmo ja.gmo ko.gmo de.gmo fr.gmo it.gmo cs.gmo pa.gmo fi.gmo sv.gmo nl.gmo
DISTFILES = $(srcdir)/ChangeLog $(srcdir)/Makefile.in.in $(srcdir)/POTFILES.in \
$(POFILES) $(GMOFILES) $(SOURCES)

POTFILES = \
     ../src/scim_backend.cpp \
     ../src/scim_chartraits.cpp \
     ../src/scim_compose_key.cpp \
     ../src/scim_config_agent.cpp \
     ../src/scim_config_base.cpp \
     ../src/scim_config_module.cpp \
     ../src/scim_connection.cpp \
     ../src/scim.cpp \
     ../src/scim_debug.cpp \
     ../src/scim_event.cpp \
     ../src/scim_filter.cpp \
     ../src/scim_filter_manager.cpp \
     ../src/scim_filter_module.cpp \
     ../src/scim_frontend.cpp \
     ../src/scim_frontend_module.cpp \
     ../src/scim_global_config.cpp \
     ../src/scim_helper.cpp \
     ../src/scim_helper_launcher.cpp \
     ../src/scim_helper_manager.cpp \
     ../src/scim_helper_manager_server.cpp \
     ../src/scim_helper_module.cpp \
     ../src/scim_hotkey.cpp \
     ../src/scim_iconv.cpp \
     ../src/scim_imengine.cpp \
     ../src/scim_imengine_module.cpp \
     ../src/scim_launcher.cpp \
     ../src/scim_lookup_table.cpp \
     ../src/scim_module.cpp \
     ../src/scim_object.cpp \
     ../src/scim_panel_agent.cpp \
     ../src/scim_panel_client.cpp \
     ../src/scim_private.cpp \
     ../src/scim_signals.cpp \
     ../src/scim_slot.cpp \
     ../src/scim_socket.cpp \
     ../src/scim_transaction.cpp \
     ../src/scim_utility.cpp \
     ../src/scim_keyboard_layout_data.h \
     ../src/scim_keyevent_data.h \
     ../modules/Config/scim_simple_config.cpp \
     ../modules/Config/scim_socket_config.cpp \
     ../modules/Filter/scim_sctc_filter.cpp \
     ../modules/FrontEnd/scim_socket_frontend.cpp \
     ../modules/FrontEnd/scim_x11_frontend.cpp \
     ../modules/FrontEnd/scim_x11_ic.cpp \
     ../modules/IMEngine/scim_rawcode_imengine.cpp \
     ../modules/IMEngine/scim_socket_imengine.cpp \
     ../modules/SetupUI/scim_frontend_setup.cpp \
     ../modules/SetupUI/scim_imengine_setup.cpp \
     ../modules/SetupUI/scim_panel_gtk_setup.cpp \
     ../extras/gtk2_immodule/gtkimcontextscim.cpp \
     ../extras/gtk2_immodule/imscim.cpp \
     ../extras/setup/scim_setup_ui.cpp \
     ../extras/setup/scim_setup_helper.cpp \
     ../extras/setup/scim_setup_module.cpp \
     ../extras/setup/scim-setup.desktop.in \
     ../extras/panel/scim_panel_gtk.cpp \
     ../utils/scimstringview.c \
     ../utils/scimkeyselection.cpp \
     ../utils/scimtrayicon.c \
     ../utils/scim_x11_utils.cpp

CATALOGS =  zh_CN.gmo zh_TW.gmo ja.gmo ko.gmo de.gmo fr.gmo it.gmo cs.gmo pa.gmo fi.gmo sv.gmo nl.gmo
CATOBJEXT = .gmo
INSTOBJEXT = .mo

.SUFFIXES:
.SUFFIXES: .c .o .po .pox .gmo .mo .msg .cat

.c.o:
	$(COMPILE) $<

.po.pox:
	$(MAKE) $(GETTEXT_PACKAGE).pot
	$(MSGMERGE) $< $(top_builddir)/po/$(GETTEXT_PACKAGE).pot -o $*pox

.po.mo:
	$(MSGFMT) -o $@ $<

.po.gmo:
	file=`echo $* | sed 's,.*/,,'`.gmo \
	  && rm -f $$file && $(GMSGFMT) -o $$file $<

.po.cat:
	sed -f ../intl/po2msg.sed < $< > $*.msg \
	  && rm -f $@ && $(GENCAT) $@ $*.msg


all: all-yes

all-yes: $(CATALOGS)
all-no:

$(GETTEXT_PACKAGE).pot: $(POTFILES)
	$(GENPOT)

install: install-exec install-data
install-exec:
install-data: install-data-yes
install-data-no: all
install-data-yes: all
	if test -n "$(MKINSTALLDIRS)"; then \
	  $(MKINSTALLDIRS) $(DESTDIR)$(datadir); \
	else \
	  $(SHELL) $(top_srcdir)/mkinstalldirs $(DESTDIR)$(datadir); \
	fi
	@catalogs='$(CATALOGS)'; \
	for cat in $$catalogs; do \
	  cat=`basename $$cat`; \
	  case "$$cat" in \
	    *.gmo) destdir=$(gnulocaledir);; \
	    *)     destdir=$(localedir);; \
	  esac; \
	  lang=`echo $$cat | sed 's/\$(CATOBJEXT)$$//'`; \
	  dir=$(DESTDIR)$$destdir/$$lang/LC_MESSAGES; \
	  if test -n "$(MKINSTALLDIRS)"; then \
	    $(MKINSTALLDIRS) $$dir; \
	  else \
	    $(SHELL) $(top_srcdir)/mkinstalldirs $$dir; \
	  fi; \
	  if test -r $$cat; then \
	    $(INSTALL_DATA) $$cat $$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT); \
	    echo "installing $$cat as $$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT)"; \
	  else \
	    $(INSTALL_DATA) $(srcdir)/$$cat $$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT); \
	    echo "installing $(srcdir)/$$cat as" \
		 "$$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT)"; \
	  fi; \
	  if test -r $$cat.m; then \
	    $(INSTALL_DATA) $$cat.m $$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT).m; \
	    echo "installing $$cat.m as $$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT).m"; \
	  else \
	    if test -r $(srcdir)/$$cat.m ; then \
	      $(INSTALL_DATA) $(srcdir)/$$cat.m \
		$$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT).m; \
	      echo "installing $(srcdir)/$$cat as" \
		   "$$dir/$(GETTEXT_PACKAGE)$(INSTOBJEXT).m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
	if test "$(PACKAGE)" = "glib"; then \
	  if test -n "$(MKINSTALLDIRS)"; then \
	    $(MKINSTALLDIRS) $(DESTDIR)$(gettextsrcdir); \
	  else \
	    $(SHELL) $(top_srcdir)/mkinstalldirs $(DESTDIR)$(gettextsrcdir); \
	  fi; \
	  $(INSTALL_DATA) $(srcdir)/Makefile.in.in \
			  $(DESTDIR)$(gettextsrcdir)/Makefile.in.in; \
	else \
	  : ; \
	fi

# Define this as empty until I found a useful application.
installcheck:

uninstall:
	catalogs='$(CATALOGS)'; \
	for cat in $$catalogs; do \
	  cat=`basename $$cat`; \
	  lang=`echo $$cat | sed 's/\$(CATOBJEXT)$$//'`; \
	  rm -f $(DESTDIR)$(localedir)/$$lang/LC_MESSAGES/$(GETTEXT_PACKAGE)$(INSTOBJEXT); \
	  rm -f $(DESTDIR)$(localedir)/$$lang/LC_MESSAGES/$(GETTEXT_PACKAGE)$(INSTOBJEXT).m; \
	  rm -f $(DESTDIR)$(gnulocaledir)/$$lang/LC_MESSAGES/$(GETTEXT_PACKAGE)$(INSTOBJEXT); \
	  rm -f $(DESTDIR)$(gnulocaledir)/$$lang/LC_MESSAGES/$(GETTEXT_PACKAGE)$(INSTOBJEXT).m; \
	done
	if test "$(PACKAGE)" = "glib"; then \
	  rm -f $(DESTDIR)$(gettextsrcdir)/Makefile.in.in; \
	fi

check: all

dvi info tags TAGS ID:

mostlyclean:
	rm -f core core.* *.pox $(GETTEXT_PACKAGE).pot *.old.po cat-id-tbl.tmp
	rm -fr *.o
	rm -f .intltool-merge-cache

clean: mostlyclean

distclean: clean
	rm -f Makefile Makefile.in POTFILES *.mo *.msg *.cat *.cat.m

maintainer-clean: distclean
	@echo "This command is intended for maintainers to use;"
	@echo "it deletes files that may require special tools to rebuild."
	rm -f $(GMOFILES)

distdir = ../$(GETTEXT_PACKAGE)-$(VERSION)/$(subdir)
dist distdir: $(DISTFILES) $(GETTEXT_PACKAGE).pot
	dists="$(DISTFILES)"; \
	for file in $$dists; do \
	  ln $$file $(distdir) 2> /dev/null \
	    || cp -p $$file $(distdir); \
	done

update-po: Makefile
	$(MAKE) $(GETTEXT_PACKAGE).pot
	tmpdir=`pwd`; \
	catalogs='$(CATALOGS)'; \
	for cat in $$catalogs; do \
	  cat=`basename $$cat`; \
	  lang=`echo $$cat | sed 's/\$(CATOBJEXT)$$//'`; \
	  echo "$$lang:"; \
	  result="`$(MSGMERGE) -o $$tmpdir/$$lang.new.po $$lang`"; \
	  if $$result; then \
	    if cmp $(srcdir)/$$lang.po $$tmpdir/$$lang.new.po >/dev/null 2>&1; then \
	      rm -f $$tmpdir/$$lang.new.po; \
            else \
	      if mv -f $$tmpdir/$$lang.new.po $$lang.po; then \
	        :; \
	      else \
	        echo "msgmerge for $$lang.po failed: cannot move $$tmpdir/$$lang.new.po to $$lang.po" 1>&2; \
	        rm -f $$tmpdir/$$lang.new.po; \
	        exit 1; \
	      fi; \
	    fi; \
	  else \
	    echo "msgmerge for $$cat failed!"; \
	    rm -f $$tmpdir/$$lang.new.po; \
	  fi; \
	done

# POTFILES is created from POTFILES.in by stripping comments, empty lines
# and Intltool tags (enclosed in square brackets), and appending a full
# relative path to them
POTFILES: POTFILES.in
	( if test 'x$(srcdir)' != 'x.'; then \
	    posrcprefix='$(top_srcdir)/'; \
	  else \
	    posrcprefix="../"; \
	  fi; \
	  rm -f $@-t $@ \
	    && (sed -e '/^#/d' 						\
		    -e "s/^\[.*\] +//" 					\
		    -e '/^[ 	]*$$/d' 				\
		    -e "s@.*@	$$posrcprefix& \\\\@" < $(srcdir)/$@.in	\
		| sed -e '$$s/\\$$//') > $@-t \
	    && chmod a-w $@-t \
	    && mv $@-t $@ )

Makefile: Makefile.in.in ../config.status POTFILES
	cd .. \
	  && CONFIG_FILES=$(subdir)/$@.in CONFIG_HEADERS= \
	       $(SHELL) ./config.status

# Tell versions [3.59,3.63) of GNU make not to export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
