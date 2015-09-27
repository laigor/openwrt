#
# Copyright (C) 2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libusb-1.0
PKG_VERSION:=1.0.8
PKG_RELEASE:=1
PKG_REV:=295c9d12e25bc2dbdd8b42bd67a1f7120f0631a1
PKG_SOURCE:=$(PKG_NAME)-git-$(PKG_REV).tar.bz2
# PKG_SOURCE_URL:=http://downloads.sourceforge.net/project/libusb/libusb-1.0/libusb-$(PKG_VERSION)
PKG_SOURCE_URL:=git://git.libusb.org/libusb.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)
# PKG_MD5SUM:=37d34e6eaa69a4b645a19ff4ca63ceef
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_REV)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_REV)

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

define Build/Prepare
	$(call Build/Prepare/Default)
	(cd $(PKG_BUILD_DIR); ./autogen.sh)
endef

define Build/InstallDev
	$(MAKE) install
	$(INSTALL_DIR) $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/include/libusb-1.0
	$(CP) $(PKG_BUILD_DIR)/libusb/libusb.h $(1)/usr/include/libusb-1.0/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libusb/.libs/libusb*.{a,so*} $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/libusb/libusb*.la $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_BUILD_DIR)/libusb*.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libusb-1.0/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libusb/.libs/libusb*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libusb-1.0))
