PORTNAME=	tokyopromenade
PORTVERSION=	0.9.25
PORTREVISION=	1
CATEGORIES=	www
MASTER_SITES=	https://dbmx.net/${PORTNAME}/pkg/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Content management system
WWW=		https://dbmx.net/tokyopromenade/

BUILD_DEPENDS=	tokyocabinet>=1.4.31:databases/tokyocabinet \
		fcgi-devkit>=0:www/fcgi
LIB_DEPENDS=	libtokyocabinet.so:databases/tokyocabinet
RUN_DEPENDS=	spawn-fcgi>=0:www/spawn-fcgi

OPTIONS_DEFINE=	LUA

CONFIGURE_ARGS=	--enable-fcgi
GNU_CONFIGURE=	yes
GNU_CONFIGURE_MANPREFIX=${PREFIX}/share
USES=		gmake localbase lua compiler

SUB_FILES=	pkg-message

LUA_CONFIGURE_ENABLE+=	lua
LUA_LDFLAGS+=	-L${LUA_LIBDIR}
LUA_CFLAGS+=	-I${LUA_INCDIR}

.include <bsd.port.pre.mk>

.if ${COMPILER_TYPE} == "clang"
CFLAGS+=		-Wno-incompatible-pointer-types-discards-qualifiers
.endif

post-patch:
	${REINPLACE_CMD} -e "s/llua/llua-${LUA_VER}/g" ${WRKSRC}/configure

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/prommgr
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/libexec/promenade.cgi
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/libexec/promenade.fcgi

.include <bsd.port.post.mk>
