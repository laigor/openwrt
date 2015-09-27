# 
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 12225 2008-08-06 22:10:29Z nbd $

include $(TOPDIR)/rules.mk

PKG_NAME:=gnugk
PKG_VERSION:=2.3.0
PKG_SOURCE:=gnugk-2.3.0-4.tar.gz
PKG_SOURCE_URL:=http://downloads.sourceforge.net/project/openh323gk/Sources/2.3.0
#PKG_MD5SUM:=5208f24d0328ee7c20b52c43eaa9aa0e
PKG_BUILD_DIR:=$(BUILD_DIR)/gnugk-2.3.0
PKG_BUILD_DEPENDS:=ptlib
PKG_CONFIG_DEPENDS:=ptlib

include $(INCLUDE_DIR)/package.mk

define Package/gnugk
  SECTION:=net
  CATEGORY:=Network
  TITLE:=gnugk
  URL:=http://www.gnugk.org
  DEPENDS:=+ptlib
endef

define Package/gnugk/description
gnugk
endef
#CFLAGS += -msoft-float
MAKE_FLAGS += optnoshared
TARGET_CFLAGS += -msoft-float
CONFIGURE_VARS +=PTLIBDIR=$(BUILD_DIR)/ptlib
CONFIGURE_VARS +=OPENH323DIR=$(BUILD_DIR)/h323plus

define Build/Configure
	$(call Build/Configure/Default)
endef

define Package/gnugk/install
	echo Installing
endef


$(eval $(call BuildPackage,gnugk))
