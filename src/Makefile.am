AUTOMAKE_OPTIONS 	= gnu
SUBDIRS 		= share command data include

MAINTAINERCLEANFILES 	= Makefile.in 

noinst_HEADERS          = candidate_view.h \
                          composing_view.h \
                          decoding_info.h \
                          function_keys.h \
                          google_imengine_config_keys.h \
                          google_imengine.h \
                          google_intl.h \
                          google_keycode.h \
                          ime_state.h \
                          pinyin_decoder_service.h \
                          pinyin_ime.h \
                          pinyin_lookup_table.h \
                          pinyin_util.h 

moduledir = @SCIM_MODULEDIR@/IMEngine
module_LTLIBRARIES = googlepinyin.la

googlepinyin_la_SOURCES = decoding_info.cpp \
                          pinyin_decoder_service.cpp \
                          pinyin_ime.cpp \
                          pinyin_lookup_table.cpp \
                          pinyin_util.cpp \
                          candidate_view.cpp \
                          composing_view.cpp \
                          function_keys.cpp \
                          google_imengine.cpp


googlepinyin_la_CXXFLAGS = -I$(includedir) -I$(top_builddir) -I./include \
                           @SCIM_CFLAGS@ \
                           -DSCIM_ICONDIR=\"@SCIM_ICONDIR@\" \
                           -DSCIM_GOOGLEPINYIN_LOCALEDIR=\"$(datadir)/locale\" \
                           -DSCIM_GOOGLEPINYIN_DATADIR=\"@SCIM_GOOGLEPINYIN_DATADIR@\" \
                           -DSCIM_GOOGLEPINYIN_ICON_FILE=\"@SCIM_ICONDIR@/google-pinyin_icon.png\" \
                           -DENABLE_DEBUG \
                           -Wall

googlepinyin_la_LDFLAGS = -avoid-version \
                          -module \
                          @SCIM_LIBS@

googlepinyin_la_LIBADD = ./share/libpinyinime.la

#
# setup UI
#
setupmoduledir           = @SCIM_MODULEDIR@/SetupUI
setupmodule_LTLIBRARIES  = googlepinyin-imengine-setup.la

googlepinyin_imengine_setup_la_SOURCES = google_imengine_setup.cpp

googlepinyin_imengine_setup_la_CXXFLAGS = \
                                       @SCIM_GTKUTILS_CFLAGS@ \
                                       @SCIM_CFLAGS@ \
			  	       -DSCIM_GOOGLEPINYIN_LOCALEDIR=\"$(datadir)/locale\" \
			  	       -Wall

googlepinyin_imengine_setup_la_LDFLAGS = \
                                      -avoid-version \
                                      -rpath $(setupmoduledir) \
                                      -module \
                                      $(LIBTOOL_EXPORT_OPTIONS) \
                                      @SCIM_GTKUTILS_LIBS@ \
                                      @LTLIBINTL@ \
                                      @SCIM_LIBS@
