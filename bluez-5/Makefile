#
# Copyright (C) 2006-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bluez-5
PKG_VERSION:=4
PKG_RELEASE:=3

# PKG_VERSION:=972c92162df5c73dd611a58811c2ed9be1a5576e
# PKG_SOURCE_PROTO:=git
# PKG_SOURCE_VERSION:=$(PKG_VERSION)
# PKG_SOURCE:=$(PKG_NAME)-git-$(PKG_SOURCE_VERSION).tar.bz2
# PKG_SOURCE_URL:=git://git.kernel.org/pub/scm/bluetooth/bluez.git
# PKG_SOURCE_SUBDIR:=$(PKG_NAME)-git-$(PKG_VERSION)

PKG_SOURCE:=$(PKG_NAME).$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://www.kernel.org/pub/linux/bluetooth
# PKG_MD5SUM:=8c2ca546c0e7bb73dbd0e906fce7f6b1
# PKG_FIXUP:=autoreconf
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME).$(PKG_VERSION)
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/bluez-5
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=Official Linux Bluetooth protocol stack
  URL:=http://www.bluez.org/
  DEPENDS:=+glib2 +libical +libreadline +libncurses +libusb-compat +udev +dbus +libsndfile +alsa-lib
endef

CONFIGURE_ARGS += \
		--disable-cups \
		--disable-systemd \
		--enable-library \
		--enable-shared \
		--enable-static \
		--enable-threads \
		--with-udevdir=/lib/udev \
		--enable-datafiles \
		LIBS=-lcurses
#		--disable-udev \

TARGET_CFLAGS += $(FPIC)

#define Build/Compile
#	mkdir -p $(PKG_INSTALL_DIR)/etc
#	$(call Build/Compile/Default,DESTDIR=$(PKG_INSTALL_DIR) all install)
#endef
	
define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/bluetooth
	$(CP) $(PKG_INSTALL_DIR)/usr/include/bluetooth/*.h $(1)/usr/include/bluetooth
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libbluetooth.{a,la,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/bluez.pc $(1)/usr/lib/pkgconfig/
endef

define Package/bluez-5/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libbluetooth.so.* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
#	$(INSTALL_DIR) $(1)/usr/share
#	$(CP) -r $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
	$(INSTALL_DIR) $(1)/usr/lib/bluetooth
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/bluetooth/* $(1)/usr/lib/bluetooth/
	$(INSTALL_DIR) $(1)/lib
	$(INSTALL_DIR) $(1)/lib/udev
	$(CP) -r $(PKG_INSTALL_DIR)/lib/udev/* $(1)/lib/udev/
	$(INSTALL_DIR) $(1)/etc
	$(CP) -r $(PKG_INSTALL_DIR)/etc/* $(1)/etc/
	$(INSTALL_DIR) $(1)/etc/bluetooth
	$(CP) $(PKG_BUILD_DIR)/src/main.conf $(1)/etc/bluetooth/
	$(CP) $(PKG_BUILD_DIR)/profiles/*/*.conf $(1)/etc/bluetooth/
endef

$(eval $(call BuildPackage,bluez-5))
