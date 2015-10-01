# 
# Copyright (C) 2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile $


include $(TOPDIR)/rules.mk

PKG_NAME:=cdctl

PKG_RELEASE:=1
PKG_VERSION=0.16
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
# PKG_SOURCE:=$(PKG_NAME)-0.16.tar.gz
PKG_SOURCE_URL:=http://sourceforge.net/projects/cdctl/files/
TARGET_CFLAGS += -I$(STAGING_DIR)/usr/lib/libintl-stub/include
# http://sourceforge.net/projects/cdctl/files/cdctl-0.16.tar.gz

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/cdctl/Default
	CATEGORY:=Utilities
	SECTION:=utils
	SUBMENU:=disc
endef

define Package/cdctl/Default/description
	Cdctl controls your cd/dvdrom drive under Linux
endef

define Package/cdctl
	$(call Package/cdctl/Default)
	TITLE:=Cdctl controls your cd/dvdrom drive under Linux
#	DEPENDS:=+libopenssl +libpthread +libnl
#	DEPENDS:=+libintl 
#	DEPENDS:=$(INTL_DEPENDS)
endef

define Package/cdctl/description
	$(call Package/cdctl/Default/description)
endef

define Package/cdctl/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/cdctl $(1)/usr/bin/
#	$(INSTALL_BIN) $(PKG_BUILD_DIR)/WTP $(1)/usr/bin/
#	$(INSTALL_BIN) $(PKG_BUILD_DIR)/WUA $(1)/usr/bin/
#	$(INSTALL_DIR) $(1)/etc/capwap
#	$(INSTALL_DATA) $(PKG_BUILD_DIR)/settings.{ac,wtp}.txt $(1)/etc/capwap/
#	$(INSTALL_DATA) $(PKG_BUILD_DIR)/config.{ac,wtp} $(1)/etc/capwap/
endef

$(eval $(call BuildPackage,cdctl))
