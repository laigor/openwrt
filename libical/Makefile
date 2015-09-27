#
# Copyright (C) 2006-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libical
PKG_VERSION:=0.48
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
# PKG_SOURCE_URL:=@SF/libusb
# PKG_SOURCE_URL:=http://downloads.sourceforge.net/project/libical/libical/libical-0.3
PKG_SOURCE_URL:=http://downloads.sourceforge.net/project/freeassociation/libical/libical-0.48
# PKG_MD5SUM:=caf182cbc7565dac0fd72155919672e6
# PKG_FIXUP:=autoreconf
# http://downloads.sourceforge.net/project/libical/libical/libical-0.3/libical-0.3.tar.gz
# http://downloads.sourceforge.net/project/freeassociation/libical/libical-0.48/libical-0.48.tar.gz
# include $(INCLUDE_DIR)/uclibc++.mk

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

define Package/libical
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libical is an Open Source (MPL/LGPL) implementation of the IETF's iCalendar Calendaring and Scheduling protocols. (RFC 2445, 2446, and 2447).
  URL:=http://www.sourceforge.net/projects/freeassociation/
  DEPENDS:=+libpthread
endef


#define Build/Configure
#	$(call Build/Configure/Default, \
#		--enable-shared \
#		--enable-static \
#	)
#endef

#TARGET_CFLAGS += $(FPIC)

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/include/libical
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libical/*.h $(1)/usr/include/libical/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/*.pc $(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.{la,so*,a} $(1)/usr/lib/

endef

define Package/libical/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libical*.so* $(1)/usr/lib/
endef


$(eval $(call BuildPackage,libical))
