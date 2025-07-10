PORTNAME=	wutil
DISTVERSIONPREFIX=	v
DISTVERSION=	0.1.0
CATEGORIES=	sysutils

MAINTAINER=	muhammad.saheed.iam@gmail.com
COMMENT=	CLI and TUI  for WiFi Management
WWW=		https://github.com/MainKt/wutil

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS+=	libifconfig.so:net/libifconfig
LIB_DEPENDS+=	libwpa_client.so:security/wpa_supplicant

MAKE_ARGS+=	CFLAGS="-I${LOCALBASE}/include" LDFLAGS="-L${LOCALBASE}/lib"

USE_GITHUB=	yes
GH_ACCOUNT=	MainKt

PLIST_FILES=	bin/wutil \
			bin/wutui \
			share/man/man1/wutil.1.gz

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/wutil ${STAGEDIR}${PREFIX}/bin
	${INSTALL_PROGRAM} ${WRKSRC}/wutui ${STAGEDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/wutil.1.gz ${STAGEDIR}${PREFIX}/share/man/man1

.include <bsd.port.mk>
