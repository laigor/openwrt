#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=asterisk18-chan-dongle
PKG_REV:=27
PKG_VERSION:=1.1.r$(PKG_REV)
PKG_RELEASE:=27

#PKG_SOURCE_URL:=https://www.makhutov.org/svn/chan_datacard/trunk
PKG_SOURCE_URL:=http://asterisk-chan-dongle.googlecode.com/svn/trunk/
PKG_SOURCE_VERSION:=$(PKG_RELEASE)
PKG_SOURCE:=chan_dongle-$(PKG_VERSION).tar.gz
PKG_SOURCE_PROTO:=svn
PKG_FIXUP:=autoreconf
# or
#PKG_SOURCE:=chan_dongle-$(PKG_VERSION).tgz
#PKG_SOURCE_URL=http://asterisk-chan-dongle.googlecode.com/files/
#PKG_MD5SUM:=4ced3ab7094b62be2a0e843a2d4b4111

PKG_SOURCE_SUBDIR:=chan_dongle-$(PKG_VERSION)
PKG_BUILD_DIR=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)

#WITH_ASTERISK=asterisk-1.8.3.2

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/asterisk18-chan-dongle
	SUBMENU:=Telephony
	SECTION:=net
	CATEGORY:=Network
	URL:=http://www.asterisk.org/
	MAINTAINER:=Hans Zandbelt <hans.zandbelt@gmail.com>
	DEPENDS:= +asterisk18 +libiconv-full
	TITLE:=Huawei UMTS 3G dongle support
endef

define Package/asterisk18-chan-dongle/description
	Asterisk channel driver for Huawei UMTS 3G dongle
endef

#TARGET_CFLAGS+= -I. -I$(STAGING_DIR)/usr/lib/libiconv-full/include -DLOW_MEMORY -D_XOPEN_SOURCE=600  $(FPIC)
#TARGET_LDFLAGS+= -L$(STAGING_DIR)/usr/lib/libiconv-full/lib -liconv


MAKE_ARGS:= \
	CC="$(TARGET_CC)" \
	LD="$(TARGET_CC)" \
	CFLAGS="$(TARGET_CFLAGS) -DLOW_MEMORY $(TARGET_CPPFLAGS) -I$(STAGING_DIR)/usr/lib/libiconv-full/include -DHAVE_CONFIG_H -I. -D_XOPEN_SOURCE=600 $(FPIC)" \
	LDFLAGS="$(TARGET_LDFLAGS) -L$(STAGING_DIR)/usr/lib/libiconv-full/lib -liconv"

#-DHAVE_CONFIG_H
#CONFIGURE_VARS += \
#        ac_cv_type_size_t=yes \
#        ac_cv_type_ssize_t=yes

CONFIGURE_ARGS += --with-asterisk=$(STAGING_DIR)/usr/include $(MAKE_ARGS)


define Build/Compile
#	$(call Build/Compile/Default,$(MAKE_ARGS))
#	$(MAKE) -C "$(PKG_BUILD_DIR)" $(MAKE_ARGS)
	(cd $(PKG_BUILD_DIR); mv single.c single.c.off; $(TARGET_CC) -shared $(TARGET_CFLAGS) -DLOW_MEMORY $(TARGET_CPPFLAGS) -I$(STAGING_DIR)/usr/lib/libiconv-full/include -DHAVE_CONFIG_H -I. -D_XOPEN_SOURCE=600 $(FPIC) $(TARGET_LDFLAGS) -L$(STAGING_DIR)/usr/lib/libiconv-full/lib -liconv -o chan_dongle.so *.c)
endef

define Package/asterisk18-chan-dongle/conffiles
/etc/asterisk/dongle.conf
endef

define Package/asterisk18-chan-dongle/install
	$(INSTALL_DIR) $(1)/etc/asterisk
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/etc/dongle.conf $(1)/etc/asterisk/
	$(INSTALL_DIR) $(1)/usr/lib/asterisk/modules
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/chan_dongle.so $(1)/usr/lib/asterisk/modules/
endef

$(eval $(call BuildPackage,asterisk18-chan-dongle))
