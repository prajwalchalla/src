# $NetBSD: Makefile,v 1.31 2018/12/23 13:35:02 maxv Exp $

.include <bsd.own.mk>

TESTS_SUBDIRS=	csu libbluetooth libc libcrypt libcurses libexecinfo \
		libm libnvmm libobjc libposix libppath libprop libpthread \
		librefuse librt libtre libusbhid libutil \
		semaphore

TESTS_SUBDIR_INSTALL_ONLY=	libevent

.if (${MKRUMP} != "no") && !defined(BSD_MK_COMPAT_FILE)
TESTS_SUBDIRS+= librumpclient librumphijack
.endif

TESTS_SUBDIRS+= libdes

.if ${MKKYUA} != "no"
# These tests come from external/bsd/lutok/tests/lib/liblutok.  Ensure they
# get registered in the Atffile only when installed.
ATFFILE_EXTRA_TPS=	liblutok
.endif

.if (${MKSKEY} != "no")
TESTS_SUBDIRS+= libskey
.endif

.if ${MKSLJIT} != "no"
TESTS_SUBDIRS+=	libsljit
TESTS_SUBDIRS+=	libbpfjit
.endif

TESTSDIR=	${TESTSBASE}/lib

.include <bsd.test.mk>
