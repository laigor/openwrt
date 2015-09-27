#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 15463 2009-04-28 00:00:51Z nico $

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/package.mk

PKG_NAME:=accel-pptp
PKG_VERSION:=0.8.3
PKG_RELEASE:=1.1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/$(PKG_NAME)


define Package/accel-pptp-kernel-module
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=
  TITLE:=accel-pptp-kernel-module
  URL:=http://$(PKG_NAME).sourceforge.net/
endef

define Package/accel-pptp-client
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=
  TITLE:=accel-pptp-client
  URL:=http://$(PKG_NAME).sourceforge.net/
endef

define Package/accel-pptp-kernel-pppd-module
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=
  TITLE:=accel-pptp-kernel-pppd-module
  URL:=http://$(PKG_NAME).sourceforge.net/
endef


# uses GNU configure

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) client
endef

define Package/accel-pptp/install
endef

$(eval $(call BuildPackage,accel-pptp))
