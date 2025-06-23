PORTNAME=	libifconfig
PORTVERSION=	0.1
CATEGORIES=	net
MASTER_SITES=	https://github.com/MainKt/freebsd-ports/releases/download/libifconfig-${_LIBIFCONFIG_HASH}/

MAINTAINER=	saheed@FreeBSD.org
COMMENT=	Library providing the functionality of ifconfig(8)
WWW=		https://cgit.freebsd.org/src/tree/lib/libifconfig

LICENSE=	BSD3CLAUSE

USE_LDCONFIG=	yes

MAKE_ARGS=	PREFIX=${PREFIX}

WRKSRC=		${WRKDIR}/libifconfig

CFLAGS+=	-Wno-pointer-sign

_LIBIFCONFIG_HASH=	b670c9bafc0e
_LIBIFCONFIG_REV=	0

.include <bsd.port.pre.mk>

.if ${OSREL} == "15.0"
DISTFILES=	libifconfig-${_LIBIFCONFIG_HASH}.tar.gz
.else
DISTFILES=	libifconfig-${OSREL}_${_LIBIFCONFIG_REV}.tar.gz
.endif

do-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/lib
	@${MKDIR} ${STAGEDIR}${PREFIX}/include
	${INSTALL_LIB} ${WRKSRC}/libifconfig.so.2 ${STAGEDIR}${PREFIX}/lib
	${LN} -s libifconfig.so.2 ${STAGEDIR}${PREFIX}/lib/libifconfig.so
.for h in libifconfig.h libifconfig_sfp.h libifconfig_sfp_tables.h
	${INSTALL_DATA} ${WRKSRC}/${h} ${STAGEDIR}${PREFIX}/include
.endfor

_ALL_VERSIONS=	13.3 13.4 13.5 14.0 14.1 14.2 14.3
.if make(makesum)
DISTFILES=
.for version in ${_ALL_VERSIONS}
DISTFILES+=	libifconfig-${version}_${_LIBIFCONFIG_REV}.tar.gz
.endfor
DISTFILES+=	libifconfig-${_LIBIFCONFIG_HASH}.tar.gz
.endif

.if defined(MAINTAINER_MODE)
upload:
	for version in ${_ALL_VERSIONS}; \
	do \
		cd /usr/src/lib && \
		git archive --format=tar.gz \
		    --output=libifconfig-$${version}_${_LIBIFCONFIG_REV}.tar.gz \
		    libifconfig/$${version} libifconfig ; \
	done
	cd /usr/src/lib && \
	git archive --format=tar.gz \
	    --output=libifconfig-${_LIBIFCONFIG_HASH}.tar.gz \
	    ${_LIBIFCONFIG_HASH} libifconfig ;
.endif

.include <bsd.port.post.mk>
