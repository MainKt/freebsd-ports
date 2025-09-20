PORTNAME=	wutil
DISTVERSIONPREFIX=	v
DISTVERSION=	0.3.0
CATEGORIES=	sysutils

MAINTAINER=	saheed@FreeBSD.org
COMMENT=	CLI and TUI for WiFi Management
WWW=		https://github.com/MainKt/wutil

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS+=	libifconfig.so:net/libifconfig

MAKE_ARGS+=	CFLAGS="-I${LOCALBASE}/include" LDFLAGS="-L${LOCALBASE}/lib"

USE_GITHUB=	yes
GH_ACCOUNT=	MainKt

PLIST_FILES=	bin/wutil \
							bin/wutui \
							share/man/man8/wutil.8.gz \
							share/man/man8/wutui.8.gz

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/wutil ${STAGEDIR}${PREFIX}/bin
	${INSTALL_PROGRAM} ${WRKSRC}/wutui ${STAGEDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/wutil.8 ${STAGEDIR}${PREFIX}/share/man/man8
	${INSTALL_MAN} ${WRKSRC}/wutui.8 ${STAGEDIR}${PREFIX}/share/man/man8

.include <bsd.port.mk>
