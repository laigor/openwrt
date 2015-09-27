# 
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 12225 2008-08-06 22:10:29Z nbd $

include $(TOPDIR)/rules.mk

PKG_NAME:=libusb-1.0
PKG_VERSION:=1.0.6
PKG_RELEASE:=6
PKG_SOURCE:=libusb-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://downloads.sourceforge.net/project/libusb/$(PKG_NAME)/libusb-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/libusb-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/libusb-1.0
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libusb-1.0
  URL:=http://libusb.wiki.sourceforge.net/
endef

define Package/libusb-1.0/description
libusb-1.0
endef

TARGET_CFLAGS += $(FPIC)
CONFIGURE_ARGS += --enable-examples-build

define Build/Configure
      $(call Build/Configure/Default)
endef

define Build/InstallDev
	mkdir -p $(1)/usr/include
	mkdir -p $(1)/usr/include/libusb-1.0
	$(CP) $(PKG_BUILD_DIR)/libusb/libusb.h $(1)/usr/include/libusb-1.0/
	mkdir -p $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libusb/.libs/libusb*.{a,so*} $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/libusb/libusb*.la $(1)/usr/lib/
	mkdir -p $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_BUILD_DIR)/libusb*.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libusb-1.0/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/examples/.libs/lsusb $(1)/usr/bin/lsusb_example
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/libusb/.libs/libusb*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libusb-1.0))
