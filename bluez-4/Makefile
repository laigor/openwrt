#
# Copyright (C) 2006-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bluez-4
PKG_VERSION:=101
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME).$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://www.kernel.org/pub/linux/bluetooth
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME).$(PKG_VERSION)
# PKG_MD5SUM:=8c2ca546c0e7bb73dbd0e906fce7f6b1
# PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/bluez-4
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=Official Linux Bluetooth protocol stack
  URL:=http://www.bluez.org/
  DEPENDS:=+glib2 +libreadline +libncurses +libusb +udev +dbus +libsndfile +alsa-lib
endef

CONFIGURE_ARGS += \
		--disable-cups \
		--enable-shared \
		--enable-static \
		--enable-tools \
		--enable-hid2hci \
		--enable-gatt \
		--enable-datafiles \
		--enable-pand \
		--enable-test \
		--enable-bccmd \
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

define Package/bluez-4/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libbluetooth.so.* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/* $(1)/usr/sbin/
	$(CP) -r $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
	$(INSTALL_DIR) $(1)/usr/lib/bluetooth
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/bluetooth/* $(1)/usr/lib/bluetooth/
	$(INSTALL_DIR) $(1)/usr/lib/alsa-lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/alsa-lib/*.so $(1)/usr/lib/alsa-lib/
	$(INSTALL_DIR) $(1)/lib
	$(INSTALL_DIR) $(1)/lib/udev
	$(CP) -r $(PKG_INSTALL_DIR)/lib/udev/* $(1)/lib/udev/
	$(INSTALL_DIR) $(1)/etc
	$(CP) -r $(PKG_INSTALL_DIR)/etc/* $(1)/etc/
	$(INSTALL_DIR) $(1)/etc/bluetooth
	$(CP) $(PKG_BUILD_DIR)/{network,input,serial,tools}/*.conf $(1)/etc/bluetooth/
	$(CP) $(PKG_BUILD_DIR)/audio/audio.conf $(1)/etc/bluetooth/
endef

$(eval $(call BuildPackage,bluez-4))
