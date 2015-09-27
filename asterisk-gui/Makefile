#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=asterisk-gui
PKG_BRANCH:=2.0
PKG_SOURCE_URL:=http://svn.digium.com/svn/asterisk-gui/branches/$(PKG_BRANCH)
PKG_REV:=5218
PKG_VERSION:=$(PKG_REV)
PKG_RELEASE:=1
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_SOURCE_PROTO:=svn
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_BUILD_PARALLEL:=1

#PKG_MD5SUM:=bc2a1168603815c23f204927d1e73239

#PKG_BUILD_DIR=$(BUILD_DIR)/asterisk-gui-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/asterisk-gui/Default
  SUBMENU:=Telephony
  SECTION:=net
  CATEGORY:=Network
  URL:=http://www.asterisk.org/
  MAINTAINER:=Hans Zandbelt <hans.zandbelt@gmail.com>
endef

define Package/asterisk-gui/Default/description
 Asterisk is a complete PBX in software. It provides all of the features
 you would expect from a PBX and more. Asterisk does voice over IP in three
 protocols, and can interoperate with almost all standards-based telephony
 equipment using relatively inexpensive hardware.
endef


define Package/asterisk-gui
$(call Package/asterisk-gui/Default)
  TITLE:=Complete open source PBX, v1.8x
  MENU:=1
  DEPENDS:= +asterisk18
endef

define Package/asterisk-gui/description
$(call Package/asterisk-gui/Default/description)
endef


CONFIGURE_ARGS+= --localstatedir="/usr"

define Build/Configure
	$(call Build/Configure/Default)
endef


define Build/Compile
	$(call Build/Compile/Default)
endef


define Package/asterisk-gui/install
	$(call Build/Compile/Default,DESTDIR="$(PKG_INSTALL_DIR)" install)
	$(INSTALL_DIR) $(1)/etc/asterisk
#	$(INSTALL_DIR) $(1)/usr/lib/asterisk/scripts
	$(INSTALL_DIR) $(1)/usr/lib/asterisk/static-http
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/asterisk/* $(1)/usr/lib/asterisk/
endef


$(eval $(call BuildPackage,asterisk-gui))
