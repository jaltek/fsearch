EXTRA_DIST = fsearch.glade \
	     shared.css \
	     gresource.xml \
	     popover.ui \
	     preferences.ui \
	     overlay.ui \
	     menus.ui

if DEBUG
AM_CFLAGS = $(FSEARCH_CFLAGS) $(GTK_CFLAGS) $(GLIB_CFLAGS) $(GIO_CFLAGS) $(PCRE_CFLAGS) -Wall -std=c11 -g -Ofast -DDEBUG=1
else
AM_CFLAGS = $(FSEARCH_CFLAGS) $(GTK_CFLAGS) $(GLIB_CFLAGS) $(GIO_CFLAGS) $(PCRE_CFLAGS) -Wall -std=c11 -Ofast
endif

bin_PROGRAMS = fsearch

fsearch_NOINST_H_FILES = fsearch.h \
			 array.h \
			 btree.h \
			 clipboard.h \
			 fsearch_config.h \
			 database.h \
			 database_search.h \
			 debug.h \
			 fsearch_thread_pool.h \
			 fsearch_window.h \
			 fsearch_window_actions.h \
			 iconstore.h \
			 list_model.h \
			 listview.h \
			 preferences_ui.h \
			 query.h \
			 string_utils.h \
			 ui_utils.h \
			 utf8.h \
			 u8_lc_map.h \
			 u8_uc_map.h \
			 utils.h

fsearch_SOURCES = main.c \
		  fsearch.c \
		  fsearch_window.c \
		  fsearch_window_actions.c \
		  clipboard.c \
		  fsearch_config.c \
		  database.c \
		  database_search.c \
		  iconstore.c \
		  list_model.c \
		  preferences_ui.c \
		  resources.c \
		  ui_utils.c \
		  fsearch_thread_pool.c \
		  array.c \
		  string_utils.c \
		  btree.c \
		  listview.c \
		  query.c \
		  utils.c \
		  utf8.c \
		  $(fsearch_NOINST_H_FILES)

BUILT_SOURCES=resources.c resources.h

CLEANFILES = $(BUILT_SOURCES)

fsearch_CPPFLAGS = -DLOCALEDIR=\"$(localedir)\"

resource_files=$(shell $(GLIB_COMPILE_RESOURCES) --sourcedir=$(srcdir) --generate-dependencies $(srcdir)/gresource.xml)

resources.h:
	$(AM_V_GEN) $(GLIB_COMPILE_RESOURCES) --target=$@ --sourcedir=$(srcdir) --generate-header $(srcdir)/gresource.xml

resources.c: gresource.xml $(resource_files) resources.h
	$(AM_V_GEN) $(GLIB_COMPILE_RESOURCES) --target=$@ --sourcedir=$(srcdir) --generate-source $(srcdir)/gresource.xml

fsearch_LDADD = $(FSEARCH_LIBS) $(GTK_LIBS) $(GLIB_LIBS) $(GIO_LIBS) $(PCRE_LIBS)

