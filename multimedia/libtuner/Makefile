# Created by: Jason Harmening <jason.harmening@gmail.com>
# $FreeBSD$

PORTNAME=	libtuner
PORTVERSION=	1.1.4
CATEGORIES=	multimedia
MASTER_SITES=	ftp://corona.homeunix.net/ports/libtuner/

MAINTAINER=	jason.harmening@gmail.com
COMMENT=	Userspace drivers for various TV/radio tuner ICs

LICENSE=	BSD2CLAUSE MIT
LICENSE_COMB=	multi

MAKE_ARGS+=	INSTALLDIR=${STAGEDIR}${PREFIX}
MAKE_ARGS+=	-D LIBTUNER_ENABLE_IIC
USE_LDCONFIG=	${PREFIX}/lib/libtuner

.include <bsd.port.mk>
