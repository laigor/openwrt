#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nut
PKG_VERSION:=2.7.2
PKG_RELEASE:=1
#http://www.networkupstools.org/source/2.7/nut-2.7.2.tar.gz
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.networkupstools.org/source/2.7/
# PKG_MD5SUM:=edc8502193cfed4974d6a770da173755
PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/nut
#  SUBMENU:=Web Servers/Proxies
  SECTION:=Utilities
  CATEGORY:=Utilities
  TITLE:=Network UPS Tools (NUT)
  URL:=http://www.networkupstools.org
  DEPENDS:=+libstdcpp +libusb-compat +libpthread +libgd +libltdl +libnetsnmp +libavahi-client +libopenssl
endef

define Package/nut/conffiles
/etc/nut
endef

CONFIGURE_ARGS+= \
	--with-usb \
	--with-cgi \
	--with-cgipath=/www/cgi-bin/nut \
	--with-htmlpath=/www/nut \
	--with-user=root \
	--sysconfdir=/etc/nut \
	--with-avahi \
	--with-snmp \
	--with-group=root
#	--without-libltdl
#	--enable-filter \
#	--enable-transparent \
#	--disable-regexcheck 

#	LIBS="-lc"
#	CFLAGS="$$$$CFLAGS -nostdinc++" \
#	LDFLAGS="$$$$LDFLAGS -nodefaultlibs" \
#	LIBS="-lc -luClibc++ -ldl -lm"
# LIBS="-lm"
TARGET_LDFLAGS += -lm

define Package/nut/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/* $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
	$(INSTALL_DIR) $(1)/www
	$(CP) -r $(PKG_INSTALL_DIR)/www/* $(1)/www/
	$(INSTALL_DIR) $(1)/etc/nut
	for etcfile in `cd $(PKG_INSTALL_DIR)/etc/nut ;ls *.sample` ; do cp -v $(PKG_INSTALL_DIR)/etc/nut/$$$${etcfile} $(1)/etc/nut/$$$${etcfile/.sample/} ; done
#	$(CP) $(PKG_INSTALL_DIR)/etc/* $(1)/etc/
endef

$(eval $(call BuildPackage,nut))
