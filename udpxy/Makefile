#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=udpxy
#PKG_REV:=1.0
#PKG_TAG:=21-2
#PKG_VERSION:=$(PKG_REV)-Chipmunk-$(PKG_TAG)
PKG_VERSION:=1.0-Chipmunk-BLD20
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME).$(PKG_VERSION).tgz
#PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_REV)-Chipmunk-$(PKG_TAG)
#PKG_SOURCE_URL:=@SF/udpxy
#PKG_SOURCE_URL:=http://sourceforge.net/projects/udpxy/files/udpxy/Chipmunk-1.0/
PKG_SOURCE_URL:=http://downloads.sourceforge.net/project/udpxy/udpxy/Chipmunk-1.0
# PKG_MD5SUM:=e1373a3bf30b2b3449a5b907aa4e29ce
#wget http://sourceforge.net/projects/udpxy/files/udpxy/Chipmunk-1.0/udpxy.1.0.21-2-prod.tgz
#wget http://downloads.sourceforge.net/project/udpxy/udpxy/Chipmunk-1.0/udpxy.1.0-21.1-prod.tgz
#http://citylan.dl.sourceforge.net/project/udpxy/udpxy/Chipmunk-1.0/udpxy.1.0-Chipmunk-BLD20.tgz
PKG_INSTALL:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-1.0-Chipmunk-20

include $(INCLUDE_DIR)/package.mk

define Package/udpxy
  SECTION:=net
  CATEGORY:=Network
  TITLE:=convert UDP IPTV streams into http stream
  URL:=http://sourceforge.net/projects/udpxy
endef

define Package/udpxy/description
	udproxy makes it possible to convert UDP IPTV streams into http
	streams which can be viewed even over wlans. http streams do
	not generate huge amounts of multicast traffic, so a sd stream
	only takes about 300k. interesting for peoply who have IPTV at
	home and do not want to rent multiple decoders from their
	provider but just use their own streaming client for example
	popcornhour/mediatomb/vlc/etc.
endef

MAKE_FLAGS += \
	INSTALLROOT="$(PKG_INSTALL_DIR)/usr"

define Package/udpxy/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/udpxy $(1)/usr/bin/
	$(INSTALL_BIN) ./files/udpxy.init $(1)/etc/init.d/udpxy
	$(INSTALL_CONF) ./files/udpxy.conf $(1)/etc/config/udpxy
	ln -sf udpxy $(1)/usr/bin/udpxrec
endef

define Package/udpxy/conffiles
/etc/config/udpxy
endef

$(eval $(call BuildPackage,udpxy))
