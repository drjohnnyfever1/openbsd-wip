# $OpenBSD: Makefile,v 1.2 2017/10/28 13:38:38 abieber Exp $

COMMENT =	fast, efficient and secure backup program

GH_ACCOUNT =	restic
GH_PROJECT =	restic
GH_TAGNAME =	v0.8.2

CATEGORIES =	sysutils

MAINTAINER =	Aaron Bieber <abieber@openbsd.org>

HOMEPAGE =	https://restic.net/

# BSD
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += c pthread

MODULES =	lang/go
MODGO_TYPE =	bin

do-build:
	cd ${WRKSRC} && ${MODGO_CMD} run -x build.go

do-test:
	cd ${WRKSRC} && ${MODGO_CMD} test ./cmd/... ./internal/...

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/restic ${PREFIX}/bin
	${INSTALL_DATA_DIR} ${PREFIX}/man/man1
	${INSTALL_MAN} ${WRKSRC}/doc/man/*.1 ${PREFIX}/man/man1

.include <bsd.port.mk>
