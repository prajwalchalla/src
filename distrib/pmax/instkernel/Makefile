#	$NetBSD: Makefile,v 1.41 2019/01/01 19:09:12 christos Exp $

.include <bsd.own.mk>
.include "${NETBSDSRCDIR}/distrib/common/Makefile.distrib"

.include <bsd.kernobj.mk>

.if ${MACHINE_ARCH} == "mips64el"
SFX=		64
.endif

IMAGE=		diskimage
IMAGESIZE=	2800k
LISTS=		${.CURDIR}/list${SFX}
MTREECONF=	${DISTRIBDIR}/common/mtree.dot
IMAGEENDIAN=	le
PRIMARYBOOT=	${DESTDIR}/usr/mdec/bootxx_ffs
IMAGEDEPENDS=	netbsd-INSTALL${SFX}.gz ${DESTDIR}/usr/mdec/boot.pmax ${PRIMARYBOOT}
IMAGEPOSTBUILD=	${TOOL_INSTALLBOOT} -v -m ${MACHINE} ${IMAGE} ${PRIMARYBOOT}

RAMDISKDIR!=	cd ${.CURDIR}/../ramdisk && ${PRINTOBJDIR}
RAMDISK=	${RAMDISKDIR}/ramdisk.fs

MDSETTARGETS=		RAMDISK${SFX} ${RAMDISK} netbsd-INSTALL${SFX}
MDSET_RELEASEDIR=	binary/kernel

.if ${MACHINE_ARCH} == "mipsel"
MDSET_SUFFIXES.netbsd-INSTALL${SFX}=	ecoff create-ecoff
create-ecoff=			${MIPS_ELF2ECOFF} ${.TARGET:R} ${.TARGET}
.endif

IMAGE_RELEASEDIR=	installation/diskimage

.include "${DISTRIBDIR}/common/Makefile.image"
.include "${DISTRIBDIR}/common/Makefile.mdset"

.include <bsd.prog.mk>
