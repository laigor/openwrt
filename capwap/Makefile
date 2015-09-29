# 
# Copyright (C) 2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile $

# OpenWrt package for Open Source CAPWAP
# Prepared by Michael Smith, McGill University

include $(TOPDIR)/rules.mk

PKG_NAME:=capwap

PKG_RELEASE:=2
PKG_VERSION=1.0
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://sourceforge.net/projects/capwap/files/
TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include/libnl3
# http://sourceforge.net/projects/capwap/files/capwap-1.0.tar.gz

# PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
# -fgnu89-inline

include $(INCLUDE_DIR)/package.mk

define Package/capwap/Default
	SECTION:=net
	CATEGORY:=Network
endef

define Package/capwap/Default/description
	The project is an implementation of CAPWAP agents for WTPs and ACs.
endef

define Package/capwap
	$(call Package/capwap/Default)
	TITLE:=open source capwap
	DEPENDS:=+libopenssl +libpthread +libnl
endef

define Package/capwap/description
	$(call Package/capwap/Default/description)
endef

define Package/capwap/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/AC $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/WTP $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/WUA $(1)/usr/bin/
endef

$(eval $(call BuildPackage,capwap))
