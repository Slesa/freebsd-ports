PORTNAME=	xfd
PORTVERSION=	1.1.4
PORTREVISION=	1
CATEGORIES=	x11

MAINTAINER=	x11@FreeBSD.org
COMMENT=	Display all characters in an X font

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libfreetype.so:print/freetype2
BUILD_DEPENDS=	fc-cache:x11-fonts/fontconfig
RUN_DEPENDS=	fc-cache:x11-fonts/fontconfig

EXTRACT_SUFX=	.tar.xz
USES=		xorg xorg-cat:app
USE_XORG=	x11 xft xkbfile xmu xrender xt xaw

GNU_CONFIGURE_MANPREFIX=	${PREFIX}/share

.include <bsd.port.mk>
