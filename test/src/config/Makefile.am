INCLUDES = -I $(top_srcdir)/include\
	-I $(top_srcdir)/extension/include\
	-I $(top_srcdir)/test/cppunit/include\
	-I $(top_srcdir)/test/src

test_srcdir = $(top_srcdir)/test/src/
config_test_srcdir = $(test_srcdir)/config

config_test_sources = \
	$(config_test_srcdir)/ConfiguratorTestCase.cpp\
	$(config_test_srcdir)/XMLConfiguratorTestCase.cpp

EXTRA_DIST = \
	$(config_test_srcdir)/ConfiguratorTestCase.h\
	$(config_test_srcdir)/XMLConfiguratorTestCase.h

check_PROGRAMS  = config_test

config_test_SOURCES = \
	$(config_test_sources)\
	$(test_srcdir)/main.cpp\
	$(test_srcdir)/TestHelper.cpp

config_test_LDADD= $(top_builddir)/extension/src/libfirtexext.la\
	$(top_builddir)/src/libfirtex.la\
	$(top_builddir)/test/cppunit/libcppunit.la\
	@FX_LIBEVENT_HOME@/libevent.la\
	@FX_LIBEVENT_HOME@/libevent_pthreads.la\
	 -lpthread -ldl

if HAVE_SNOWBALL
config_test_LDADD += $(top_builddir)/contrib/snowball/src/libfirtex_snowball.la
endif 

if HAVE_HIGHLIGHTER
config_test_LDADD += $(top_builddir)/contrib/highlighter/src/libfirtex_highlighter.la
endif 

config_test_LDFLAGS = $(LIBADD_DL)

if HAVE_TCMALLOC
config_test_LDADD += @FX_TCMALLOC_HOME@/libtcmalloc.la
endif

TESTS_ENVIRONMENT=LD_LIBRARY_PATH=/usr/local/lib:/usr/local/lib64 \
		HEAPCHECK=normal

TESTS = $(check_PROGRAMS)

