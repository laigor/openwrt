#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pshare
PKG_REV:=213
PKG_VERSION:=$(PKG_REV)
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=svn
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=pshare-$(PKG_VERSION)
PKG_SOURCE_URL:=http://tsdemuxer.googlecode.com/svn/trunk/pshare
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz


include $(INCLUDE_DIR)/package.mk


TARGET_CFLAGS += -fno-exceptions -fno-rtti -DWITH_URANDOM

define Build/Compile
	(cd $(PKG_BUILD_DIR); $(TARGET_CC) $(TARGET_CFLAGS) $(TARGET_CPPFLAGS) $(TARGET_LDFLAGS) -o pshare main.cpp upnp.cpp soap.cpp tmpl.cpp mem.cpp proxy.cpp common.cpp)
endef

define Package/pshare
  SECTION:=multimedia
  CATEGORY:=Multimedia
  DEPENDS:=+liblua
  TITLE:=Playlists sharing over UPnP/DLNA
  URL:=http://ps3muxer.org/pshare.html
endef

define Package/pshare/conffiles
/usr/share/pshare/pshare.lua
endef

define Package/pshare/description
This program is a light DLNA Media Server which provides ContentDirectory:1 service
for sharing IPTV unicast streams over local area network (with 'udpxy' for multicast to HTTP unicast conversion).
The program shares UTF8-encoded M3U playlists with links over local area network as content of the directory.
You can watch HDTV broadcasts (multicast or unicast) and listen Internet Radio in IP network without transcoding.
endef

define Package/pshare/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/pshare $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/pshare.init $(1)/etc/init.d/pshare
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/pshare.conf $(1)/etc/config/pshare
	$(INSTALL_DIR) $(1)/usr/share/pshare
	$(INSTALL_DIR) $(1)/usr/share/pshare/www
	$(CP) $(PKG_BUILD_DIR)/www/* $(1)/usr/share/pshare/www
	$(INSTALL_DIR) $(1)/usr/share/pshare/playlists
endef

define Package/pshare/conffiles
/etc/config/pshare
endef

$(eval $(call BuildPackage,pshare))
