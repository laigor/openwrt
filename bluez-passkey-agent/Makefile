#
# Copyright (C) 2010-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bluez-passkey-agent
PKG_VERSION:=1
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/bluez-passkey-agent
  SECTION:=multimedia
  CATEGORY:=Multimedia
  DEPENDS:=+bluez-4
  TITLE:=Bluez passkey agent
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include/dbus-1.0 -I$(STAGING_DIR)/usr/lib/dbus-1.0/include
TARGET_LDFLAGS += -ldbus-1

define Package/bluez-passkey-agent/description
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Configure
endef


define Package/bluez-passkey-agent/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/passkey-agent $(1)/usr/bin/
endef

$(eval $(call BuildPackage,bluez-passkey-agent))
