bin_PROGRAMS = xqproxy

AM_CFLAGS = $(libxdmcp_CFLAGS)
xqproxy_LDADD = $(libxdmcp_LIBS)

xqproxy_SOURCES =	\
        xdmcpclient.c \
        xdmcpclient.h \
        xqproxy.c

appman_PRE = \
        xqproxy.man

# App default files  (*.ad)

EXTRA_DIST = ChangeLog autogen.sh xqssh

appmandir = $(APP_MAN_DIR)

appman_DATA = $(appman_PRE:man=@APP_MAN_SUFFIX@)

EXTRA_DIST += $(appman_PRE)
CLEANFILES = $(appman_DATA)

SED = sed

# Strings to replace in man pages
XORGRELSTRING = @PACKAGE_STRING@
  XORGMANNAME = X Version 11

MAN_SUBSTS = \
	-e 's|__vendorversion__|"$(XORGRELSTRING)" "$(XORGMANNAME)"|' \
	-e 's|__xorgversion__|"$(XORGRELSTRING)" "$(XORGMANNAME)"|' \
	-e 's|__xservername__|Xorg|g' \
	-e 's|__xconfigfile__|xorg.conf|g' \
	-e 's|__projectroot__|$(prefix)|g' \
	-e 's|__apploaddir__|$(appdefaultdir)|' \
	-e 's|__appmansuffix__|$(APP_MAN_SUFFIX)|g' \
	-e 's|__libmansuffix__|$(LIB_MAN_SUFFIX)|g' \
	-e 's|__adminmansuffix__|$(ADMIN_MAN_SUFFIX)|g' \
	-e 's|__miscmansuffix__|$(MISC_MAN_SUFFIX)|g' \
	-e 's|__filemansuffix__|$(FILE_MAN_SUFFIX)|g'

SUFFIXES = .$(APP_MAN_SUFFIX) .man

.man.$(APP_MAN_SUFFIX):
	sed $(MAN_SUBSTS) < $< > $@
