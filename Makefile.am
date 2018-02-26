
if WANT_JANSSON
JANSSON_INCLUDES= -I$(top_srcdir)/compat/jansson
else
JANSSON_INCLUDES=
endif

EXTRA_DIST	= example-cfg.json nomacro.pl
SUBDIRS		= compat

dist_man_MANS	= minerd.1
bin_PROGRAMS	= minerd
minerd_SOURCES	= src/elist.h \
                  src/miner.h \
                  src/compat.h \
                  src/cpu-miner.c \
                  src/util.c \
                  src/sha2.c \
                  src/scrypt.c

if USE_ASM
if ARCH_x86
minerd_SOURCES += src/sha2-x86.S src/scrypt-x86.S
endif

if ARCH_x86_64
minerd_SOURCES += src/sha2-x64.S src/scrypt-x64.S
endif

if ARCH_ARM
minerd_SOURCES += src/sha2-arm.S src/scrypt-arm.S
endif

if ARCH_PPC
minerd_SOURCES += src/sha2-ppc.S src/scrypt-ppc.S
endif
endif

minerd_LDFLAGS	= $(PTHREAD_FLAGS)
minerd_LDADD	= @LIBCURL@ @JANSSON_LIBS@ @PTHREAD_LIBS@ @WS2_LIBS@
minerd_CFLAGS	= -fno-strict-aliasing
minerd_CPPFLAGS	= @LIBCURL_CPPFLAGS@ $(JANSSON_INCLUDES) $(PTHREAD_FLAGS)

