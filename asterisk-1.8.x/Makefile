#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=asterisk18
PKG_VERSION:=1.8.11.0
PKG_RELEASE:=1
PKG_BUILD_PARALLEL:=1
PKG_SOURCE:=asterisk-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://downloads.asterisk.org/pub/telephony/asterisk/releases/
#PKG_MD5SUM:=bc2a1168603815c23f204927d1e73239

PKG_BUILD_DIR=$(BUILD_DIR)/asterisk-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/asterisk18/Default
  SUBMENU:=Telephony
  SECTION:=net
  CATEGORY:=Network
  URL:=http://www.asterisk.org/
  MAINTAINER:=Hans Zandbelt <hans.zandbelt@gmail.com>
endef

define Package/asterisk18/Default/description
 Asterisk is a complete PBX in software. It provides all of the features
 you would expect from a PBX and more. Asterisk does voice over IP in three
 protocols, and can interoperate with almost all standards-based telephony
 equipment using relatively inexpensive hardware.
endef


define Package/asterisk18
$(call Package/asterisk18/Default)
  TITLE:=Complete open source PBX, v1.8x
  MENU:=1
  DEPENDS:= +libopenssl +libpopt +libpthread +libncurses +zlib @!TARGET_avr32
#  DEPENDS:= +libpopt +libpthread +zlib @!TARGET_avr32
endef

define Package/asterisk18/description
$(call Package/asterisk18/Default/description)
endef


CONFIGURE_ARGS+= \
	--with-sounds-cache="$(DL_DIR)" \
	--disable-xmldoc \
	--localstatedir="/usr" \
	--without-sdl \
	--without-curses
#	--with-gsm=internal \
#	--without-gtk \
#	--without-gtk2 \
#	--without-isdnnet \
#	--without-kde \
#	--without-misdn \
#	--without-nbs \
#	--with-ncurses="$(STAGING_DIR)/usr" \
#	--without-netsnmp \
#	--without-newt \
#	--without-odbc \
#	--without-ogg \
#	--without-osptk \
#	--with-popt="$(STAGING_DIR)/usr" \
#	--without-pri \
#	--without-qt \
#	--without-radius \
#	--without-sdl \
#	--without-spandsp \
#	--without-suppserv \
#	--without-tds \
#	--without-termcap \
#	--without-tinfo \
#	--without-vorbis \
#	--without-vpb \
#	--with-z="$(STAGING_DIR)/usr" \

# CONFIGURE_ARGS+= LIBS="-Wl,-rpath-link=$(STAGING_DIR)/usr/lib"


#MAKE_ARGS+= \
#	ASTVARRUNDIR="/var/run/asterisk" \
#	ASTSPOOLDIR="/var/spool/asterisk" \
#	ASTLOGDIR="/var/log/asterisk"

EXTRA_CFLAGS+= $(TARGET_CPPFLAGS)
EXTRA_LDFLAGS+= $(TARGET_LDFLAGS)

define Build/Configure
	$(call Build/Configure/Default)
endef


define Build/Compile
	$(call Build/Compile/Default, CC=gcc menuselect)
	$(call Build/Compile/Default,ASTVARRUNDIR="/var/run/asterisk" ASTSPOOLDIR="/var/spool/asterisk" ASTLOGDIR="/var/log/asterisk" DESTDIR="$(PKG_INSTALL_DIR)" DEBUG="" OPTIMIZE="" all install samples)
endef


#define Build/Compile
#	$(MAKE) -C "$(PKG_BUILD_DIR)" \
#		include/asterisk/version.h \
#		include/asterisk/buildopts.h defaults.h \
#		makeopts.embed_rules
#	ASTCFLAGS="$(EXTRA_CFLAGS) -DLOW_MEMORY" \
#	ASTLDFLAGS="$(EXTRA_LDFLAGS)" \
#	$(MAKE) -C "$(PKG_BUILD_DIR)" \
#		ASTVARRUNDIR="/var/run/asterisk" \
#		ASTSPOOLDIR="/var/spool/asterisk" \
#		ASTLOGDIR="/var/log/asterisk" \
#		NOISY_BUILD="1" \
#		DEBUG="" \
#		OPTIMIZE="" \
#		DESTDIR="$(PKG_INSTALL_DIR)" \
#		all install samples
#endef


define Package/asterisk18/conffiles
/etc/asterisk/
endef

define Package/asterisk18/install
	$(INSTALL_DIR) $(1)/etc/asterisk
	$(CP) ./files/etc/* $(1)/etc/asterisk/
	$(INSTALL_DIR) $(1)/usr/share
	$(INSTALL_DIR) $(1)/usr/share/asterisk
	$(INSTALL_DIR) $(1)/usr/share/asterisk/sampleconfigs
	$(CP) $(PKG_INSTALL_DIR)/etc/asterisk/* $(1)/usr/share/asterisk/sampleconfigs/
	mv $(1)/usr/share/asterisk/sampleconfigs/asterisk.conf $(1)/etc/asterisk/
	mv $(1)/usr/share/asterisk/sampleconfigs/features.conf $(1)/etc/asterisk/
	mv $(1)/usr/share/asterisk/sampleconfigs/musiconhold.conf $(1)/etc/asterisk/
	mv $(1)/usr/share/asterisk/sampleconfigs/sip.conf $(1)/etc/asterisk/
	mv $(1)/usr/share/asterisk/sampleconfigs/rtp.conf $(1)/etc/asterisk/
	mv $(1)/usr/share/asterisk/sampleconfigs/udptl.conf $(1)/etc/asterisk/
	mv $(1)/usr/share/asterisk/sampleconfigs/modules.conf $(1)/etc/asterisk/
	mv $(1)/usr/share/asterisk/sampleconfigs/logger.conf $(1)/etc/asterisk/
#	for f in asterisk extensions features \
#		indications logger manager modules \
#		sip sip_notify rtp; do \
#		$(CP) $(PKG_INSTALL_DIR)/etc/asterisk/$$$$f.conf $(1)/etc/asterisk/ ; \
#	done
	$(INSTALL_DIR) $(1)/usr/lib/asterisk
#	$(INSTALL_DIR) $(1)/usr/lib/asterisk/modules
#	for f in app_dial app_echo app_playback app_macro \
#		chan_sip res_rtp_asterisk res_rtp_multicast \
#		codec_ulaw codec_gsm \
#		format_gsm format_pcm format_wav format_wav_gsm \
#		pbx_config \
#		func_strings func_timeout func_callerid func_logic; do \
#		$(CP) $(PKG_INSTALL_DIR)/usr/lib/asterisk/modules/$$$$f.so $(1)/usr/lib/asterisk/modules/ ; \
#	done
	rm -rf $(PKG_INSTALL_DIR)/usr/lib/asterisk/documentation
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/asterisk/* $(1)/usr/lib/asterisk/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/asterisk $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc/default
	$(INSTALL_DATA)  ./files/asterisk.default $(1)/etc/default/asterisk
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN)  ./files/asterisk.init $(1)/etc/init.d/asterisk
endef


define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef


$(eval $(call BuildPackage,asterisk18))
