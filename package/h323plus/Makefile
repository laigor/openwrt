# 
# Copyright (C) 2006-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=h323plus
PKG_VERSION:=1.21.0
PKG_SOURCE:=h323plus-v1_21_0.zip
PKG_SOURCE_URL:=http://www.h323plus.org/source/download
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_BUILD_DEPENDS:=ptlib
PKG_CONFIG_DEPENDS:=ptlib


include $(INCLUDE_DIR)/package.mk

define Package/h323plus
  SECTION:=net
  CATEGORY:=Network
  TITLE:=H.323 Plus
  URL:=http://www.h323plus.org
  DEPENDS:=+ptlib
endef

define Package/h323plus/description
h323plus
endef

TARGET_CFLAGS += $(FPIC)

#CONFIGURE_ARGS += \
#	--prefix=$(1) \
#	--enable-minsize \
#	--enable-opal \
#	--enable-internalregex \
#	--enable-audio \
#	--disable-alsa \
#	--disable-asn \
#	--disable-avc \
#	--enable-configfile \
#	--disable-dc \
#	--disable-dtmf \
#	--enable-expat \
#	--disable-ftp \
#	--disable-http \
#	--disable-httpsvc \
#	--disable-jabber \
#	--disable-odbc \
#	--disable-openldap \
#	--disable-openssl \
#	--disable-oss \
#	--disable-pipechan \
#	--disable-plugins \
#	--disable-pop3smtp \
#	--disable-remconn \
#	--enable-resolver \
#	--enable-qos \
#	--disable-sasl \
#	--disable-sdl \
#	--disable-serial \
#	--disable-shm-video \
#	--disable-snmp \
#	--disable-soap \
#	--disable-socks \
#	--enable-stun \
#	--disable-telnet \
#	--disable-tts \
#	--disable-v4l \
#	--disable-v4l2
#	--disable-bsdvideo \
#	--disable-video \
#	--disable-vxml \
#	--enable-wavfile \
#	--disable-xmlrpc \

CONFIGURE_VARS += PTLIBDIR=$(BUILD_DIR)/ptlib
#	CXXFLAGS="$(TARGET_CFLAGS) -fno-builtin -fno-rtti" \

#CONFIGURE_CMD = ./configure

#define Build/Configure/Default
#        (cd $(PKG_BUILD_DIR)/$(CONFIGURE_PATH)/$(strip $(3)); \
#        if [ -x $(CONFIGURE_CMD) ]; then \
#                $(CP) $(SCRIPT_DIR)/config.{guess,sub} $(PKG_BUILD_DIR)/$(3)/ && \
#                $(CONFIGURE_VARS) \
#                $(2) \
#                $(CONFIGURE_CMD) \
#                $(CONFIGURE_ARGS) \
#                $(1); \
#        fi; \
#        )
#endef


MAKE_FLAGS += optnoshared

define Build/Configure
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	echo Installing Dev
#	$(MAKE) -C $(PKG_BUILD_DIR) DESTDIR=$(1) install
#	$(MAKE) -C $(PKG_BUILD_DIR) DESTDIR="$(PKG_INSTALL_DIR)" install
#	ln -sf $(PKG_NAME)-$(PKG_VERSION) $(BUILD_DIR)/$(PKG_NAME)
#	$(SED) 's|//\(#include <ptlib/sound.h>\)|\1|' $(PKG_BUILD_DIR)/include/ptlib.h
endef
define Package/h323plus/install
	echo Installing
endef

$(eval $(call BuildPackage,h323plus))
