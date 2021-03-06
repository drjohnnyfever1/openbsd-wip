# $OpenBSD$

COMMENT =		ncurses-based Tox client

CATEGORIES =		net

HOMEPAGE =		https://github.com/Jfreegman/toxic

# GPLv3+
PERMIT_PACKAGE_CDROM =	Yes

GH_ACCOUNT =		Jfreegman
GH_PROJECT =		toxic
GH_TAGNAME =		v0.8.1

WANTLIB += alut c config curses curl m ncursesw openal opus png pthread
WANTLIB += qrencode toxav toxcore toxdns toxencryptsave vpx z

LIB_DEPENDS =		audio/freealut \
			audio/openal \
			net/toxcore \
			devel/libconfig \
			net/curl \
			graphics/libqrencode

FLAVORS = python no_x11 notify
FLAVOR ?=

USE_GMAKE =		yes

.if ${FLAVOR:Mpython}
MAKE_ENV +=		PYTHON_ENABLE=1
RUN_DEPENDS +=		lang/python/3.6
.endif

.if ${FLAVOR:Mno_x11}
MAKE_ENV +=		DISABLE_X11=1
.else
WANTLIB += X11
.endif

.if ${FLAVOR:Mnotify}
WANTLIB += gdk_pixbuf-2.0 gio-2.0 glib-2.0 gobject-2.0 intl notify
LIB_DEPENDS +=		devel/libnotify
.else
MAKE_ENV +=		DISABLE_DESKTOP_NOTIFY=1
.endif

NO_TEST =		Yes

.include <bsd.port.mk>
